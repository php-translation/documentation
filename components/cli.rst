Command line interface
======================

If you do not want to "pollute" your application with a lot of dependencies you may
install our CLI tool. It is basically the Symfony Translation bundle packed down in
a single PHAR.

The CLI support extracting, syncing and downloading translations. It does also run
the WebUI so you can edit translations in a nice user interface.

Configuration
-------------

Every time you run the CLI it looks for a configuration file named "translation.yml"
that should be located in the same directory that you execute the command. The
configuration will be exact the same as for the TranslationBundle. Example::

.. code-block:: yaml

    // config.yml
    translation:
      locales: ["en", "sv"]
      configs:
        app:
          dirs: ["%kernel.project_dir%/app/Resources/views", "%kernel.project_dir%/src"]
          output_dir: "%kernel.project_dir%/app/Resources/translations"
          excluded_names: ["*TestCase.php", "*Test.php"]
          excluded_dirs: [cache, data, logs]

Other translation bundles installed
-----------------------------------

The CLI tool does also have a few other translation bundles installed. They are installed
by default to give you the possibility to configure different kind of remote storages.

* Loco Adapter
* Transifex Adapter
