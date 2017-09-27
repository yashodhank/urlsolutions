# Installation

1. Extract the `urlsolutions-2.*.*.zip`. Move `urlsolutions` folder to WHMCS registrars modules directory. It location depends on the WHMCS version:

- For WHMCS version 7 and abobe - `<whmcs root directory>/public_html/modules/registrars/`
- For WHMCS versions below version 7 - `<whmcs root directory>/modules/registrars`

Please remove the previous module version first.

# Configuration

In the beginning make sure that you have your API key(signature). Keys can be generated from the [Signatures section](https://mcp-admin.pananames.com/profile/signatures) on the site. You can generate API key for specific IP address (recommended), so this key won’t work from all other IP addresses.

You should login into WHMCS admin area.

1. Add two new custom client fields using the `Setup → Custom Client Fields` Menu.

 - `Country Code` with validation /^([0-9]{1,3}$/
 - `Phone Number` with validation /^[0-9]{7,14}$/

2. Go to `Setup → Product & Services → Domain registrars` and activate URLSolutions module.

3. Click `Configure` button in URLSolution module row and fill fields.

- `URL` for API environment. Staging - `https://api-staging.pananames.com/merchant/v2/`. Production - `https://api.pananames.com/merchant/v2/`
- `Signature`. Note that API keys from staging evironment will not work with production and otherwise.


4. At the end you have to add a cron job as shown below:.

For WHMCS version 7 and above

```
5 */7 * * * /opt/php/5.6/bin/php -q <whmcs root directory>/public_html/modules/registrars/urlsolutions/urlsolutionssync.php
```

For WHMCS versions below version 7

```
5 */7 * * * /opt/php/5.6/bin/php -q <whmcs root directory>/modules/registrars/urlsolutions/urlsolutionssync.php
```

Now you can try to register a domain name. Make sure custom fields are filled, registrar requires country code and phone number to be separate.

# Documentation

- [Staging environment](https://docs-staging.pananames.com/)
- [Production environment](https://docs.pananames.com/)