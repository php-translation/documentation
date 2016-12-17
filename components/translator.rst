Translator
==========

The Translator component provides an interface for translation services like Google
Translate or Bing Translate.

Installation and Usage
----------------------

Install the extractor component with Composer

.. code-block:: bash

    composer require php-translation/translator

.. code-block:: php

    require "vendor/autoload.php";

    $translator = new Translator();
    $translator->addTranslatorService(new GoogleTranslator('api_key'));

    echo $translator->translate('apple', 'en', 'sv'); // "äpple"

Architecture
------------

The ``Translator`` class could be considered a "chain translator" it asks the first
translation service to translate the string. If the translation fails it asks the
second service until a translation is found. If no translation is found a ``null``
value will be returned.

The ``Translator`` class is SOLID so you can easily add your custom translator into
the chain.

.. note::

    Protip: Since most translator services are paid services you probably want to
    add agressive caching on the responses. See :doc:`../guides/configure-httplug`
    for more information.
