Automatically Add Missing Translations
======================================

When you are visiting a page the Symfony ``TranslationDataCollector`` will
record what translations are being used. The translations marked as "Missing" will
be added to the storage.

Configuration
-------------

.. code-block:: yaml

    # config/config.yaml
    translation:
      # ..
      auto_add_missing_translations:
        enabled: true
        config_name: 'default'
      # ..

Usage
-----

That's it. You do not have to do anything more. Translations will automatically
pop up in your storage.

Production environment
----------------------

Note: The ``TranslationDataCollector`` is not used in production environment (this file is linked with the profiler).
For use in production, you need to decorate the translator :

.. code-block:: yaml

    translator.data_collector:
        class: Symfony\Component\Translation\DataCollectorTranslator
        decorates: translator
        arguments: ['@translator.data_collector.inner']
