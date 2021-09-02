# Notes for "Bootstrap 5 Crash Course" from Net Ninja.

## Lesson 1
Create index.html in vscode.

Type doc and then hit ```TAB``` to create boilerplate HTML 5 doc.

Copy Bootstrap CDN links to paste into index.html file:

https://getbootstrap.com/docs/5.0/getting-started/download/

Install and enable Live Server (Ritwick Dey) extension for vscode.

Open index.html with Live Server by right-clicking and choosing "Open with Live Server".

Note that font family is no longer default Times New Roman, but now Sans Serif.

Create assets folder and download files from lesson-1 branch of git repo.

My local repo already has lesson branches, so I can check out individual files from the lesson branches (make sure to change directory to the target folder).

```
$ cd assets
```

First show all the files in source folder. In the case of /assets:

```
$ git show lesson-1:assets

tree lesson-1:assets

ebook-cover.png
kindle.png
```
Then checkout each file into main's assets directory:

```
$ git checkout lesson-1 ebook-cover.png
$ git checkout lesson-1 kindle.png
```
