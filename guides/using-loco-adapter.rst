How to use Loco Adapter
=======================

When your application has reached a certain number of languages and you can't translate
all of them yourself you need a translation platform to ease your work with external
translators. This article shows how to set up a storage adapter using Loco_. Loco
is just an example here. All storage adapters have a similar way of being configured.

Installation
------------

Assuming you have already installed the :doc:`Symfony bundle <../symfony/index>`,
you need to find and install a storage adapter. See our :doc:`list of storage adapters <../overview>`.

.. code-block:: bash

    composer require php-translation/loco-adapter

The storage adapter does also contain a bundle which needs to be enabled.

.. code-block:: php

    <?php
    // app/AppKernel.php

    public function registerBundles()
    {
        $bundles = array(
            // ...
            new Translation\PlatformAdapter\Loco\Bridge\Symfony\TranslationAdapterLocoBundle(),
        );
    }

Configuration
-------------

Once the adapter bundle is installed you must configure it with your API keys. For
Loco the configuration looks like this:

.. code-block:: yaml

    # /app/config/config.yml
    translation_adapter_loco:
      projects:
        messages:
          api_key: 'foobar'
        navigation:
          api_key: 'bazbar'

When the storage adapter bundle is configured it will register a service with id
`php_translation.adapter.loco`. Now wee need to tell the ``TranslationBundle``
to use this adapter.

.. note::

    The terminology for "adapters" in the context of the Symfony bundle is "storage".

The ``TranslationBundle`` supports multiple storages. You can even use them at the
same time. There are **local storages** and **remote storages**. One should consider
the local storage as a cache. Which means that the absolute truth is always the
remote storage. By default there is a local file storage which would be suitable
for most applications.

Lets configure the bundle to use Loco as a remote storage.

.. code-block:: yaml

    translation:
        locales: ["en", "fr", "sv"]
        configs:
            app:
                dirs: ["%kernel.root_dir%/Resources/views", "%kernel.root_dir%/../src"]
                output_dir: "%kernel.root_dir%/Resources/translations"
                remote_storage: ["php_translation.adapter.loco"]


Usage
-----

You may use the ``TranslationBundle`` as you normally do. When you add new translations
in the :doc:`Symfony Profiler <../symfony/profiler-ui>` they will automatically
be added in Loco. You can also run Symfony commands to upload and download translations
to your remote storages.

.. _Loco: https://localise.biz/
