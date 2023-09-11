# pancake.sh
... uses pandoc to create a website from a markdown based note-archive. I choose pandoc because I wanted to keep the toolchain simple and because it can render citations from a bibtex file, which is pretty awesome.

Besides pandoc and git, the scrip uses commonly available command line tools: `eval`, `sed`, `awk`, `grep`, `rsync`, `find`, and some filesystem commands. I might want to clean up the scripts once and make them more modular.

## What does it do
The provided scripts recursively renders a folder with its subfolders and markdown files to the same structure into the given folder. It then syncs the given files or assets folder and last but not least, resizes the images in the output folder. It's kind of a static site generator realised with pandoc.

The `bake` command takes all the markdown files, and generates an html website from it. It then continues to add the generated files to a specific branch of the git repository which was the input directory.

## Setup
- have pandoc, pandoc-citeproc and git installed - `sudo apt install pandoc pandoc-citeproc git` on something debian/ubuntu based
- have a repository with two branches, one with the markdown files, and one which will hold the html files
- have a `.bake` file present in said repository
- your markdown archive needs to use the proper markdown link format, as in `[Link Text](https://link.url)`. pancake doesn't work with Wikilinks
- render your markdown archive into a html website, and deploy it, through the `bake` command and adding the path to the repository as parameter: `./bake ../test-repository`

There is an `example-repository` for you to look at.

### Structure of a `.bake` file
```yaml
BRANCHES:
  MAIN: main
  DEPLOY: pages
FILES:
  TEMPLATES: assets
  DEFAULT_TEMPLATE: default
  BIBTEX: assets/bibfile.bib
IMAGES:
  OPTIMIZE: true
  COLORS: 6
  DIMENSIONS: 960
BLOG:
  RSS: true
  PATH: journal
  TITLE: Hello World
  DESCRIPTION: Best Blog Ever
  URL: "https://thgie.ch"
```
Do not rename the variables, please.

- `BRANCHES_MAIN` holds the markdown files
- `BRANCHES_PAGES` will hold the html files
- `FILES_TEMPLATES`: where the template files lie
- `FILES_DEFAULT_TEMPLATE`: the default template; you can change template via frontmatter; `.html` is added
- `FILES_BIBTEX`: where the bibtex file is
- `IMAGES_OPTIMIZE`: true/false; if you want to optimize your images. Optimization is done via dithering and resizing
- `IMAGES_COLORS`: the amount of colors an image should be reduced to
- `IMAGES_DIMENSIONS`: the max width and height an image can have
- `BLOG_RSS`: true/false; if you want to generate an rss feed.xml
- `BLOG_PATH`: path to where the blog posts lie
- `BLOG_TITLE`: …
- `BLOG_DESCRIPTION`: …
- `BLOG_URL`: …

## License
Released and distributed under the [Anti-Capitalist Attribution Cooperative License](https://noroadhome.itch.io/acaclicense).
