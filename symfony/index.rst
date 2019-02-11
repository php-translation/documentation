Symfony Translation Bundle
==========================

The Symfony bundle is filled with cool features that will ease your translation
workflow. You probably do not want **all features** enabled, just choose the ones
you like. Some features requires you to install extra packages, but that is explained
in the documentation for each feature.

Features
--------

- :doc:`extracting-translations`
- :doc:`webui`
- :doc:`profiler-ui`
- :doc:`edit-in-place`
- :doc:`auto-translate`
- :doc:`auto-add-missing`

Installation
------------

Install the bundle with Composer

.. code-block:: bash

    composer require php-translation/symfony-bundle


Then enable the bundle in AppKernel.php

.. code-block:: php

    class AppKernel extends Kernel
    {
      public function registerBundles()
      {
        $bundles = array(
            // ...
            new Translation\Bundle\TranslationBundle(),
        }
      }
    }

Configuration
-------------

The bundle has a very flexible configuration. It allows you do have different setups
for different parts of your application. This might be overkill for most applications
but it is possible by specifying more keys under ``translation.configs``.

Below is an example of configuration that is great to start with.

.. code-block:: yaml

    translation:
      locales: ["en", "fr", "sv"]
      configs:
        app:
          dirs: ["%kernel.root_dir%/Resources/views", "%kernel.root_dir%/../src"]
          output_dir: "%kernel.root_dir%/Resources/translations"
          excluded_names: ["*TestCase.php", "*Test.php"]
          excluded_dirs: [cache, data, logs]

With the configuration above you may extract all translation key from your source
code by running

.. code-block:: bash

    php bin/console translation:extract app

.. note::

    See page :doc:`extracting-translations` for more information.


Storages
--------

By default we store all translations on the file system. This is highly configurable.
Many developers keep a local copy of all translations but do also use a remote storage,
like a translations platform. You may also create your own storage. A storage service
must implement ``Translation\Common\Storage``.

.. code-block:: yaml

    translation:
      locales: ["en", "fr", "sv"]
      configs:
        app:
          dirs: ["%kernel.root_dir%/Resources/views", "%kernel.root_dir%/../src"]
          output_dir: "%kernel.root_dir%/Resources/translations"
          remote_storage: ["php_translation.adapter.loco"]
          local_storage: ["app.custom_local_storage"]
          output_format: "yml"


The PHP Translation organisation provides some adapters to commonly used translation
storages. See our all :doc:`storage adapters <../overview>`
or see an example on how to :doc:`install an adapter <../guides/using-loco-adapter>`.
