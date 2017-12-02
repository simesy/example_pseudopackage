# Pseudo package example - D8 JSON API

This is an example of how distributions should separate functionality into
pseudo-packages. It is derived from how the Contenta profile sets up Drupal
as a headless application.

Contribute to the conversation here: https://github.com/contentacms/contenta_jsonapi/issues/232

## The problem

Many distributions (type: drupal-profile) include a wide range of module requirements.
When you inspect these distributions, the functional areas are usually separated,
and there are usually instructions about how to turn these on and off. 

There is a huge overlap between distributions. And the problem is you can't
pick and choose these features from different distributions.

It's untenable to add multiple distribution profiles to a website codebase, for the purpose
of using some of these features, for a few reasons:

- Any custom logic (eg modules) in the second profile is not accessible to Drupal
- Profiles usually contain very specific logic which is incompatible with other profiles
- Unrequired module dependencies of Profile B may conflict with need modules required by Profile A
- You can't easily allow a sub-set of patches to be applied from another package

For example, due to the way composer works, you can't have Lighting Media without
Composer resolving and downloading a large suite of modules related to Lighting Layouts. (Or can you?)

## But config?

All distributions recognise that, once installed, config diverges from the
distribution. A pseudo package should be responsible for having tools (think drush
commands or status page alerts) that inform a website administrator of 
important upstream (default) config changes that are related to the pseudo-package.

## Should a pseudo package have a module?

Yes a module could provide additional functionality. As long as it
isn't too opinionated. The "Lightning Media" module should not assume it is being used
in Lightning, it might be being used in Contenta or Thunder.

## Examples

These should be in pseudo-packages to encourage re-usability outside their
corresponding profiles. In some cases below, the overlap is really not necessary.
These distributions should be sharing code and not reimplementing.

Four examples, with links to each distribution's "features" directory.

[Lightning](https://github.com/acquia/lightning/tree/8.x-2.x/modules/lightning_features)

- Lighting workflow
- Lightning media
- Lightning layouts
- Lightning API

[Thunder](https://github.com/BurdaMagazinOrg/thunder-distribution/tree/develop/modules)

- Thunder media
- Thunder paragraphs
- Thunder articles

[Open Social](https://github.com/goalgorilla/open_social/tree/8.x-1.x/modules/social_features)

- Social SSO
- Social editor
- Social mentions 
- many more ...

[Varbase](https://github.com/Vardot/varbase/tree/8.x-4.x/modules/varbase_features)

- varbase_media
- varbase_internationalization
- many more ...


Bonus Example. Distributions which all repeat a similar JSON API set up.

- Contenta
- Lighting
- Headless Lighting
- Reservoir
