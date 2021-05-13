# latex-tricks

Collection of useful commands with LaTeX.



## Installing and using latexdiff to see the pdf revisions

`latexdiff` is a very useful LaTeX tool that allows to visualize automatically the revisions (deletions, additions) between two versions of a `.tex` document. This is very useful when sharing copies of a manuscript with collaborators and reviewers to highlight the changes at resubmission to a scientific journal for example, similarly to what is done at the proofs stage before publication.

### Using latexdiff with Overleaf
At the moment, as far as I am aware, Latexdiff is not integrated in the online editor Overleaf, where some information on [its installation](https://es.overleaf.com/learn/latex/Articles/Using_Latexdiff_For_Marking_Changes_To_Tex_Documents) are given. However, the History options in Overleaf allow one to label different versions of a project ad different times, and download the full zipped folder. In this way one can use latexdiff on the different versions. 

### Using latexdiff online
You can copy-paste the two drafts, say `main_v1.tex` and `main_v2.tex` into the online forms at https://3142.nl/latex-diff/ and then copy the generated output back into Overleaf, compiling again the new `diff_v1_v2.tex` document, or locally on your computer. This however does not work too well with nested `.tex` files. 

### Using latexdiff locally
You may already have `latexdiff` installed by your LaTeX distribution. Check it from terminal with
```
latexdiff
```

#### Installing Perl
Information on installation are given [here](https://es.overleaf.com/learn/latex/Articles/Using_Latexdiff_For_Marking_Changes_To_Tex_Documents). To use Latexdiff you need Perl. 

For Mac, an easy path is to copy the source code from the [Perl5](https://github.com/Perl/perl5) repository from your terminal with `git`  

```
  git clone https://github.com/Perl/perl5.git perl

```
Go to the `perl` folder that will have been created and from there type
```
  ./Configure -des -Dprefix=$HOME/localperl
  make install

```
Alternatively, if you want to be extra careful about the installation, you can first run the tests, which though may take several minutes to run, with 
```
  ./Configure -des -Dprefix=$HOME/localperl
  make tests
  make install
```

You can then download `latexdiff` from [CTAN](https://ctan.org/tex-archive/support/latexdiff).

#### Using latexdiff on multiple files

If you have two folders with multiple nested files included in the main files, you can use the `--flatten` option to obtain a single `diff.tex` output. 
For example
```
latexdiff v2/main.tex v1/main.tex --flatten > diff.tex
```
will produce the desired output. 

In order to check the changes also on the bibliograpy, if you are using a `.bib` file for example, make sure to run the two `main.tex` files compiling the Bibtex to generate the `.bbl` file first.  

