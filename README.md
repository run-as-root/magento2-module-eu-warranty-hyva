# RunAsRoot_EuWarrantyHyva

Hyvä Theme compatibility module for [`run-as-root/module-eu-warranty`](https://github.com/run-as-root/magento2-module-eu-warranty).

The base module shows the official EU legal guarantee notice on the `/eu-warranty` storefront page and in order confirmation emails. Its page template is built for Luma. This module replaces that template with a Tailwind-based one, so the page renders properly on Hyvä themes.

## What it does

- Registers itself in Hyvä's `CompatModuleRegistry` (`etc/frontend/di.xml`) as the compat module for `RunAsRoot_EuWarranty`. On Hyvä themes, Hyvä's compat module fallback then picks up this module's templates instead of the originals.
- Ships a Hyvä version of the notice page template, `view/frontend/templates/notice/page.phtml`. It renders:
  - the notice image, styled with Tailwind utility classes;
  - a link to the full legal text on europa.eu, with a Heroicons external-link icon from Hyvä's `HeroiconsOutline` view model.
- Renders nothing when **Notice Page > Enabled** is off in the base module's configuration.

Everything else comes from the base module: configuration, the `/eu-warranty` route, the notice language setting and the order email integration. The email part doesn't depend on the theme, so this module doesn't touch it.

## Installation

```bash
composer require run-as-root/module-eu-warranty-hyva
```

No configuration is needed. Configure the notice in the base module under **Stores > Configuration > General > EU Warranty Information**. See the base module's README for details.

## Customizing

To change the markup, override `RunAsRoot_EuWarranty::notice/page.phtml` in your Hyvä child theme the usual way. Your theme's template takes precedence over this module's.

## License

OSL-3.0
