# Custom Nginx

## Installation

## How to use

## Configuration

Add-on configuration:

```yaml
domain: my.domain.com
use_default_http_config: true
use_default_https_config: true
certificate_file: fullchain.pem
private_key_file: privkey.pem
advanced: true
custom_config_path: /config/custom_nginx
```

### Option: `domain` (required)

The domain of your Home Assistant instance.

### Option: `use_default_http_config`

Use the default nginx HTTP configuration which is bundled in the addon.

### Option: `use_default_https_config`

Use the default nginx HTTPS configuration which is bundled in the addon. Make sure to have a certificate and private key file present.

### Option: `certificate_file`

Name of the fullchain certificate file in the /ssl directory.

### Option `private_key_file`

Name of the private key file in the /ssl directory.

### Option `advanced`

Enable this option to override the nginx configuration with your own files.

### Option `custom_config_path`

Path to the folder containing your custom nginx.conf file. You can optionally use the following template variables which will be resolved by the addon:

- %%SERVER_NAME%%
- %%CERTIFICATE_FILE%%
- %%PRIVATE_KEY_FILE%%
- %%HA_PORT%%

The ssh_dhparam and proxy_pass option should be taken as is.

```
# nginx.conf
http {
    ...
    server {
        server_name _ %%SERVER_NAME%%;
        ssl_dhparam /data/dhparams.pem;
        ssl_certificate /ssl/%%CERTIFICATE_FILE%%;
        ssl_certificate_key /ssl/%%PRIVATE_KEY_FILE%%;
        location / {
            proxy_pass http://homeassistant.local.hass.io:%%HA_PORT%%;
            ...
        }
        ...
    }
}
```

## Known issues and limitations

## Support

[issue]: https://github.com/tienducle/ha-addon-custom-nginx/issues
[repository]: https://github.com/tienducle/ha-addon-custom-nginx
