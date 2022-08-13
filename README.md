[![Coverage Status](https://coveralls.io/repos/github/zebox/go-oc-currency-updater/badge.svg?branch=master)](https://coveralls.io/github/zebox/go-oc-currency-updater?branch=master)
![Build Status](https://github.com/zebox/go-oc-currency-updater/actions/workflows/main.yml/badge.svg)
[![Go Report Card](https://goreportcard.com/badge/github.com/zebox/gojwk)](https://goreportcard.com/report/github.com/zebox/go-oc-currency-updater)
### OPENCART CURRENCY UPDATER
After the Yahoo service which used for currency update in OpenCart became unavailable users use different way for fixed it.
But some popular offered ways sometimes brake auto update function. Also auto update function, in default module, triggers when admin logged in to admin panel.
But I need get currency update daily and automatically without login to admin panel. I don't have big skills in PHP and OpenCart framework 
and that i decision to make simple external CLI util for do it (OpencCartCurrencyUpdate - OCCU).

This util wraps calling an internal OpenCart API (`route=localisation/currency/refresh`) which refresh currency when user click a refresh button 
in `'Settings'->'Localisation'->'Currency'` section. Before call previous API util gets `user_token` using `route=common/login` call with admin credentials.

This util required base OpenCart URL and credentials for login to admin panel (required parameter set as CLI flags). 
Then  user can schedule execute this utils by either coron or some different schedulers.

#### Example 
```text
./go-oc-currency-updater -b=https://example.org -u=example_login -p=example_password
```
### All application Options
```text
-b, --base-url:  Base URL for OpenCart site (https://example.org) [%OCCU_BASE_URL%] (required)
-u, --username:  Username for access to OpenCart admin panel [%OCCU_LOGIN%] (required)
-p, --password:  Password for access to OpenCart admin panel [%OCCU_PASSWORD%] (required)

Help Options:
-?              Show this help message
-h, --help      Show this help message

```

### Credits
[Umputun](https://github.com/umputun) - ideas, patterns and examples  

[jessevdk/go-flags](https://github.com/jessevdk/go-flags) - for CLI parameters parser.