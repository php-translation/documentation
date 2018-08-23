Application Delivery
====================

If you decide to remove translations from your project repository,
when you deliver your application, you have to run the
``translation:download`` command.
To do so, you just have to add one line in your ``composer.json`` file.

Requirement
-------------

The ``sensio/distribution-bundle`` is needed. If you don't already
have it, install it with Composer

.. code-block:: bash

    composer require sensio/distribution-bundle


Configuration
-------------

You now can use ``"Translation\\Bundle\\Composer\\ScriptHandler::translationDownload"``
in your ``composer.json`` file.

Example :

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
