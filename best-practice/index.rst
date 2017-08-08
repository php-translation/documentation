Best practices
==============

A goal of this organization is to show best practises and case studies how to do
translations in PHP. The information here should not be considered an absolute truth
but rather show examples of how other is doing translations and to be a place of
shared knowledge.

Articles
--------

- :doc:`few-languages`
- :doc:`using-service`

Translation keys
----------------

The Symfony best practice document states that:

    "Keys should always describe their purpose and not their location. For example,
    if a form has a field with the label 'Username', then a nice key would be ``label.username``,
    not ``edit_form.label.username``."

That is a good start that we like to build on to. All reusable translations keys
should describe their purpose. But non-reusable translation keys **should** describe
their location. Example ``pricing_page.partner.paragraph0`` or ``flash.user_signup.email_in_use``.

The translation keys are also used to give translators *some* context about where
they are used. The following table is a good rule of thumb.

.. csv-table::
   :header: "Message key", "Description"

   "**label.** foo", "For form form labels."
   "**flash.** foo", "For flash messages."
   "**error.** foo", "For error messages."
   "**help.** foo", "For help text used with forms."
   "foo **.heading**", "For a heading."
   "foo **.paragraph0**", "For the first paragraph after a heading."
   "foo **.paragraph1**", "For the second paragraph after a heading."
   "foo.paragraph2 **.html**", "A third paragraph where HTML is allowed inside the translation."
   "_foo", "Starting with underscore means the the translated string should start with a lowercase character."
   "**foo**", "For any common strings like “Show all”, “Next”, “Yes” etc."
   "**vendor.bundle.controller.action.** foo", "For any non-reusable translation."




One should also use different domains to give translators more context. Example of
good domains are **mail**, **messages**, **navigation**, **validators** and **admin**.
