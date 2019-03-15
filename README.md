Example keynote version control via exporting to html and tracking the text files
=================================================================================

_This repo was born from reading [this RStudio community thread](https://community.rstudio.com/t/keeping-track-of-keynote-presentations/25277/5)_

The idea is to export the keynote file to HTML using keynote itself. This generates lots of small `json` files that contain the text in the slides. It also generates PDF files with slide images. 

This repository has 4 commits, although really only 2 are necessary.

## [Commit 1](https://github.com/lcolladotor/vcontrol_keynote_test/commit/59c71191418a59f52e09e80dd8e275f32bd4ae58)


Just started a new keynote file called `presentation.key`, nothing special here.

## [Commit 2](https://github.com/lcolladotor/vcontrol_keynote_test/commit/c1f793dfa29ca6aa82097b51616072273a549289)



* I exported the keynote file `presentation.key` to HTML to the directory `presentation` (default suggested name).
* I then ignored some files that are either repetitive or not really needed for tracking changes to the presentation. That is, the `.jsonp` and `.pdfp` files. I also ignored the `assets/player` directory that contains information for making the HTML actually work. If you plan to host the HTML files (say via GitHub pages), you'll likely need those files.

```bash
echo "presentation/assets/player" >> .gitignore
echo "*.jsonp" >> .gitignore
echo "*.pdfp" >> .gitignore

git add .gitignore
git add *
```

You could either just version control everything or ignore even more files than the ones I ignored.

If you were to ignore the `.key` files, this would be the true first commit.

## [Commit 3](https://github.com/lcolladotor/vcontrol_keynote_test/commit/fbe1b6b2aa14c7be60b279634a66329c72fbe946)

I made some edits to the `presentation.key` file. As you can see in the commit diff, because `presentation.key` is a binary file there's no way to see what actually changed.

## [Commit 4](https://github.com/lcolladotor/vcontrol_keynote_test/commit/9fd2f98454f52cb89dc8fd68c15a86b0aceba745)

I re-exported the `presentation.key` file as HTML to the `presentation` directory (which overwrote it, hence why the `.gitignore` lives outside it). We can see in [commit 4](https://github.com/lcolladotor/vcontrol_keynote_test/commit/9fd2f98454f52cb89dc8fd68c15a86b0aceba745) the actual text changes in the `.json` file. Other code changed too, which add some noise, but you can still find the actual text changes. By version controlling the PDF files (one per slide), you can also visually see the difference, though for size issues you might prefer to ignore them (also, keeping them is kind of equivalent to version controlling the `.key` file to begin with). Similar to the PDF files, you can choose to ignore the `thumbnail.jpeg` files.

This would be the most strict set of commands for your `.gitignore` file:

```bash
echo "*/assets/player" >> .gitignore
echo "*.jsonp" >> .gitignore
echo "*.pdfp" >> .gitignore
echo "*.pdf" >> .gitignore
echo "*.jpeg" >> .gitignore

git add .gitignore
git add *
```

I imagine that it might be possible to write a parser for the diff on the `json` files. Though I leave that to someone else ^_^

## Commit 5

This README ^_^
