Symfony Profiler UI
===================



Symfony Profiler Integration
----------------------------

.. code-block:: yaml

    // config.yml
    translation:
      locales: ["sv", "en"]
      symfony_profiler:
        enabled: true

.. code-block:: yaml

    // routing_dev.yml
    _translation_profiler:
        resource: '@TranslationBundle/Resources/config/routing_symfony_profiler.yml'
