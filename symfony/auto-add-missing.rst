Automatically Add Missing Translations
======================================

When you are visiting a page the Symfony ``TranslationDataCollector`` will
record what translations are being used. The translations marked as "Missing" will
be added to the storage.

Configuration
-------------

.. code-block:: yaml

    # config/config.yml
    translation:
      # ..
      auto_add_missing_translations:
        config_name: 'default'
      # ..

Usage
-----

That's it. You do not have to do anything more. Translations will automatically
pop up in your storage.
