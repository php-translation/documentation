Application Delivery
====================

If you decide to remove translations from your project repository,
when you deliver your application, you have to run the
``translation:download`` command.
To do so, you just have to add one line in your ``composer.json`` file.

Requirement
-------------

For Symfony 2.x or 3.x, the ``sensio/distribution-bundle`` is needed.
If you don't already have it, install it with Composer

.. code-block:: bash

    composer require sensio/distribution-bundle


Configuration
-------------

Update the section ``"scripts"`` of you ``composer.json`` file. 

Example for Symfony 2.x or 3.x :

.. code-block:: JSON

    {
      "scripts": {
        "symfony-scripts": [
          "Translation\\Bundle\\Composer\\ScriptHandler::translationDownload"
        ],
        "post-install-cmd": [
          "@symfony-scripts"
        ],
        "post-update-cmd": [
          "@symfony-scripts"
        ]
      }
    }

Example for Symfony 4.x :

.. code-block:: JSON

    {
      "scripts": {
        "auto-scripts": {
          "translation:download --cache": "symfony-cmd"
        },
        "post-install-cmd": [
          "@auto-scripts"
        ],
        "post-update-cmd": [
          "@auto-scripts"
        ]
      }
    }

