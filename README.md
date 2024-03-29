"Project Management and Maintenance on Information Systems Administration" Thesis Project
===================================

A LaTeX project for my Thesis Project (using Springer theme, requested  by IST).

To increase my productivity i decided to use some tools available to help writing my thesis project report. I came to the work done by David Dias https://github.com/diasdavid/thesis-project-bootstrap.istecni.co where we presented a set of tools to speedup this ward work of writing a thesis project.

This repo is based on the work of David Dias and all the credits for discovering and presenting these tools are for him.

## Folder structure

```bash
.
├── LICENSE
├── README.md
├── refs.bib         # bibliography file
├── img                 # Here we store all our images for the report
├── llncs2e
│   ├── aliascnt.sty
│   ├── history.txt
│   ├── llncs.cls
│   ├── llncs.dem
│   ├── llncs.doc
│   ├── llncsdoc.pdf
│   ├── llncsdoc.sty
│   ├── objectives.tex
│   ├── readme.txt
│   ├── remreset.sty
│   ├── splncs.bst
│   ├── splncs03.bst
│   ├── splncs_srt.bst
│   └── sprmindx.sty
├── report.pdf          # The exported report as .pdf
├── report.tex          # The main file of the report
├── sections            # sections of the report
│   ├── 1-abstract.tex
│   ├── 2-keywords.tex
│   ├── 3-introduction.tex
│   ├── 4-objectives.tex
│   ├── 5-related-work.tex
│   ├── 6-architecture.tex
│   ├── 7-evaluation.tex
│   ├── 8-conclusions.tex
│   └── 9-appendix.tex
└── toPDF.sh            # Compiling and exporting your report to pdf, use $ sh toPDF.sh to run it 
```

## Tools

##### Mendeley 

![mendeley](http://d3fildg3jlcvty.cloudfront.net/20140120-01/graphics/commonnew/logo-mendeley.png)

Since you will have to manage dozens of papers, notes and references. You definitely don't want to do it on paper, after reading 40 papers, how the hell are you going to find quickly that one reference you are looking for. Then you start thinking, lets "be smart" and start taking notes in word, or an excell spreadsheet (I've seen all of these cases), but then you realize searching in this type of documents is hard and in the end, you still have to compile your bibliography by hand (because of the .bib format needed by LaTeX). Fear not, Mendeley is here to save you from all that pain, in the Tips section we will specify some key things you can do with Mendeley, for now, just [install](http://www.mendeley.com/) it and watch this to [sync mendely citations with latex](http://blog.mendeley.com/tipstricks/howto-use-mendeley-to-create-citations-using-latex-and-bibtex/).

##### Text Editors

There are a lot of LaTeX editors, from [TexShop](http://pages.uoregon.edu/koch/texshop/), [Latexian](http://tacosw.com/latexian/) to [Scribo](https://www.macupdate.com/app/mac/30939/scribo). We took preference on the editor that we use for programming, for its simplicity and extensibility [Sublime Text](http://www.sublimetext.com/).

##### Sublime Plug-ins
![sublime](http://upload.wikimedia.org/wikipedia/en/4/4c/Sublime_Text_Logo.png)

What I was looking in the text editor was for a good theming scheme, simply layout, powerful auto complete and well defined snippets for me. All of this was achieved by installing [latexing](http://www.latexing.com/) for Sublime.

Another cool plug-in to use is [Google Translate](https://github.com/golfadas/SublimeText-Google-Translate-Plugin). It is not available on the ST package manager, but check the github page for install instructions.
Here is how it works:
![sublime](https://imageshack.com/a/img827/4828/9m43.gif)

## Tips

##### How to Compile/Export to PDF


A scriptis available to do this automatically `toPDF.sh`, this script also has a "cleaning" function, to remove all the temporary files from your folder created by `pdflatex` compile step, so it you don't get your folder "full of things" :)

To execute it, just open your terminal and then

```bash
$ sh toPDF.sh
```

##### Citations

This is one of the key treats I like by having sublime, by typing `\cite{` sublime search in your .bib files: 
![cite gif](https://imageshack.com/a/img703/6486/3rtk.gif)


##### Change margins

Changing the margins can be a nice trick when you want to have more content you want to talk then the space you have available, you can change it by using package `geometry` with the margin option, see:

https://github.com/diasdavid/thesis-project-bootstrap.istecni.co/blob/master/report.tex#L7-L10


##### Distraction Free Mode

The web is full of distractions, writing long chunks of text can be boring sometimes, you need something to keep your focus on and don't get distracted, that is when the Distraction Free Mode of Sublime kicks in, to activate it, just press:

```
ctrl+shift+cmd+f
```

##### Snippets

By having `latexing` by your side, you have all sorts of powerful snippets! my favorites are for tables and images, to access them, just open `Sublime` Command Pallet (`cmd+shift+p`) and type `sn `, the rest defines the snipped, like so:

![snippet](https://imageshack.com/a/img69/9782/yq3.gif)

When you know the snippet text trigger, just write it and press tab. So writing `item` and then pressing `tab` will result in:

![snippet2](https://imageshack.com/a/img513/9320/ie6.gif)

## Notes/Others

##### Difference between `\input` and `\include`

As this [answer](http://tex.stackexchange.com/a/250) eloquently put's it out:

`\input{filename}` imports the commands from filename into the target file; it's equivalent to typing all the commands from filename right into the current file where the `\input` line is.

`\include{filename}` essentially does a `\clearpage` before and after `\input{filename}`, together with some magic to switch to another .aux file, and omit the inclusion at all if you have an `\includeonly` without the filename in the argument. This is primarily useful when you have a big project on a slow computer; changing one of the include targets won't force you to regenerate the outputs of all the rest

`\include` gets you the speed bonus, but it also can't be nested, can't appear in the preamble, and forces page breaks around the included text.
