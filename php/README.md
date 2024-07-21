# PHP Docker Controller

This is the code for the PHP Docker controller.

## How to run

Running this locally requires Docker Engine on the same machine. 
If this is the case, just execute the following command:

```bash
composer install
composer run dev
```

You can then access the web interface at `localhost:8080`.

## Commands

| Command                                 | Description                            |
|-----------------------------------------|----------------------------------------|
| `composer run dev`                      | Starts the development server          |
| `composer run psalm`                    | Run Psalm static analysis              |
| `composer run psalm:update-baseline`    | Run Psalm with `--update-baseline` arg |
| `composer run lint`                     | Run PHP Syntax check                   |

[//]: # (| `composer run php-deprecation-detector` | Run PHP Deprecation Detector           |)
