# Symfony Translation Bundle

## Installation

```bash
composer require php-translation/symfony-bundle
```

```php
new Translation\Bundle\TranslationBundle(),
```

## WebUI

```yaml
// config.yml
translation:
  locales: ["sv", "en"]
  webui:
    enabled: true
```

```yaml
// routing_dev.yml
_translation:
    resource: "@TranslationBundle/Resources/config/routing_webui.yml"
    prefix:  /admin/_trans
```