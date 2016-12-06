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

Platform adapters
`````````````````
.. image:: https://poser.pugx.org/php-translation/platform-adapter/v/stable
   :target: https://packagist.org/packages/php-translation/platform-adapter

.. image:: https://poser.pugx.org/php-translation/platform-adapter/downloads
   :target: https://packagist.org/packages/php-translation/platform-adapter
   :alt: Total Downloads

The platform adapters integrate third party platforms like Localize.biz to a common
interface.

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

.. toctree::
    :hidden:

    PHP Translation <self>

.. toctree::
   :hidden:
   :caption: Introduction

   Adding extractors <introduction/adding-extractor>

.. toctree::
   :hidden:
   :caption: Components

   Symfony bundle <components/symfony-bundle>

.. toctree::
   :hidden:
   :caption: Best practice

   Intro <best-practice/index>
   Using service <best-practice/using-service>


.. toctree::
   :hidden:
   :caption: ---------

   development/index.rst
