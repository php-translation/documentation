Symfony WebUI
=============

The Symfony WebUI feature bring you a web interface to add, edit and remove translations.

.. image:: /assets/image/webui-dashboard.png
    :width: 300px
    :align: left

.. image:: /assets/image/webui-page.png
    :width: 300px
    :align: left

|clearfloat|

Configuration
-------------

.. code-block:: yaml

    # config/config.yml
    translation:
      # ..
      webui:
        enabled: true
      # ..


.. code-block:: yaml

    # config/routing_dev.yml
    _translation_webui:
        resource: "@TranslationBundle/Resources/config/routing_webui.yml"
        prefix:  /admin

Go to http://localhost.dev/app_dev.php/admin/_trans


.. |clearfloat|  raw:: html

    <div style="clear:left"></div>
