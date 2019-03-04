# Twig templates for German DSGVO / GDPR 

## The Goal 

This templates collection shall provide you [ready-to-use snippets](#available-templates) which only need context variables to be filled in. Any user feel invited to [contribute!](#contributions-welcome)

## Use at own risk

**As “best practices” have not evolved yet, the texts provided here can not be considered “legally bullet-proof”.** In any case, stay in touch with your Data Protection Officer.

## DSGVO Readings


**Jens Kubieziel's [DSGVO-Liste](https://github.com/qbi/DSGVO-Liste)** on GitHub   
„Informationsquellen und weitere Ressourcen zur Datenschutz-Grundverordnung“ 

**Lukas Leitsch's [DSGVO-Checkliste](https://github.com/lukasleitsch/dsgvo-checkliste)** on GitHub  
„Eine Übersicht für Website-Betreiber“



## Installation

Whilst templates are not PHP, Composer makes it easy to download the templates somewhere and update automatically. Feel free to propose an handsome alternative, opening a new issue: [issues list.][i0]

```bash
$ composer require tomkyle/dsgvo-twig
```

To obtain the stable release one day, use this:

```bash
$ composer require tomkyle/dsgvo-twig:">0.2|^1.0"
```

## Usage

First add `vendor/tomkyle/dsgvo-twig/templates`to Twig's template paths. Make sure to *append* the templates directory to make sure you can *override* the default template with a customized copy in your primary (app) templates directory. 

See Twig's documentation on [File system loaders](https://twig.symfony.com/doc/2.x/api.html#built-in-loaders).

```php
<?php
// The path where Composer installs this package
$dsgvo_templates_path = 'vendor/tomkyle/dsgvo-twig/templates';

// Instantiate Loader
$loader = new Twig_Loader_Filesystem([
	'my_templates',
	$dsgvo_templates_path
]);

// Alternatively, add DSGVO templates after instantiation
$loader = ...
$loader->addPath( $dsgvo_templates_path );
```



## Available Templates

Jump directly to:

- [Intro text](#dsgvointrotwig)
- [Responsible organisation](#dsgvoresponsibletwig)
- [Data Protection Officer](#dsgvodpotwig)
- [Security with SSL/HTTPS](#dsgvohttpstwig)
- [Google ReCAPTCHA](#dsgvogoogle-recaptchatwig)
- [Webfonts via Typekit](#dsgvowebfonts-typekittwig)
- [Videos via YouTube](#dsgvovideos-youtubetwig)
- [Subject to change](#dsgvochangestwig)



### [dsgvo.intro.twig](templates/dsgvo.intro.twig)

Some basic introductory text for the top of your privacy terms page.

```php
<?php
echo $twig->render('dsgvo.intro.twig', [
	'company' => 'The ACME Company',
	
	// optional
	'company_shortname' => 'ACME'
]);
```

### [dsgvo.responsible.twig](templates/dsgvo.responsible.twig)

Information about the responsible organisation for your website.

```php
<?php
echo $twig->render('dsgvo.resonsible.twig', [
	'website_name' => 'www.test.com',
	'email'    => 'info@test.com',
	
	// optional:
	'company'      => 'MUSTER-Firma GmbH',
	'address'  => 'Musterstrasse 5',
	'zip'      => '99999',
	'city'     => 'Musterstadt',
	'phone'    => '+4940123456789',
    'title'         => 'Verantwortlicher und Geltungsbereich',
    'website_realm' => 'das Internetangebot',
	'law_name'      => 'EU-Datenschutz-Grundverordnung',
	'law_shortname' => 'DSGVO',
	'company_shortname' => 'MUSTER',
	'region'        => 'Schleswig-Holstein',
	'country'       => 'Deutschland',
	'phone_display' => '+49 (040) 12345678-9',
	'fax_display'   => '+49 (040) 12345678-1'
]);
```

### [dsgvo.dpo.twig](templates/dsgvo.dpo.twig)

Information about the DPO (Data Processing Officer) for your organisation.

```php
<?php
echo $twig->render('dsgvo.dpo.twig', [
	'external' => true,
	'name'     => 'John Doe',
	'address'  => 'Musterstrasse 5',
	'zip'      => '99999',
	'city'     => 'Musterstadt',
	'phone'    => '+4940123456789',
	'email'    => 'privacy@test.com',
	
	// optional:
	'jobtitle' => 'Zertifiziert als Datenschutzbeauftragter',
	'company'  => 'The External DPO Comp.',
	'region'   => 'Schleswig-Holstein',
	'country'  => 'Deutschland',
	'phone_display' => '+49 (040) 12345678-9',
	'fax_display'   => '+49 (040) 12345678-1'
]);
```



### [dsgvo.rights.twig](templates/dsgvo.rights.twig)

Information about the user's privacy rights

```php
<?php
echo $twig->render('dsgvo.rights.twig');
```



### [dsgvo.contact.twig](templates/dsgvo.contact.twig)

Information about how to contact your company (via email and/or contact form)

```php
<?php
echo $twig->render('dsgvo.contact.twig', [
	'contactform' => true        
]);
```



### [dsgvo.https.twig](templates/dsgvo.https.twig)

Information about SSL/HTTPS transportation.

```php
<?php
echo $twig->render('dsgvo.https.twig');
```



### [dsgvo.cookies.twig](templates/dsgvo.cookies.twig)

Information about using cookies and how to avoid them.

```php
<?php
echo $twig->render('dsgvo.cookies.twig');
```



### [dsgvo.links.twig](templates/dsgvo.links.twig)

External links disclaimer

```php
<?php
echo $twig->render('dsgvo.links.twig');
```



### [dsgvo.google-recaptcha.twig](templates/dsgvo.google-recaptcha.twig)

Information about Google ReCAPTCHA

```php
<?php
echo $twig->render('dsgvo.google-recaptcha.twig', [
	// optional:
	'google_policy_url' => 'https://www.google.de/intl/de/policies/privacy/',
	'legal_basis'        => 'Art.&thinsp;6&nbsp;Abs.&thinsp;1&nbsp;lit.&thinsp;b,c&nbsp;DSGVO'
]);
```



### [dsgvo.webfonts-typekit.twig](templates/dsgvo.webfonts-typekit.twig)

Information about webfonts used on your site.

```php
<?php
echo $twig->render('dsgvo.webfonts-typekit.twig', [
	// optional:
	'typekit_policy_url' => 'https://www.adobe.com/de/privacy/policies/typekit.html',
	'typekit_url'        => 'https://typekit.com',
	'legal_basis'        => 'Art.&thinsp;6&nbsp;Abs.&thinsp;1&nbsp;lit.&thinsp;f&nbsp;DSGVO'
]);
```



### [dsgvo.videos-youtube.twig](templates/dsgvo.videos-youtube.twig)

Information about using cookieless YouTube.

```php
<?php
echo $twig->render('dsgvo.videos-youtube.twig', [
	// optional:
	'google_policy_url' => 'https://www.google.de/intl/de/policies/privacy/'
]);
```



### [dsgvo.changes.twig](templates/dsgvo.changes.twig)

Information about what is called „Änderungsvorbehalt“ in German.

```php
<?php
echo $twig->render('dsgvo.changes.twig');
```





## Contributions welcome!

Any contribution and proposal with this is highly appreciated. Stay up to-date on [issues list.][i0] Also checkout the [Wishlist][wishlist].

[i0]: https://github.com/tomkyle/dsgvo-twig/issues
[wishlist]: https://github.com/tomkyle/dsgvo-twig/issues/4


## Development

```bash
$ git clone git@github.com:tomkyle/dsgvo-twig.git
$ cd dsgvo-twig
$ composer install
```



## Unlicense

This is free and unencumbered software released into the public domain.

Anyone is free to copy, modify, publish, use, compile, sell, or
distribute this software, either in source code form or as a compiled
binary, for any purpose, commercial or non-commercial, and by any
means.

In jurisdictions that recognize copyright laws, the author or authors
of this software dedicate any and all copyright interest in the
software to the public domain. We make this dedication for the benefit
of the public at large and to the detriment of our heirs and
successors. We intend this dedication to be an overt act of
relinquishment in perpetuity of all present and future rights to this
software under copyright law.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND,
EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF
MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.
IN NO EVENT SHALL THE AUTHORS BE LIABLE FOR ANY CLAIM, DAMAGES OR
OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE,
ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR
OTHER DEALINGS IN THE SOFTWARE.

For more information, please refer to <http://unlicense.org>

