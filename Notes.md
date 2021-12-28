# Notes for "Bootstrap 5 Crash Course" from Net Ninja.

## Lesson 1
Get started.

Create index.html in vscode.

Type doc and then hit tab to create boilerplate HTML 5 doc.

Copy Bootstrap CDN links to paste into index.html file:

https://getbootstrap.com/docs/5.0/getting-started/download/

Install and enable Live Server (Ritwick Dey) extension for vscode.

Open index.html with Live Server by right-clicking and choosing "Open with Live Server".

Note that font family is no longer default Times New Roman, but now Sans Serif.

Create assets folder and download files from lesson-1 branch of git repo.

My local repo already has lesson branches, so I can check out individual files from the lesson branches (make sure to change directory to the target folder).

```bash
$ cd assets
```

First show all the files in source folder. In the case of /assets:

```bash
$ git show lesson-1:assets

tree lesson-1:assets

ebook-cover.png
kindle.png
```
Then checkout each file into main's assets directory:

```bash
$ git checkout lesson-1 ebook-cover.png
$ git checkout lesson-1 kindle.png
```

NOTE: reverse the last commit with:

```bash
$ git reset --soft HEAD~1
```

## Lesson 2
New features in Bootstrap 5.

* Bootstrap 5 has dropped jQuery!
* Forms revamped
* Right-to-Left support added
* New utility classes
* Minor changes to some components and grid (Jumbotron gone)
* Bootstrap icons
* Two new components: off canvas and accordion

Bootstrap documentation:

https://getbootstrap.com/docs/5.0/getting-started/download/

## Lesson 3
Colors and Typography.

"Reboot" of the default browser styles (colors, margins, typography). Replaces with a clean basic set of bootstrap styles.

Display headings, ```class="display-1"```.

In vscode type

```html
h1.display-1
```

Then hit tab and build-in emmet will create class:

```html
<h1 class="display-1"></h1>
```

Lead text, ```class="lead"```.

Generate Lorem ipsum text by starting a line with ```lorem8``` and then hitting tab (number indicates how may words should be in sentence)/

Text decoration, ```class="text-decoration-underline```.

Theme colors

Primary, Secondary, Success, Danger, Warning, Info, Light, Dark.

## Lesson 4
Buttons.

```html
<button class="btn btn-secondary">secondary button</button>
```

Anchor tags as buttons:

```html
<a href="#" class="btn btn-success">success anchor tag</a>
```

Button sizes:

```html
<button class="btn btn-lg btn-danger">large danger button</button>
```

Outlined styles:

```html
<button class="btn btn-outline-primary">outlined primary button</button>
```

Button groups:

```html
<div class="btn-group">
    <a href="#" class="btn btn-primary">button 1</a>
    <a href="#" class="btn btn-warning">button 2</a>
</div>
```

## Lesson 5
Utility Classes.

Margin and padding:

```html
<div class="bg-primary m-5 p-5">large margin and padding</div>
```

Borders:

```html
<div class="m-3 p-3 rounded border border-5">rounded corners</div>
```

Box shadow:

```html
<div class="m-3 p-3 shadow-lg">element with large box shadow</div>
```

Font weight:

```html
<p class="fw-bold">bold text</p>
<p class="fst-italic">italic text</p>
```

fw - font weight
fst - font style

## Lesson 6
Containers.

```html
<div class="container">
```

```html
<div class="container-fluid">
````

```html
<div class="container-lg">
```

```html
<div class="container-xl">
```


## Lesson 19 Customizing Bootstrap

### Override values of existing bootstrap css defaults
Can do this by either creating your own stylesheet, or using a sass file.

To use a sass file you need a local copy of bootstrap. This can be installed using npm (be sure to add source from [Node.gitignore](https://github.com/github/gitignore/blob/master/Node.gitignore) to your .gitignore).

In project folder, create node project with new package.json:

```bash
$ npm init
```

Install bootstrap:

```bash
$ npm install bootstrap
```

This will install latest bootstrap. If you're going to continue to use bootstrap js from the cdn, be sure js version matches the new bootstrap css just installed.

Now create sass folder, and under it a main.scss file.

```scss

// import bootstrap
@import '../node_modules/bootstrap/scss/bootstrap';
```

The import line imports standard bootstrap. Change default values for variables in lines above this:

```scss
// custom variables
$primary: #c29938;
$light: #fbf5e5;

// import bootstrap
@import '../node_modules/bootstrap/scss/bootstrap';
```

Install [Live Sass Compiler](https://github.com/ritwickdey/vscode-live-sass-compiler) in VS Code. This will watch the /sass folder for changes and compile them into a new bootstrap min.css file.

Configure Live Sass Compiler, by adding to VSCode .vscode/settings.json:

```json
    "liveSassCompile.settings.formats": [

        {
            "format": "compressed",
            "extensionName": ".min.css",
            "savePath": "/css" 
        }
    ],
    "liveSassCompile.settings.autoprefix": [],
```
Tutorial had you change the global settings.json for VSCode, but doc for the extension recommended using a local settings file for each project. I modified to make this:

```json
{
    "liveSassCompile.settings.formats": [

        {
            "format": "expanded",
            "extensionName": ".css",
            "savePath": "/css" 
        },
        {
            "format": "compressed",
            "extensionName": ".min.css",
            "savePath": "/css" 
        }
    ],
    "liveSassCompile.settings.excludeList": [
        "**/node_modules/**",
        ".vscode/**"
    ],
    "liveSassCompile.settings.generateMap": true,
    "liveSassCompile.settings.autoprefix": [],
}
```
I opted to include an expanded main.css so I could more easily verify the changes I was making.

This will automatically re-compile a new main.min.css in the /css folder every time a change is made to main.scss under /sass.

To enable, click on the "Watch Sass" button on the bottom notification bar in VSCode.

Finally, change line in head to point at the new minified css:

```html
<link href="/css/main.min.css" rel="stylesheet">
```

### Adding new bootstrap css values

To add new variables, first need to include bootstrap _modules and _functions in main.scss:

```scss
// import the functions & varibales
@import "../node_modules/bootstrap/scss/_functions";
@import "../node_modules/bootstrap/scss/_variables";
```
Then add map for new custom colors and merge with original theme map:

```scss
// import the functions & varibales
@import "../node_modules/bootstrap/scss/_functions";
@import "../node_modules/bootstrap/scss/_variables";

$custom-theme-colors: (
    "altlight": #f2ebfa,
    "altdark": #522192
);

$theme-colors: map-merge($custom-theme-colors, $theme-colors);
```
The recompiled css will now include altlight and altdark for all elements, like btn, etc.

Except bg. For some reason, it did not create bg-altlight and bg-altdark.

To get new background colors (as well as new colors for other elements), add a loop after loading the bootstrap scss module as shown below:

```scss
$custom-theme-colors: (
    "altlight": #f2ebfa,
    "altdark": #522192
);

$theme-colors: map-merge($custom-theme-colors, $theme-colors);

// import bootstrap
@import '../node_modules/bootstrap/scss/bootstrap';

// Loop to add new background colors
@each $key,$val in $custom-theme-colors {
    .bg-#{$key}{
        background-color: $val;
    }
    .text-#{$key}{
        color: $val;
    }
}

```
The above fix was contributed by [丹尼Danny](https://www.youtube.com/channel/UCvfC0WyqxuGPoLcOtBZfgJw) in the comments to the corresponding YouTube video for this lesson, https://www.youtube.com/watch?v=nCX3QVl_PiI&list=PL4cUxeGkcC9joIM91nLzd_qaH_AimmdAR&index=19.

