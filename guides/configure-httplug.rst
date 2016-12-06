Configure HTTPlug
=================

If you are using the Symfony bundle you want to use HTTPlug. It is a great tool
to decouple from the HTTP client. If you are new to HTTPlug you may want to read
their introduction_. The very easiest way of using HTTPlug is to install the HTTPlugBundle.

When you are using the auto translation features you may want to cache the responses
from your paid third party translator services. To configure HTTPlug to be aggressive
for those request you need the CachePlugin and the UrlMathcher.

TODO Show how to configure the CachePlugin to cache google translate calls.

.. _introduction: http://docs.php-http.org/en/latest/httplug/users.html
