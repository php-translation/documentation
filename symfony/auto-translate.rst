Automatically Translate
=======================

When your application is in production and you request for a translation that happens
to be missing, the default action is to check if the translation exists in the
*fallback locale*. If we are "lucky" we show a string in the fallback language.

This could be done better. With the *auto translate* feature we can try to translate
the string in the fallback language to the requested language using a translation
service like Google Translate.

Installation
------------

To use this feature you need to install *php-translation/translator*.

.. code-block:: bash

    composer require php-translation/translator

.. note::

    If you are having issues installing. See :doc:`../guides/configure-httplug`.

Configuration
-------------

.. code-block:: yaml

    # config/config.yml
    translation:
      # ..
      fallback_translation:
        enabled: true
        service: 'google' # One of "google", "yandex", or "bing"
        api_key: 'foobar'
      # ..

Usage
-----

That's it. You do not have to do anything more. It is however a good idea to add
some aggressive caching on the responses from the translation service in order to
remove the need of paying for the same translation twice. See how you :doc:`../guides/configure-httplug`.
