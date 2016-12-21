Configure HTTPlug
=================

If you are using the Symfony bundle you want to use HTTPlug. It is a great tool
to decouple from the HTTP client. If you are new to HTTPlug you may want to read
their introduction_. The very easiest way of using HTTPlug is to install the HTTPlugBundle_.

The standard configuration (no configuration) works for a common setup but you may
want to add some configuration. If you want to add logging for **all** the requests and
responses for a client named ``acme`` you may do:

.. code-block:: yaml

    httplug:
        plugins:
            logger: ~
        clients:
            acme:
                factory: 'httplug.factory.guzzle6'
                plugins: ['httplug.plugin.logger']
                config:
                    verify: false
                    timeout: 2

    translation:
        http_client: 'httplug.client.acme'

Configure caching
-----------------

When you are using the :doc:`auto translation <../components/translator>` features
you may want to cache the responses from your paid third party translator services.
To configure HTTPlug to be aggressive for those request you need the CachePlugin
and a PSR-6 cache pool.

.. code-block:: yaml

    # Using PHP-cache.com for PSR-6 cache.
    cache_adapter:
        providers:
            my_redis:
                factory: 'cache.factory.redis'

    httplug:
        plugins:
            logger: ~
            cache:
                cache_pool: 'cache.provider.my_redis'
                config:
                    default_ttl: 94608000 # three years
                    respect_cache_headers: false # We cache no matter what the sever says
        clients:
            translator_client:
                factory: 'httplug.factory.guzzle6'
                plugins: ['httplug.plugin.cache', 'httplug.plugin.logger']

    translation:
        # ...
        http_client: 'httplug.client.translator_client'
        fallback_translation:
            service: 'google'
            api_key: 'foobar'

.. note::

    See `PHP-cache.com <http://www.php-cache.com/>`_ for information about caching.

.. _introduction: http://docs.php-http.org/en/latest/httplug/users.html
.. _HTTPlugBundle: https://github.com/php-http/HttplugBundle
