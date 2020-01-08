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
