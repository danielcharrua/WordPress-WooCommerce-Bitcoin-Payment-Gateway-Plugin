# SpectroCoin Wordpress Crypto Payment Plugin

Integrate cryptocurrency payments seamlessly into your Wordpress store with the [SpectroCoin Crypto Payment Plugin](https://spectrocoin.com/plugins/accept-bitcoin-wordpress-woocommerce.html). This extension facilitates the acceptance of a variety of cryptocurrencies, enhancing payment options for your customers. Easily configure and implement secure transactions for a streamlined payment process on your Wordpress website.

## Installation

0. We strongly reccomend downloading the plugin from Wordpress market. In this case you will be able to update the plugin automatically. In case you are downloading it from Github, please follow the installation steps below.</br>
1. Download plugin files from [github](https://github.com/SpectroCoin/WordPress-WooCommerce-Bitcoin-Payment-Gateway-Plugin).
2. Extract and upload plugin folder to your Wordpress <em>/wp-content/plugins</em> folder.<br />
   OR<br>
   in "Plugins" -> "Add New" -> "Upload Plugin". -> Upload <em>spectrocoin.zip</em>.</br>
3. Go to "Plugins" -> "Installed Plugins" -> Locate installed plugin and click "Activate" -> Click "Settings".

## Setting up

1. [Sign up](https://auth.spectrocoin.com/signup) for a Spectroin Account.
2. [Log in](https://auth.spectrocoin.com/login) to your Spectroin account.
3. On the dashboard, locate the ["Business"](https://spectrocoin.com/en/merchants/projects) tab and click on it.
4. Click on ["New project"](https://spectrocoin.com/en/merchants/projects/new).
5. Fill in the project details and select desired settings (settings can be changed).
6. The Private and Public keys are obtained from your merchant project's settings page. Private key is only displayed once when the project is created, but can be newly generated by pressing on "Generate" button below your Public key field. Copy the newly generated private and public keys and store them in plugin settings.
7. Click "Submit" to save the project and then click "Close".
8. Select the option "All projects" and choose your project.
9. In plugin settings fill the merchant id and project id.

## Make it work on localhost

In order to make the plugin work on localhost for testing purposes, <b>change these 3 lines in <em>SCMechantClient.php createOrder() function</em></b>:

`'callbackUrl' => $request->getCallbackUrl(),
'successUrl' => $request->getSuccessUrl(),
'failureUrl' => $request->getFailureUrl()`

<b>To</b>

`'callbackUrl' => 'http://localhost.com',
'successUrl' => 'http://localhost.com',
'failureUrl' => 'http://localhost.com'`

Don't forget to change it back when migrating website to public.

## Changelog

### Version 1.4.0 MINOR (01/03/2024):

This update is significant to plugin's security and stability. The posibility of errors during checkout is minimized, reduced posibility of XSS and SQL injection attacks.

Migrated: Since HTTPful is no longer maintained, we migrated to GuzzleHttp. In this case /vendor directory was added which contains GuzzleHttp dependencies.

Added: Settings field sanitization.

Added: Settings field validation. In this case we minimized possible error count during checkout, SpectroCoin won't appear in checkout until settings validation is passed.

_Added_: Admin notice in admin plugin settings for all fields validation.

_Added_: Escaping all output variables with appropriate functions.

_Added_: "spectrocoin\_" prefix to functiton names.

_Added_: "SpectroCoin\_" prefix to class names.

_Added_: Validation and Sanitization when request payload is created.

_Added_: Validation and Sanitization when callback is received.

_Added_: Components class "SpectroCoin_ValidationUtil" for specific validation functions.

_Added_: Logging to Wordpress log when errors occur.

_Added_: Logging to WooCommerce status log when errors occur.

_Fixed_: is_available() function sometimes returned false, even if all settings were correct.

_Optimised_: Removed the The whole $\_POST stack processing. Now only needed callback keys is being processed.

_Updated_: Removed hardcoded notice display from admin_options() function.

_Updated_: spectrocoin_admin_error_notice() function, added additional parameter to allow hyperlink display. Also the notice will be displayed once and won't be displayed in other admin screens except SpectroCoin settings.

### Version 1.3.0 MINOR (10/04/2023):

_Fixed_: Replaced hardcoded order statuses in plugin settings.

_Added_: Custom order statuses created manually or using plugins will appear in SpectroCoin settings menu.

_Added_: During checkout, if error is occured, now client will see the error code and message instead of generic error message.

_Added:_ Now plugin checks the FIAT currency, if it is not supported by SpectroCoin, payment will not be available.

_Added:_ Added admin notice in admin plugin settings to notify that shop currency is not supported by SpectroCoin.

### Version 1.2.0 MINOR (09/10/2023):

_Added_: Implemented plugin string internationalization, for plugin translation to various languages.

_Added_: Included two additional links within admin window connecting to official wordpress.org website to easily rate, leave feedback and report bugs.

_Tested_: Tested and checked compatibility with Wordpress 6.3 and WooCommerce 8.0.1

_Modified_: Added style changes in settings window

_For Developers_: Added documentation with parameters and return variables before every function

### Version 1.1.0 MINOR (07/31/2023):

_Added_: Included a new option in admin menu, to display or not the SpectroCoin logo during checkout.

### Version 1.0.0 MAJOR (07/31/2023):

_Fixed:_ Corrected a typo in the plugin's description. Changed "aplugin" to "a plugin" for better clarity.

_Added_: Included a link to access SpectroCoin plugin settings directly from the plugin page. This enhancement provides users with easier access to the configuration options.

_Updated:_ Implemented an "if" statement to handle compatibility with older PHP versions (PHP 8 and below) for the function openssl_free_key($public_key_pem). This change is necessary as PHP 8
deprecates openssl_free_key and now automatically destroys the key instance when it goes out of scope. (Source: https://stackoverflow.com/questions/69559775/php-openssl-free-key-deprecated)

_Improved:_ In the WC_Gateway_Spectrocoin class, made changes to prevent deprecated messages related to the creation of dynamic properties. The properties (merchant_id, protected_id, private_key, and order_status) are now explicitly declared as protected, and getter functions are added to ensure better encapsulation. This update is particularly important for PHP version 8.2 and above.

_Added:_ Specified a dependency on the WooCommerce plugin for the SpectroCoin plugin. The SpectroCoin plugin now requires WooCommerce to be installed and active on the site. If the user deletes or deactivates WooCommerce, a notice will be displayed, and the SpectroCoin plugin will be deactivated automatically.

_Added:_ Enhanced the style of the admin's payment settings window to match the design of SpectroCoin.com, providing a more cohesive user experience.

_Added:_ Introduced an informative message on the admin page, guiding users on how to obtain the mandatory credentials required for using the SpectroCoin plugin effectively. This addition helps users easily find the necessary information for setup and configuration.

## Information

This client has been developed by SpectroCoin.com If you need any further support regarding our services you can contact us via:

E-mail: merchant@spectrocoin.com </br>
Skype: spectrocoin_merchant </br>
[Web](https://spectrocoin.com) </br>
[Twitter](https://twitter.com/spectrocoin) </br>
[Facebook](https://www.facebook.com/spectrocoin/)<br />
