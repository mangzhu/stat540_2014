STAT 540 Homework Submission Instructions
========================================================

## GitHub set-up

  - Register an [educational GitHub account](https://education.github.com); it has the added perk of giving you some free private repositories for a couple of years. You probably want a *student, individual* account.
  - Optional: Upload your photo to [Gravatar](http://gravatar.com), if you're comfortable with that. This photo will appear in your GitHub profile, be associated with your commits and comments, etc.
  - Create a __public__ GitHub repository named `stat540-2014-lastname-firstname` for lab work
  - Create a __private__ GitHub repository named `stat540-2014-lastname-firstname-hw` for assignments
  - Add the profs and TAs as collaborators to your __private__ GitHub repository
    - [Jenny Bryan -- jennybc](https://github.com/jennybc) on GitHub
    - [Shaun Jackman -- sjackman](https://github.com/sjackman) on GitHub
    - [Gloria Li -- gloriali](https://github.com/gloriali) on GitHub
    
## Set-up your private GitHub repo for homework

  * We're talking about the repo `stat540-2014-lastname-firstname-hw` now.
  * Make a top-level directory for each assignment, e.g. `hw01` and `hw02`
    - We truly mean a [directory or "folder"](http://en.wikipedia.org/wiki/Directory_(computing)) -- NOT a [Git branch](http://git-scm.com/book/en/Git-Branching) or anything fancy like that! On your local computer, go to the directory where this Git repository lives. Make the 2 directories here. FYI, since Git tracks *files*, you might not see evidence of the `hw02` directory on, e.g. GitHub, until there are some files in it.
  * Make a top-level `README.md` that includes, at the very least, something like "This is Jenny Bryan's private repository for STAT540 homework."
    - GitHub automatically renders all Markdown files into (pseudo-)HTML when you visit them in a browser. Whenever a *directory* in a repo is visited, if it contains a Markdown file called `README.md`, it will automatically be rendered, effectively serving as a landing or home page.
  * It is also nice to include a `README.md` inside each of the assignment directories, for all the same reasons. See below.

## R Markdown

  - Write your homework in R Markdown. The file extension should be `.rmd`.
  - Recommendation: Create a skeleton of your report by starting with the Markdown file that creates the assignment itself! You can take some things away (unnecessary detail) and add others (R chunks) to morph this into your homework solution.
    - [Source for 2014 homework assignment 1](https://github.com/jennybc/stat540_2014/blob/master/homework/hw01/hw01_quality-exploration-DE.md)
    - [Source for 2014 homework assignment 2](https://github.com/jennybc/stat540_2014/blob/master/homework/hw02/hw02_array-rna-seq-dea.md)
    - You'll have these files if you are using Git(Hub) to keep a current copy of the whole course repository. Or, from the links above, click on "Raw" to get raw Markdown and save to a local file.
    
## HTML

  * Compile your homework to Markdown (file extension should be `.md`) and then to HTML (file extension should be `.html`).
    - RStudio's "Knit HTML" button will do this
    - Alternatively, use `knit2html()` from the `knitr` package in the R Console or in an R script.
    - To run from the shell or in a Makefile, use something like `Rscript -e "knitr::knit2html('hw01_bryan-jenny.rmd')"`
  * Notice that, by default, any figures created are placed into a `figures/` subdirectory. The intermediate Markdown file links to these and, therefore, requires them to present your full report. By default, the figures are base64 encoded and *embedded* into the HTML, which, therefore, is self-contained.

## What to put (or not put) into your Git(Hub) repository

> This is rather specific to STAT 540 and may not necessarily reflect your workflow in the future and in other contexts.

  * Commit the main R markdown (`.rmd`) file that constitutes your solution. Commit early, commit often!
  * Do not commit the input data to your repository.
    - Locally, you are of course encouraged to keep the file in some logical place within the homework assignment's directory. But list the names of such data files in your top-level [`.gitignore` file](http://git-scm.com/docs/gitignore), so that Git ignores it. We do this so that TAs don't end up with 50 copies of the input data when they mark your work.
  * Commit the intermediate Markdown (`.md`) file and the figures stored in the `figures/` subdirectory.
    - Some purists would say intermediate and downstream products do NOT belong in the repo. After all, you can always recreate them from source, right? But here in reality, it turns out to be incredibly handy to have this in the repo.
  * Commit the end product HTML (`.html`) file.
    - See above comment re: version control purists vs. pragmatists.
  * You may not want to commit the Markdown and HTML until the work is fairly advanced, maybe even until submission. Once these enter the repo, you really should recompile them each time you commit changes to the R Markdown source, so that the Git history reflects the way these files should evolve as an ensemble.
  * __Never ever__ edit the Markdown or HTML "by hand". Only edit the R Markdown source and then regenerate the downstream products from that.

## How to "turn in" your homework

  * Make sure you have committed all the files associated with your solution in your local Git repository.
  * Make sure you have pushed the current state of your local repo to GitHub.
  * Open your private GitHub repository in a web browser
  * On the web page just above the files, look for the text "latest commit" followed by ten numbers and letters (called the revision SHA) and a clipboard icon
  * Click on the clipboard icon to copy the revision SHA to your clipboard
  * Create an issue in your private repository. Click on "Issues", then on "New Issue". Name the issue "Mark homework x of *firstname* *lastname*", where *x* is, e.g. 1 or 2.
  * In the description of the issue, tag both TAs by including text like `@gloriali and @sjackman`, and paste the revision SHA.
   * Click "Submit new issue". You're done! Congratulations!

> If you're concerned that something hasn't gone right with the submission, send Gloria glorialuolanli@gmail.com and Shaun sjackman@gmail.com an e-mail with your assignment attached. **Note**: this is only an emergency back-up plan. We will pester and work with you until you eventually get it submitted via GitHub.
  
## Polish your work

At this point, you have technically completed this assignment. But here are some minor tweaks that can make a big difference in how awesome your product is.

### Make it easy for people to access your work

Reduce the friction for TAs and profs to get the hard-working source code (the R markdown) __and__ the front-facing report (HTML).

  * Create a `README.md` in the homework's subdirectory to serve as the landing page for your submission. Whenever anyone visits this subdirectory of your repo, this will be automatically rendered nicely! In particular, hyperlinks will work.
  * With this `README.md` file, create annotated links to the documents TAs and profs will need to access. Such as:
    - Your main R markdown document.
    - The intermediate Markdown product that comes from knitting your main R markdown document. Remember GitHub will render this into pseudo-HTML automagically. Remember the figures in `figures/` need to be available in the repo in order appear here.
    - The final pretty HTML report. Read instructions below on how access the pretty, not the ugly source.
    
> You could link to an HTML report on RPubs, but a GitHub-only solution is preferred. RPubs isn't really necessary once your work is hosted on GitHub.Plus it's kinda nice to keep this private.

If you want to see an example of a `README.md` that links to and explains a bunch of files in the same repo + subdirectory, you can look at these examples from STAT 545A: [example 1](https://github.com/jennybc/STAT545A/tree/master/hw06_scaffolds/01_justR), [example 2](https://github.com/jennybc/STAT545A/tree/master/hw06_scaffolds/02_rAndMake), [example 3](https://github.com/jennybc/STAT545A/tree/master/hw06_scaffolds/03_knitWithoutRStudio).

### Linking to HTML files in the repo

Simply visiting an HTML file in a GitHub repo just shows ugly HTML source. You need to do a little extra work to see this rendered as a proper webpage.

  * Navigate to the HTML file on GitHub. Click on "Raw" to get the raw version; the URL should look something like this: `https://raw.github.com/stat540-2014-bryan-jennifer-hw/hw01/stat540-2014-bryan-jennifer-hw01.html`. Copy that URL!
  * Create a link to that in the usual Markdown way BUT prepend `http://htmlpreview.github.io/?` to the URL. So the URL in your link should look something like this: `http://htmlpreview.github.io/?https://raw.github.com/stat540-2014-bryan-jennifer-hw/hw01/stat540-2014-bryan-jennifer-hw01.html`. You can learn more about this preview facility [here](http://htmlpreview.github.io).
  * This sort of link would be fabulous to include in `README.md`.

### Make it easy for others to run your code

  * In exactly one, very early R chunk, load any necessary packages, so your dependencies are obvious.
  * In exactly one, very early R chunk, import anything coming from an external file. This will make it easy for someone to see which data files are required, edit to reflect their locals paths if necessary, etc. There are situations where you might not keep data in the repo itself.
  * Pretend you are someone else. Clone a fresh copy of your own repo from GitHub, fire up a new RStudio session and try to knit your R markdown file. Does it "just work"? It should!
  
### Make pretty tables

There are a few occasions where, instead of just printing an object with R, you could format the info in an attractive table. Some leads:

  * Consider the `kable()` function from `knitr`. *via Rod Docking* This is fairly primitive, one step up from just printing the object.
  * [STAT 545A material on using custom CSS](http://www.stat.ubc.ca/~jenny/STAT545A/topic10_tablesCSS.html) also shows how to use the `xtable` package for making pretty HTML tables.
  