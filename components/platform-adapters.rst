Platform Adapters
=================

To be able to integrate with all the third party translation platforms we need adapters
for each of them. The adapter converts the ``ThirdPartyPlatformApiClient`` into
a ``Translation\Common\Storage``.

The `platform adapter repository`_ is a "monolithic" repository. It uses `www.subtreesplit.com`_
to push changes from ``php-translation/platform-adapter`` to ``php-translation/foo-adapter``.
This setup will make it easier to maintain the adapters since it requires only one
pull request to make a change on many adapters. Note that ``php-translation/foo-adapter``
is a **read only** repository and changes should go to ``php-translation/platform-adapter``.

The Adapters
------------

Each adapter has a a dependency on a API client. They also have different Composer
requirements and may support different PHP version. All the adapters has a Symfony
bundle for ease the integration with Symfony.

To install an adapter in Symfony you need to download it with Composer, activate
the bundle in ``AppKernel`` and then add some configuration. This procedure is described
at each adapters repository.

.. note::

    See guide :doc:`../guides/using-loco-adapter`

The table below shows the adapters and their platform where you can read more about
the service.


.. csv-table::
   :header: "Platform", "Repository", "Badges"

   "`Loco/Localise.biz <https://localise.biz/>`_", "`php-translation/loco-adapter <https://github.com/php-translation/loco-adapter/>`_", |vLoco| |dLoco|

.. _`platform adapter repository`: https://github.com/php-translation/platform-adapter
.. _`www.subtreesplit.com`: https://www.subtreesplit.com/

.. Badges:

.. |vLoco| image:: https://poser.pugx.org/php-translation/loco-adapter/v/stable
   :target: https://packagist.org/packages/php-translation/loco-adapter
.. |dLoco| image:: https://poser.pugx.org/php-translation/loco-adapter/downloads
   :target: https://packagist.org/packages/php-translation/loco-adapter


