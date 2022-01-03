# chappe

[![Test and Build](https://github.com/valeriansaliou/chappe/workflows/Test%20and%20Build/badge.svg?branch=master)](https://github.com/valeriansaliou/chappe/actions?query=workflow%3A%22Test+and+Build%22) [![NPM](https://img.shields.io/npm/v/chappe.svg)](https://www.npmjs.com/package/chappe) [![Downloads](https://img.shields.io/npm/dt/chappe.svg)](https://www.npmjs.com/package/chappe) [![Buy Me A Coffee](https://img.shields.io/badge/buy%20me%20a%20coffee-donate-yellow.svg)](https://www.buymeacoffee.com/valeriansaliou)

**Developer Docs builder. Write guides in Markdown and references in API Blueprint. Comes with a built-in search engine.**

Chappe is a Developer Docs builder, that produces static assets. No runtime, just lightweight static files. It was built to address SaaS companies needs, and can serve as a first-class modern alternative to hosted services such as [ReadMe](https://readme.com/).

The reason behind why we made Chappe is the following: while looking for a Developer Docs builder at Crisp, all that we could find were either outdated open-source projects, or commercial documentation builders. We wanted a modern Developer Docs website hosted on our premises, as pure-static assets (the latter is especially important, as we do not want to rely on a plethora of external services that can go down anytime).

**Using Chappe is as easy as:**

1. Writing all your docs in Markdown;
2. Building your docs in a single command;
3. Finally, deploying static build assets to your Web servers (or GitHub Pages, Cloudflare Pages, etc. — _this can be automated under GitHub Actions_);

**🇵🇪 Crafted in Lima, Peru.**

## Screenshots & Demo

**👉 See a live demo of Chappe on [Crisp Developer Hub](https://docs.crisp.chat/).**

1️⃣ Chappe can generate your REST API references:

[![Chappe References](https://valeriansaliou.github.io/chappe/images/screenshot-references.gif)](https://docs.crisp.chat/references/rest-api/v1/)

2️⃣ It also generates Markdown-based developer guides:

[![Chappe Guides](https://valeriansaliou.github.io/chappe/images/screenshot-guides.gif)](https://docs.crisp.chat/guides/rest-api/rate-limits/)

3️⃣ Oh, and it also lets your users search anything in your Developer Docs:

[![Chappe Search](https://valeriansaliou.github.io/chappe/images/screenshot-search.gif)](https://docs.crisp.chat/)

_👉 Note that the search engine feature is local. This means that it does not run on an external service like [Algolia](https://www.algolia.com/), though it provides similar search performance and results. The search index is generated at build time as a JSON file, which gets loaded on-demand when the search box gets opened._

## Who uses it?

<table>
<tr>
<td align="center"><a href="https://crisp.chat/"><img src="https://valeriansaliou.github.io/chappe/images/logo-crisp.png" width="64" /></a></td>
</tr>
<tr>
<td align="center">Crisp</td>
</tr>
</table>

_👋 You use Chappe and you want to be listed there? [Contact me](https://valeriansaliou.name/)._

## Last changes

The version history can be found in the [CHANGELOG.md](https://github.com/valeriansaliou/chappe/blob/master/CHANGELOG.md) file.

## Features

* **Simple & fast**: generate a Developer Docs into optimized static assets. No runtime
* **Guides**: write developer guides in Markdown (rich content support: images, videos, tables, etc.)
* **References**: document your HTTP REST API specification using API Blueprint
* **Changes**: maintain a changelog of your platform (eg. your REST API, your SDKs)
* **RSS feed**: users can subscribe to your changelog over RSS
* **Built-in search engine**: the index is generated during build and is hosted locally
* **Fully responsive**: full support of desktop, tablet and phone screens
* **SEO-friendly**: a deep sitemap is generated for search engines
* **Sharing-friendly**: support for the Open Graph protocol
* **Private pages support**: mark any guide or reference as private or unlisted (prefix its name with `_`)

_The following optional features can also be enabled:_

* **Chatbox**: integrate with the [Crisp Chatbox](https://crisp.chat/en/livechat/) to handle tech support and collect user feedback
* **Status page**: integrate with your [Vigil](https://github.com/valeriansaliou/vigil) status page to report live system status

## How to use it?

### Installation & Overview

To install and use Chappe, please follow those steps:

1. Create a new, empty Git repository;
2. Copy the `examples/crisp-docs/` folder contents from the Chappe repository into your project root;
3. Run: `npm install`;
4. Write your Markdown guides and references in the `data/` directory;
5. Run: `npx chappe` to build the docs;
6. Upload the contents of the `dist/` folder to your Web server (at the root);

Please refer to sections below for more details on how to write docs, customize Chappe, and deploy your docs to your Web server.

### Configuration

The configuration of your Chappe docs is stored in a single JSON file, usually named `config.json`. Your configuration file will make references to images, such as your docs logo, which are stored in the `assets/` folder.

An empty definition of the Chappe configuration file is available in: [res/config/user.json](https://github.com/valeriansaliou/chappe/blob/master/res/config/user.json), although you may rather want to see a filled example: [examples/crisp-docs/config.json](https://github.com/valeriansaliou/chappe/blob/master/examples/crisp-docs/config.json)

Common configuration needs are covered below.

###### Customize your docs favicons:

TODO

###### Set an illustration on the homepage:

TODO

###### Configure the header menus & navigation links:

TODO

###### Set icons for `guides` and `references` categories:

TODO

###### Define categories for `changes`:

TODO

###### Configure the URL of your Vigil status page:

TODO

###### Enable the Crisp Chatbox:

TODO

###### Available code coloring:

TODO: list them all

###### Check file sizes during build:

TODO

### Chappe CLI usage

Chappe provides you with the `chappe` command, that builds your docs.

It supports the following parameters, with a default value if not set:

* `--config` (_default:_ `./config.json`)
* `--assets` (_default:_ `./assets`)
* `--data` (_default:_ `./data`)

To build your docs, you can call `chappe` as such:

`npx chappe --config=./config.json --assets=./assets --data=./data`

_👉 If the `chappe` command is not found, make sure to add `chappe` to your `package.json` and call `npm install`._

### Writing docs

Docs can be either: `guides`, `references` or `changes`. The corresponding folders are stored in the `data/` directory, which is passed to the Chappe CLI whenever building your docs.

`guides` are articles that walk your users through using your systems ([exemple here](https://docs.crisp.chat/guides/rest-api/rate-limits/)). They are written in Markdown, and are organized in sub-folders if deep nesting of guides in several sections is required. Chappe will auto-generate the navigation sidebar for you, based on this folder hierarchy.

`references` are formal specifications of your systems (exemples of: [API Blueprint](https://docs.crisp.chat/references/rest-api/v1/) and [Markdown](https://docs.crisp.chat/references/rtm-api/v1/)). They are written in [API Blueprint](https://apiblueprint.org/) for your HTTP REST API (a pseudo-Markdown format), or traditional Markdown for other systems (eg. a WebSocket server).

`changes` is a timeline of updates that you made to your systems ([exemple here](https://docs.crisp.chat/changes/)). They are defined in a JSON format. In addition to the timeline, an RSS feed also gets generated at the `/changes.rss` URL.

### Deploying your docs

To deploy your docs, first, create a Virtual Host on your Web server, using a dedicated domain, eg. `docs.acme.com`.

Then, after you built Chappe (on your local computer or a CI/CD runner such as GitHub Actions), copy the contents of the `dist/` folder to your server folder for your docs Virtual Host (eg. `/var/www/docs.acme.com`).

⚠️ Chappe **must** be hosted at the root of your docs domain, it **will not** work if hosted in a sub-directory!

Here is an example configuration file for NGINX on the Virtual Host `docs.acme.com`:

```
server {
  listen 443;
  server_name docs.acme.com;

  root /var/www/docs.acme.com;

  error_page 404 /not_found/;
}
```

_👉 Note that if possible, you should make sure that you have a rule to catch 404 errors and show the `not_found` page (as the NGINX configuration file above shows)._

## Syntax guide

### How to write guides?

TODO

### How to write references?

TODO

### How to write changelogs?

TODO

## Common questions

### How can I customize my docs style?

In order to customize your docs style — ie. override the default Chappe style past what can already be customized in the `config.json` configuration file — open `config.json` and look for the `includes` property (that contains `stylesheets`, that contains `urls` and `inline`).

You can easily deploy your own custom stylesheet on your docs domain, along with Chappe, with CSS classes overriding Chappe default styles:

```json
// (...)

"includes" : {
  // (...)

  "stylesheets" : {
    "urls"   : [
      "/overrides/style.css"
    ],

    "inline" : []
  }
},

// (...)
```

### How can I add scripts like Google Tag Manager?

To add inline scripts such as Google Tag Manager, open your `config.json` configuration file for Chappe, and look for the `includes` property (that contains `scripts`, that contains `urls` and `inline`).

Add a new entry to the `urls` and `inline` array, separately, giving eg.:

```json
// (...)

"includes" : {
  "scripts" : {
    "urls"   : [
      "https://www.googletagmanager.com/gtag/js?id={YOUR_GTM_ID}"
    ],

    "inline" : [
      "window.dataLayer = window.dataLayer || [];\nfunction gtag(){dataLayer.push(arguments);}\ngtag(\"js\", new Date());\ngtag(\"config\", \"{YOUR_GTM_ID}\");"
    ]
  },

  // (...)
},

// (...)
```

The `urls` property will include the JavaScript at the provided URL on all pages, while the `inline` property will append the inline JavaScript in a `script` element on all pages.

### How can I deploy my docs to GitHub Pages?

TODO

### Where does the Chappe name come from?

Chappe was named after [Claude Chappe](https://en.wikipedia.org/wiki/Claude_Chappe), a French inventor, pioneer in long-distance communications. He invented the [optical telegraph](https://en.wikipedia.org/wiki/Optical_telegraph) (a.k.a. semaphore telegraph), later replaced by the [electrical telegraph](https://en.wikipedia.org/wiki/Electrical_telegraph). Those technologies were the founding blocks of what took over the world next: analog and digital telecommunications.

Quoting from his page on Wikipedia:

> This [the optical telegraph] was the first practical telecommunications system of the industrial age, and was used until the 1850s when electric telegraph systems replaced it.

_Credits to [Baptiste Jamin](https://github.com/baptistejamin) for the name idea._
