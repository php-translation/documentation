Adding extractors
=================

The extractor library is very SOLID which means that you easily can add extractors
without changing existing code. There are some concepts to be aware of:

The `Extrator` object has a collection of **FileExtractor** that are executed
on files with a file type they support. The `PHPFileExtractor` and `TwigFileExtractor`
are using the [visitor pattern](https://en.wikipedia.org/wiki/Visitor_pattern).
They have a collection of `Translation\Extractor\Visitor` that will be executed
for each file the FileExtractor is running for. To add a custom extractor for a
custom PHP class you may only add a visitor for the `PHPFileExtractor`.

Example
-------

This is an example of how you would extract the "foobar" from the following PHP script:

.. code-block:: php

    $this->translateMe('google', 'foobar');


First you need to create your visitor. Since it is a PHP file we do not need to add
another FileExtractor.

.. code-block:: php

    use PhpParser\Node;
    use PhpParser\NodeVisitor;
    use Translation\Extractor\Model\SourceLocation;
    use Translation\Extractor\Visitor\Php\BasePHPVisitor;

    class TranslateMeVisitor extends BasePHPVisitor implements NodeVisitor
    {
        public function enterNode(Node $node)
        {
            if ($node instanceof Node\Expr\MethodCall) {
                if (!is_string($node->name)) {
                    return;
                }
                $name = $node->name;

                if ('translateMe' === $name) {
                    $label = $this->getStringArgument($node, 1);

                    $source = new SourceLocation(
                        $label,
                        $this->getAbsoluteFilePath(),
                        $node->getAttribute('startLine'),
                        ['domain' => 'messages']
                    );
                    $this->collection->addLocation($source);
                }
            }
        }

        // ...
    }

.. note::

    Refer to the documentation of [nikic/PHP-Parser](https://github.com/nikic/PHP-Parser)
    for more examples of note types.

Tests
`````

This will work, but we need tests. Each extractor must be properly tested. We use
functional tests for each visitor. Add test resources with scripts that you will
use to test your visitor. Reusing test resources should be avoided.

By using the `BasePHPVisitorTest` class you can easily write test will little or
no overhead.

.. code-block:: php

    class TranslateMeVisitorTest extends BasePHPVisitorTest
    {
        public function testExtract()
        {
            $collection = $this->getSourceLocations(new TranslateMeVisitor(), Resources\Php\Symfony\TranslateMeVisitor::class);

            $this->assertCount(1, $collection);
            $source = $collection->first();
            $this->assertEquals('foobar', $source->getMessage());
        }
    }
