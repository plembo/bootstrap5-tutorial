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
