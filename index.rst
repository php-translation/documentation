PHP Translation
===============

The goal of this organization is to provide a tool set for doing translations in
a PHP project. The secondary goal is to provide guides or case studies how one
could use those tools.

Organization overview
---------------------

Extractor
`````````
.. image:: https://poser.pugx.org/php-translation/extractor/v/stable
   :target: https://packagist.org/packages/php-translation/extractor

.. image:: https://poser.pugx.org/php-translation/extractor/downloads
   :target: https://packagist.org/packages/php-translation/extractor
   :alt: Total Downloads

This package include extractors that look at your source code and extract translation
keys from it. We support extractor from PHP files, Twig files and Blade template
files.

Common
``````
.. image:: https://poser.pugx.org/php-translation/common/v/stable
   :target: https://packagist.org/packages/php-translation/common

.. image:: https://poser.pugx.org/php-translation/common/downloads
   :target: https://packagist.org/packages/php-translation/common
   :alt: Total Downloads

Common interfaces and classes used by 2 or more packages.

Translator
``````````
.. image:: https://poser.pugx.org/php-translation/translator/v/stable
   :target: https://packagist.org/packages/php-translation/translator

.. image:: https://poser.pugx.org/php-translation/translator/downloads
   :target: https://packagist.org/packages/php-translation/translator
   :alt: Total Downloads

The translator package includes third party translation clients. Use this package
if you want to translate a string with Google Translate or Bing Translate.

Symfony Bundle
``````````````
.. image:: https://poser.pugx.org/php-translation/symfony-bundle/v/stable
   :target: https://packagist.org/packages/php-translation/symfony-bundle

.. image:: https://poser.pugx.org/php-translation/symfony-bundle/downloads
   :target: https://packagist.org/packages/php-translation/symfony-bundle
   :alt: Total Downloads

The Symfony bundle integrates all these fancy features with Symfony. We have support
for automatic translation, web UI, third party services and more.


Platform adapters
`````````````````

This organisation has plenty of platform adapters to support third party services.
They all live in the php-translation/platform-adapter repository.


.. toctree::
    :hidden:

    PHP Translation <self>
    Introduction <introduction>

.. toctree::
   :hidden:
   :caption: Guides

   Adding extractors <guides/adding-extractor>
   Configure Platform adapter <guides/using-loco-adapter>
   Configure HTTPlug <guides/configure-httplug>

.. toctree::
   :hidden:
   :caption: Best practice

   Intro <best-practice/index>
   Using service <best-practice/using-service>

.. toctree::
   :hidden:
   :caption: Symfony

   A bundle to rule them all <symfony/index>
   Configuration reference <symfony/configuration-reference>
   Extracting translations <symfony/extracting-translations>
   WebUI <symfony/webui>
   Symfony Profiler UI <symfony/profiler-ui>
   Edit in place <symfony/edit-in-place>
   Auto translate <symfony/auto-translate>

.. toctree::
   :hidden:
   :caption: Components

   Common <components/common>
   Extractor <components/extractor>
   Translator <components/translator>
   Platform adapters <components/platform-adapters>



.. toctree::
   :hidden:
   :caption: ---------

   development/index.rst
