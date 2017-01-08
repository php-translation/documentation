PHP Translation
===============

**How do you manage your multilanguage Symfony application?**

This is something you know many companies do but nobody talks about how they do it.
It might be because nobody is really proud of their solution. That is something we
like to change. We want to share ideas, knowledge and tools with the PHP community.

This organization has some large building blocks that you should be aware of. First
there is the :doc:`Extractor<components/extractor>` that finds translation keys in
any source file. Second we have the :doc:`Symfony Bundle<symfony/index>` which is
using the Extractor and puts a lot of great feature that will help your translation
workflow. There are features like :doc:`automatic translation<symfony/auto-translate>`, a
:doc:`Web UI<symfony/webui>`, :doc:`Edit-in-place<symfony/edit-in-place>`
that allows you to edit translations in the right context and there is also support
for multiple local and remote *storages*.

Getting started
---------------

If you are using Symfony you should start by looking at the documentation for the
:doc:`Symfony bundle<symfony/index>`. If you are more hard core you may want to
start by looking at the :doc:`overview`.


.. toctree::
    :hidden:

    PHP Translation <self>
    Organization overview <overview>

.. toctree::
   :hidden:
   :caption: Guides

   Configure storage adapter <guides/using-loco-adapter>
   Configure HTTPlug <guides/configure-httplug>
   Adding extractors <guides/adding-extractor>

.. toctree::
   :hidden:
   :caption: Best practice

   Introduction <best-practice/index>
   best-practice/few-languages
   Using service <best-practice/using-service>

.. toctree::
   :hidden:
   :caption: Symfony

   Symfony Translation Bundle <symfony/index>
   Configuration reference <symfony/configuration-reference>
   Extracting translations <symfony/extracting-translations>
   WebUI <symfony/webui>
   Symfony Profiler UI <symfony/profiler-ui>
   Edit in place <symfony/edit-in-place>
   Auto translate <symfony/auto-translate>
   Auto add missing translations <symfony/auto-add-missing>

.. toctree::
   :hidden:
   :caption: Components

   Common <components/common>
   Extractor <components/extractor>
   Translator <components/translator>


.. toctree::
   :hidden:
   :caption: ---------

   development/index.rst

