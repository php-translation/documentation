Extractor
=========

The responsibility of the Extractor component is to get translation keys from the
source code.

Installation and Usage
----------------------

Install the extractor component with Composer

.. code-block:: bash

    composer require php-translation/extractor

When the extractor is downloaded you may use it by doing the following:

.. code-block:: php

    require "vendor/autoload.php";

    use Translation\Extractor\Visitor\Php\Symfony as Visitor;

    // Create extractor for PHP files
    $fileExtractor = new PHPFileExtractor()

    // Add visitors
    $fileExtractor->addVisitor(new Visitor\ContainerAwareTrans());
    $fileExtractor->addVisitor(new Visitor\ContainerAwareTransChoice());
    $fileExtractor->addVisitor(new Visitor\FlashMessage());
    $fileExtractor->addVisitor(new Visitor\FormTypeChoices());

    // Add the file extractor to Extractor
    $extractor = new Extractor();
    $extractor->addFileExtractor($this->getPHPFileExtractor());

    //Start extracting files
    $sourceCollection = $extractor->extractFromDirectory('/foo/bar');

    // Print the result
    foreach ($sourceCollection as $source) {
      echo sprintf('Key "%s" found in %s at line %d', $source-getMessage(), $source->getPath(), $source->getLine());
    }

Architecture
------------

There is a lot of things happening the the code example above. Everything is very
SOLID so it is easy to add your own extractors if you have custom features that
you need to translate.

The class that we interact with after when we want to extract translations is the
``Extractor`` class. It supports ``Extractor::extractFromDirectory(string)`` and
the more flexible ``Extractor::extract(Finder)``. The Extractor looks at all files
in the directory and checks the type/extension. The extractor then executes all
``FileExtractor`` for this file type.

There is a few ``FileExtractor`` that comes with this component. They are ``PHPFileExtractor``,
``TwigFileExtractor`` and ``BladeExtractor``. As you may guess they extract translations
from PHP files, Twig files and Blade files respectively. The most interesting ones
are ``PHPFileExtractor`` and ``TwigFileExtractor`` because they are using the `Visitor pattern`_
to parse all the nodes in the document.

Let's focus on the ``PHPFileExtractor`` only for a moment. We are using the Nikic
PHP Parser to split the PHP source into an abstract syntax tree which enables us
to statically analyze the source. Read more about this in the `nikic/php-parser`_
documentation. When you add a visitor to the ``PHPFileExtractor`` it will be called
for each node in the syntax tree.

The visitors is very specific with what they are looking for. The ``FlashMessage``
visitor is searching for a pattern like ``$this->addFlash()``. If that string is
found it will add a new ``SourceLocation`` to the ``SourceCollection`` model.

When all visitors and ``FileExtractor`` has been executed an instance of the ``SourceCollection``
will be returned.

.. note::

    If you want to add functionality to the extractor you are most likely to add
    a new visitor. See :doc:`../guides/adding-extractor` for more information.

Special extractors
------------------

We have common extractors for Symfony, Twig and Blade. They all are doing static
analysis on the source files to find translation strings. But in some situations
you need to specify translation dynamically. You may achieve this by implementing
``TranslationSourceLocationContainer``.

.. code-block:: php

    use Translation\Extractor\Model\SourceLocation;
    use Translation\Extractor\TranslationSourceLocationContainer;
    use Symfony\Component\Form\AbstractType;

    class MyCustomFromType extends AbstractType implements TranslationSourceLocationContainer
    {
        // ...
        public static function getTranslationSourceLocations()
        {
            $options = // Get options
            $data = [];
            foreach ($options as $option) {
                $data[] = SourceLocation::createHere('option.'.$option);
            }

            return $data;
        }
    }


.. _`Visitor pattern`: https://en.wikipedia.org/wiki/Visitor_pattern
.. _`nikic/php-parser`: https://github.com/nikic/PHP-Parser

