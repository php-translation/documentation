Symfony WebUI
=============



WebUI
-----

.. code-block:: yaml

    // config.yml
    translation:
      locales: ["sv", "en"]
      webui:
        enabled: true
      configs:
        app:
          dirs: ["%kernel.root_dir%/Resources/views", "%kernel.root_dir%/../src"]
          output_dir: "%kernel.root_dir%/Resources/translations"
          excluded_names: ["*TestCase.php", "*Test.php"]
          excluded_dirs: [cache, data, logs]


.. code-block:: yaml

    // routing_dev.yml
    _translation_webui:
        resource: "@TranslationBundle/Resources/config/routing_webui.yml"
        prefix:  /admin

Go to http://localhost.dev/app_dev.php/admin/_trans
