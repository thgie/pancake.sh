# pancake.sh
... uses pandoc to render html files from markdown. I choose pandoc because I wanted to keep the toolchain simple and because it can render citations from a bibtex file, which is pretty awesome.

## What does it do
The provided scripts recursively renders a folder with its subfolders and markdown files to the same structure into the given folder. It then syncs the given files or assets folder and last but not least, resizes the images in the output folder. It's kind of a static site generator realised with pandoc.

There are two ways to initalize a "deployment". The `deploy` script should be triggered once, initially or whenever something went wrong. It removes the output directory and renders the whole collection once.

The second trigger is a git hook, which is a script that is executed at a certain time in the git push/pull process. The post-merge hook runs when the merge after a pull has finished. Usually you just need this one. If you pull in some changes, the scripts knows what changed and renders just these files.

## Setup
- have pandoc as well as pandoc-citeproc installed - `sudo apt install pandoc pandoc-citeproc` on something debian/ubuntu based
- clone or copy pancake.sh to your markdown archive's root
- copy `post-merge` to `.git/hooks/post-merge` and make sure it's executable
- adjust `$OUTOUT_DIR`, `$BIBTEX_FILE` and `$TEMPLATE_FILE` in either or both `deploy` or `post-merge`

## License
Released and distributed under the [Anti-Capitalist Attribution Cooperative License](https://noroadhome.itch.io/acaclicense).
