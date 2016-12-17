Common
======

The Common component is the least exiting component. It contains common interfaces
and classes that are used by many other packages in this organization. The most
important ones are listed on this page.

Message
-------

The ``Message`` class is a representation of a translation in a specific language. This
class is commonly used as a parameter or a return value for functions in the organisation.

The message contains of an ``key``, ``domain``, ``locale`` and ``translation``.
There is also an array where meta data can be stored. Example of usage of meta data
could be when a third party translation service has flagged the translation as "fuzzy".

Storage
-------

The ``Storage`` interface is an abstraction for places where you can store translations.
There are many examples like on file system, in database or in any third party translation
service. A ``Storage`` is very simple. It has methods for getting, updating and
deleting a translation.

Exception
---------

The ``Exception`` interface will decorate all the runtime exceptions in the organisation.
