Start neues Semester

### 1. Pages

Pages vom vorherigen Semester unbennen

- Thematik zu Thematik (Semester+Jahr) unbennen
- Themensponsoren zu Themensponsoren (Semester+Jahr) unbennen

Neue Pages erstellen

- Thematik
- Themensponsoren

### 2. Tags

- neuer Tag mit Semester + Jahr z.B FS23
- Verlinkungen bei Tag description hinzufügen (in HTML)

### 3. About-Seite (Über diese Lehrveranstaltung)

Neues Toggle erstellen für vorheriges Semester

- In eine Zeile klicken -> aufs + ->Toggle auswählen

  ![Toggle-image](/assets/images/about.png)

- Toggle header: Thema (Semester Jahr)
- Collapsible content: - Showroom -Thematik -Themensponsoren
- mit Doppelklick aufs Wort Verlinkungen hinzufügen
- URL Thematik und Sponsoren: Pages-> Thematik-> oben rechts auf Vierreck -> unter Page URL in Grau:

  ![Toggle-image](/assets/images/thematik.png)

- URL Showroom: Tags -> Semester auswählen -> unten am Slug in Grau geschrieben:

  ![Toggle-image](/assets/images/tags.png)

### 3. Navigation

- URL bei Thematik und Themensponsor anpassen

### **Wichtig für Studierende:**

Alle Posts vom Semester X müssen mit dem Tag SemesterX getagt werden.Falls ein Post mehrere Tags hat muss der SemesterX der erste Tag sein. Ansonsten können die Posts nicht nach Semester zugeteilt werden.

### Routing

Damit auf Home nur Content vom aktuelle Semester angezeigt wird müssen die anderen Semester ausgeblendet werden.

Gehe zu: Content/settings/routes.yaml

Nach jedem Semester muss beim Filter das alte Semester hinzugefügt werden, damit dieses auf der Home Seite ausgeblendet wird.

```
 collections:
  /fs/:
    permalink: /fs/{slug}/
    template: index
    filter: primary_tag:[hs21] #hs21 wird jetzt nicht auf home(index) angezeigt
  /:
    permalink: /{slug}/
    template: index

taxonomies:
  tag: /tag/{slug}/
  author: /author/{slug}/
```

z.B nach Ende FS22 muss der filter so angepasst werden:

```
 filter: primary_tag:[hs21,fs22]
```

Nach Anpassung Filter yaml Datei wieder hochladen.

# Casper

The default theme for [Ghost](http://github.com/tryghost/ghost/). This is the latest development version of Casper! If you're just looking to download the latest release, head over to the [releases](https://github.com/TryGhost/Casper/releases) page.

&nbsp;

![screenshot-desktop](https://user-images.githubusercontent.com/353959/66987533-40eae100-f0c1-11e9-822e-cbaf38fb8e3f.png)

&nbsp;

# First time using a Ghost theme?

Ghost uses a simple templating language called [Handlebars](http://handlebarsjs.com/) for its themes.

This theme has lots of code comments to help explain what's going on just by reading the code. Once you feel comfortable with how everything works, we also have full [theme API documentation](https://ghost.org/docs/themes/) which explains every possible Handlebars helper and template.

**The main files are:**

- `default.hbs` - The parent template file, which includes your global header/footer
- `index.hbs` - The main template to generate a list of posts, usually the home page
- `post.hbs` - The template used to render individual posts
- `page.hbs` - Used for individual pages
- `tag.hbs` - Used for tag archives, eg. "all posts tagged with `news`"
- `author.hbs` - Used for author archives, eg. "all posts written by Jamie"

One neat trick is that you can also create custom one-off templates by adding the slug of a page to a template file. For example:

- `page-about.hbs` - Custom template for an `/about/` page
- `tag-news.hbs` - Custom template for `/tag/news/` archive
- `author-ali.hbs` - Custom template for `/author/ali/` archive

# Development

Casper styles are compiled using Gulp/PostCSS to polyfill future CSS spec. You'll need [Node](https://nodejs.org/), [Yarn](https://yarnpkg.com/) and [Gulp](https://gulpjs.com) installed globally. After that, from the theme's root directory:

```bash
# install dependencies
yarn install

# run development server
yarn dev
```

Now you can edit `/assets/css/` files, which will be compiled to `/assets/built/` automatically.

The `zip` Gulp task packages the theme files into `dist/<theme-name>.zip`, which you can then upload to your site.

```bash
# create .zip file
yarn zip
```

# PostCSS Features Used

- Autoprefixer - Don't worry about writing browser prefixes of any kind, it's all done automatically with support for the latest 2 major versions of every browser.
- [Color Mod](https://github.com/jonathantneal/postcss-color-mod-function)

# SVG Icons

Casper uses inline SVG icons, included via Handlebars partials. You can find all icons inside `/partials/icons`. To use an icon just include the name of the relevant file, eg. To include the SVG icon in `/partials/icons/rss.hbs` - use `{{> "icons/rss"}}`.

You can add your own SVG icons in the same manner.

# Copyright & License

Copyright (c) 2013-2021 Ghost Foundation - Released under the [MIT license](LICENSE).
