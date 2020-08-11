Extracting Translations from Source
===================================

Extracting translations from your project
-----------------------------------------

.. code-block:: yaml

    translation:
      locales: ["en", "fr", "sv"]
      configs:
        app:
          dirs: ["%kernel.root_dir%/Resources/views", "%kernel.root_dir%/../src"]
          output_dir: "%kernel.root_dir%/Resources/translations"
          excluded_names: ["*TestCase.php", "*Test.php"]
          excluded_dirs: [cache, data, logs]

With the configuration above you may extract all translation keys from your
source code by running

.. code-block:: bash

    php bin/console translation:extract app

Extracting translations from a bundle
-------------------------------------

If you're using a bundle shipped with custom translations, you can extract
them using ``external_translations_dir``.

For example, with `FOSUserBundle<https://github.com/FriendsOfSymfony/FOSUserBundle/>`:

.. code-block:: yaml

    translation:
      configs:
        app:
          external_translations_dir: ["%kernel.root_dir%/vendor/friendsofsymfony/user-bundle/Resources/translations"]


Creating custom extractor
-------------------------

Example of method whose argument we want to translate 

.. code-block:: php

    $this->logger->addMessage("text");

Example of extractor class that we use to create translations

.. code-block::	php

    <?php

    namespace App\Extractor;

    use PhpParser\Node;
    use PhpParser\NodeVisitor;
    use Translation\Extractor\Visitor\Php\BasePHPVisitor;
    
    final class MyCustomExtractor extends BasePHPVisitor implements NodeVisitor 
    {
        /**
         * {@inheritdoc}
         */
        public function beforeTraverse(array $nodes): ?Node
        {
            return null;
        }

        /**
         * {@inheritdoc}
         */
        public function enterNode(Node $node): ?Node
        {
            if (!$node instanceof Node\Expr\MethodCall) {
                return null;
            }

            if (!is_string($node->name) && !$node->name instanceof Node\Identifier) {
                return null;
            }
            
            $name = (string) $node->name;

            //This "if" check that we have method which interests us
            if ($name !== "addMessage") {
                return null;
            }

            $caller = $node->var;
            $callerName = isset($caller->name) ? (string) $caller->name : '';
           
            //This "if" check that we have xxx->logger->addMessage() 
            if ($callerName === 'logger' && $caller instanceof Node\Expr\MethodCall) {
                
                //This "if" chack that we have first argument in method as plain text ( not as variable ) 
                //xxx->logger->addMessage("custom-text") is acceptable
                if (null !== $label = $this->getStringArgument($node, 0)) {
                    $this->addLocation($label, $node->getAttribute('startLine'), $node);
                }
            }
            
            return null;
        }
 
        
        /**
         * {@inheritdoc}
         */
        public function leaveNode(Node $node): ?Node
        {
            return null;
        }

        /**
         * {@inheritdoc}
         */
        public function afterTraverse(array $nodes): ?Node
        {
            return null;
        }        
    }



Necessary configuration for proper operation

.. code-block:: yaml
    
    # -- config/service.yml -- 
 
    # ....

    App\Extractor\MyCustomExtractor:
        tags:
            - { name: php_translation.visitor, type: php }

    # ....
    
