Organization overview
=====================

There is quite a few repositories in this organisation. Here is a brief overview
what all of them does.

Extractor
---------
.. image:: https://poser.pugx.org/php-translation/extractor/v/stable
   :target: https://github.com/php-translation/extractor

.. image:: https://poser.pugx.org/php-translation/extractor/downloads
   :target: https://packagist.org/packages/php-translation/extractor
   :alt: Total Downloads

This package include extractors that look at your source code and extract translation
keys from it. We support extractor from PHP files, Twig files and Blade template
files. Read more :doc:`about the extractor <components/extractor>`.

Common
------
.. image:: https://poser.pugx.org/php-translation/common/v/stable
   :target: https://github.com/php-translation/common

.. image:: https://poser.pugx.org/php-translation/common/downloads
   :target: https://packagist.org/packages/php-translation/common
   :alt: Total Downloads

Common interfaces and classes used by 2 or more packages. Read more
:doc:`about common <components/common>`.

Symfony Bundle
--------------
.. image:: https://poser.pugx.org/php-translation/symfony-bundle/v/stable
   :target: https://github.com/php-translation/symfony-bundle

.. image:: https://poser.pugx.org/php-translation/symfony-bundle/downloads
   :target: https://packagist.org/packages/php-translation/symfony-bundle
   :alt: Total Downloads

The Symfony bundle integrates all these fancy features with Symfony. We have support
for automatic translation, web UI, third party services and more. Read more
:doc:`about the bundle <symfony/index>`.


Translator
----------
.. image:: https://poser.pugx.org/php-translation/translator/v/stable
   :target: https://github.com/php-translation/translator

.. image:: https://poser.pugx.org/php-translation/translator/downloads
   :target: https://packagist.org/packages/php-translation/translator
   :alt: Total Downloads

The translator package includes third party translation clients. Use this package
if you want to translate a string with Google Translate or Bing Translate.
Read more :doc:`about translators <components/translator>`.

Storage adapters
----------------

This organisation has plenty of storage adapters to support storing your translations
on different third party services. All storages implement ``Translation\Common\Storage``.
The Symfony bundle allows you to use multiple storages.

Symfony storage
```````````````
.. image:: https://poser.pugx.org/php-translation/symfony-storage/v/stable
   :target: https://github.com/php-translation/symfony-storage

.. image:: https://poser.pugx.org/php-translation/symfony-storage/downloads
   :target: https://packagist.org/packages/php-translation/symfony-storage
   :alt: Total Downloads

The Symfony storage stores translations on the local file system using Symfony's
writers and loaders. This storage is required by the Symfony bundle and should be
considered as a "local cache".

The Symfony storage also has a ``XliffConverter`` that converts a ``Catalogue`` to
the contents of a Xliff file. It also supports the reverse action.

Flysystem
`````````
.. image:: https://poser.pugx.org/php-translation/flysystem-adapter/v/stable
   :target: https://github.com/php-translation/flysystem-adapter

.. image:: https://poser.pugx.org/php-translation/flysystem-adapter/downloads
   :target: https://packagist.org/packages/php-translation/flysystem-adapter
   :alt: Total Downloads

Do you use a remote filesystem for your translations? The Flysystem adapter is the
adapter for you. It is a storage based on the excellent Flysystem_ by Frank de Jonge.

Loco
````
.. image:: https://poser.pugx.org/php-translation/loco-adapter/v/stable
   :target: https://github.com/php-translation/loco-adapter

.. image:: https://poser.pugx.org/php-translation/loco-adapter/downloads
   :target: https://packagist.org/packages/php-translation/loco-adapter
   :alt: Total Downloads

Use the power of Loco_ to manage your translations and give your translators access
to a custom user interface. Loco is created by Tim Withlock.

Transifex
`````````
.. image:: https://poser.pugx.org/php-translation/transifex-adapter/v/stable
   :target: https://github.com/php-translation/transifex-adapter

.. image:: https://poser.pugx.org/php-translation/transifex-adapter/downloads
   :target: https://packagist.org/packages/php-translation/transifex-adapter
   :alt: Total Downloads

An adapter for Transifex_.


.. _`Flysystem`: https://flysystem.thephpleague.com/
.. _`Loco`: https://localise.biz/
.. _`Transifex`: https://www.transifex.com/
