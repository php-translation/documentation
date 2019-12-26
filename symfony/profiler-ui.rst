Symfony Profiler UI
===================

The Symfony profiler page for translation is great. You see all translations that
were used in that request. But what if you could edit those translations as well?
This is exactly what this feature does. It is way easier to edit and add new translations
since the *missing translations* are highlighted.


Configuration
-------------

.. code-block:: yaml

    # config/config.yaml
    translation:
      # ..
      symfony_profiler:
        enabled: true

.. code-block:: yaml

    # config/routing_dev.yaml
    _translation_profiler:
        resource: '@TranslationBundle/Resources/config/routing_symfony_profiler.yaml'

See the updated Translation page in the Symfony profiler. There are some new buttons
on the right hand side.
