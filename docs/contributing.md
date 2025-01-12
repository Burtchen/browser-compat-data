# Contributing to browser-compat-data

We're really happy to accept contributions to the mdn/browser-compat-data repository!

## Table of contents

1. [Before you begin](#before-you-begin)
2. [Ways to contribute](#ways-to-contribute)
3. [Finding browser version numbers for features](#finding-browser-version-numbers-for-features)
4. [Updating compatibility tables on MDN](#updating-compatibility-tables-on-mdn)
5. [Opening issues and pull requests](#opening-issues-and-pull-requests)
   1. [Optional: Generating data using the Web API Confluence Dashboard](#optional-generating-data-using-the-web-api-confluence-dashboard)
   1. [Optional: Generating data using the mdn-bcd-collector project](#optional-generating-data-using-the-mdn-bcd-collector-project)
   1. [Optional: Generating data by mirroring](#optional-generating-data-by-mirroring)
6. [Getting help](#getting-help)

## Before you begin

The browser-compat-data project (BCD) welcomes contributors of all kinds, but we ask that you keep these guidelines in mind when you're contributing.

The project requires that all contributors follow [Mozilla's code of conduct and etiquette guidelines](/CODE_OF_CONDUCT.md).

This project has [a formal governance document](/GOVERNANCE.md), which describes how various types of contributors work within the project and how decisions are made.

The repository is made available under the terms the [Creative Commons CC0 Public Domain Dedication](/LICENSE). Any contributions must be compatible with its terms. If you're not sure about that, [please ask](#getting-help).

## Ways to contribute

There are many ways you can help improve this repository! For example:

- **Add new compat data**: familiarize yourself with the [schema](../schemas/compat-data.schema.json) and read the [schema docs](../schemas/compat-data-schema.md) and [data guidelines](data-guidelines.md) to add new files.
- **Fix existing compat data**: maybe a browser now supports a certain feature. Yay! If you open a PR to fix a browser's data, it would be most helpful if you include a link to a bug report or similar so that we can double-check the good news.
- **Fix a bug:** we have a list of [issues](https://github.com/mdn/browser-compat-data/issues),
  or maybe you found your own.
- **Review a pull request:** there is a list of [PRs](https://github.com/mdn/browser-compat-data/pulls).
  Let us know if these look good to you.

## Finding browser version numbers for features

When adding data for a particular feature, you'll often need to find which version of each browser the feature first shipped in. For how-to guidance which will help you do that, see [Matching web features to browser release version numbers](https://developer.mozilla.org/docs/MDN/Contribute/Processes/Matching_features_to_browser_version).

## Updating compatibility tables on MDN

It takes up to four weeks for BCD changes to be reflected in MDN's browser compatibility tables.
The process is:

1. A pull request is reviewed and merged to `main`.
2. Project owners publish a new release of [`@mdn/browser-compat-data`](https://www.npmjs.com/package/@mdn/browser-compat-data).
   See [Publishing a new version of `@mdn/browser-compat-data`](publishing.md) for details.
3. MDN staff build and deploy a new image of [Kumascript](https://github.com/mdn/yari/tree/main/kumascript), which includes the BCD release, to production.
   This typically happens within a day of the release of the npm package.
4. Tables are generated on MDN:

   - Existing tables automatically regenerate monthly.
     Alternatively, logged-in MDN users can [force-refresh a page](https://en.wikipedia.org/wiki/Wikipedia:Bypass_your_cache#Bypassing_cache) to regenerate it.
   - For new pages, you must add the [`{{Compat}}`](https://github.com/mdn/kumascript/blob/master/macros/Compat.ejs) macro to the page.
     For instructions, see [Inserting the data into MDN pages](https://developer.mozilla.org/en-US/docs/MDN/Contribute/Structures/Compatibility_tables#Inserting_the_data_into_MDN_pages).

Large-scale changes follow a different process. See [Migrations](migrations.md) for details.

## Opening issues and pull requests

Before submitting your pull request, [validate your new data against the schema](testing.md).

Not everything is enforced or validated by the schema. A few things to pay attention to:

- Feature identifiers (the data namespaces, like `css.properties.background`) should make sense and are spelled correctly.
- Nesting of feature identifiers should make sense.
- Notes use correct grammar and spelling. They should be complete sentences ending with a period.

### Optional: Generating data using the Web API Confluence Dashboard

If the feature you're interested in is a JavaScript API, you can cross-reference data against [Web API Confluence](https://web-confluence.appspot.com/) using the `confluence` command. This command overwrites data in your current working tree according to data from the dashboard. See [Using Confluence](using-confluence.md) for instructions.

### Optional: Generating data using the mdn-bcd-collector project

If the feature you're interested in is an API, CSS or JavaScript feature, you can cross-reference data against [mdn-bcd-collector](https://mdn-bcd-collector.appspot.com/). See the project's guide on [updating BCD using the results](https://github.com/foolip/mdn-bcd-collector#updating-bcd-using-the-results) for instructions.

### Optional: Generating data by mirroring

Many browsers within BCD can be derived from other browsers given they share the same engine, for example Opera derives from Chrome, and Firefox Android derives from Firefox. To help cut down time working on copying values between browsers, contributors may specify a special value in the data to automatically mirror the data from their upstream counterparts. See the [schema documentation](../schemas/compat-data-schema.md#mirroring-data) for more info.

Note: originally, this functionality used to be provided as an executable script. However, because the script had to be run manually, this meant that mirrored data would become stale rapidly. It was proposed in [#15083](https://github.com/mdn/browser-compat-data/issues/15083) to move the mirroring into a build step to reduce maintenance time.

## Getting help

If you need help with this repository or have any questions, contact the MDN team on [chat.mozilla.org#mdn](https://chat.mozilla.org/#/room/#mdn:mozilla.org) or write to us on [Discourse](https://discourse.mozilla-community.org/c/mdn).
