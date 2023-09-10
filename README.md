# pancake.sh
... uses pandoc to render html files from markdown. I choose pandoc because I wanted to keep the toolchain simple and because it can render citations from a bibtex file, which is pretty awesome.

## What does it do
The provided scripts recursively renders a folder with its subfolders and markdown files to the same structure into the given folder. It then syncs the given files or assets folder and last but not least, resizes the images in the output folder. It's kind of a static site generator realised with pandoc.

The `bake` command takes all the markdown files, and generates an html website from it. It then continues to add the generated files to a specific branch of the git repository which was the input directory.

## Setup
- have pandoc as well as pandoc-citeproc installed - `sudo apt install pandoc pandoc-citeproc` on something debian/ubuntu based
- have a repository with two branches, one with the markdown files, and one which will hold the html files
- have a `.bake` file present in said repository
- render your markdown archive into a html website, and deploy it, through this command `./bake ../test-repository`

There is an `example-repository` for you to look at.

### Structure of a `.bake` file
```
MAIN_BRANCH: main
DEPLOY_BRANCH: pages
TEMPLATE_DIR: assets
DEFAULT_TEMPLATE: default
BIBTEX_FILE: assets/bibfile.bib
OPTIMIZE_IMAGES: true
DITHER_COLORS: 8
RESIZE_DIMENSIONS: 1280
BLOG_RSS: true
BLOG_PATH: journal
BLOG_TITLE: Hello World
BLOG_DESCRIPTION: Best Blog Ever
BLOG_URL: "https://test-repository.net"
```
Do not rename the variables, please.

- `MAIN_BRANCH` holds the markdown files
- `DEPLOY_BRANCH` will hold the html files
- `TEMPLATE_DIR`: where the template files lie
- `DEFAULT_TEMPLATE`: the default template; I will add the possibility to change template via frontmatter; `.html` is added
- `BIBTEX_FILE`: where the bibtex file is
- `OPTIMIZE_IMAGES`: true/false; if you want to optimize your images. Optimization is done via dithering and resizing
- `DITHER_COLORS`: the amount of colors an image should be reduced to
- `RESIZE_DIMENSIONS`: the max width and height an image can have
- `BLOG_RSS`: true/false; if you want to generate an rss feed.xml
- `BLOG_PATH`: path to where the blog posts lie
- `BLOG_TITLE`: …
- `BLOG_DESCRIPTION`: …
- `BLOG_URL`: …

## License
Released and distributed under the [Anti-Capitalist Attribution Cooperative License](https://noroadhome.itch.io/acaclicense).
