Configuration reference
=======================

The full default configuration is:

```yaml
translation:
    configs:

        # Prototype
        name:

            # Directories we should scan for translations
            dirs:                 []
            excluded_dirs:        []
            excluded_names:       []
            external_translations_dirs: []
            output_format:        xlf # One of "php"; "yml"; "xlf"; "po"
            blacklist_domains:    []
            whitelist_domains:    []

            # Service ids with to classes that supports remote storage of translations.
            remote_storage:       []

            # Service ids with to classes that supports local storage of translations.
            local_storage:

                # Default:
                - php_translation.local_file_storage.abstract
            output_dir:           '%kernel.root_dir%/Resources/translations'

            # The root dir of your project. By default this will be kernel_root's parent.
            project_root:         ~

            # The version of XLIFF XML you want to use (if dumping to this format).
            xliff_version:        '2.0'

            # Options passed to the local file storage's dumper.
            local_file_storage_options: []
    fallback_translation:
        enabled:              false
        service:              google # One of "google"; "yandex"
        api_key:              null
    edit_in_place:
        enabled:              false
        config_name:          default
        activator:            php_translation.edit_in_place.activator
        show_untranslatable:  true
    webui:
        enabled:              false
        allow_create:         true
        allow_delete:         true

        # Base path for SourceLocation's. Defaults to "%kernel.project_dir%".
        file_base_path:       null
    locales:              []

    # Your default language or fallback locale. Default will be kernel.default_locale
    default_locale:       ~

    # Extend the debug profiler with information about requests.
    symfony_profiler:

        # Turn the symfony profiler integration on or off. Defaults to kernel debug mode.
        enabled:              true
        formatter:            null

        # Limit long HTTP message bodies to x characters. If set to 0 we do not read the message body. Only available with the default formatter (FullHttpMessageFormatter).
        captured_body_length: 0
        allow_edit:           true
    auto_add_missing_translations:
        enabled:              false
        config_name:          default
    http_client:          httplug.client
    message_factory:      httplug.message_factory
```

You can also dump the default configuration using Symfony command:

```bash
bin/console config:dump-reference translation
```
