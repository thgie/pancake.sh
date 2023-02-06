# pancake.sh
... uses pandoc to render html files from markdown. I choose pandoc because I wanted to keep the toolchain simple and because it can render citations from a bibtex file, which is pretty awesome.

## What does it do
The provided scripts recursively renders a folder with its subfolders and markdown files to the same structure into the given folder. It then syncs the given files or assets folder and last but not least, resizes the images in the output folder. It's kind of a static site generator realised with pandoc.

The `deploy` command takes all the markdown files, and generates an html website from it. It then continues to add the generated files to a specific branch of the git repository which was the input directory.

## Setup
- have pandoc as well as pandoc-citeproc installed - `sudo apt install pandoc pandoc-citeproc` on something debian/ubuntu based
- render your markdown archive into a html website through this commond `./deploy -i ../thgie.ch/ -o ../thgie-output/ -t ../thgie.ch/files/template/main.html -b ../thgie.ch/files/Zettelkasten.bib`

- `-i` input directory, don't forget the trailing slash `/`
- `-o` output directory, again, there is a trailing slash `/`
- `-t` template file, which is used to frame the markdown content
- `-b` bibtext file, in case you've got citations in your markdown files
- `-u` does everything, but only with changed files since last commit, like this `-u true`

## License
Released and distributed under the [Anti-Capitalist Attribution Cooperative License](https://noroadhome.itch.io/acaclicense).
