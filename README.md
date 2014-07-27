make-iop-author-list
====================

Generates `LaTeX` code for an IOP publication author list (e.g. for
ApJ, AJ, etc.).

I wrote this barebones script to automate the annoyance of IOP's
`iopart.cls` lacking proper `\affiliation` and `\author` handling.

`iopart.cls` requires you to manually "footnote" your author listing,
determine the affiliation order by hand, etc. This is a nightmare for
a paper with a large number of authors and many institutions, having
authors with multiple institutions where some overlap.
`make-iop-author-list` is supposed to automate the process.

The script accepts two plain text files and emits `LaTeX` source on
stdout. The first plain text file (say `authors.txt`) contains the
ordered author list with keywords for each author's institutional
affiliations. The second plain text file (say `affils.txt`) is map of
affiliation-keys to their addresses.

`authors.txt` has the following format: one author per line, each line
consists of:

```latex
Author's~name~in~LaTeX~with~no~withspace[arbitrary amount of whitespace]comma,delimited,affiliation,keyword,list
```

`affils.txt` has the following format: one affiliation per line, each
line consists of:

```latex
keyword[arbitrary amount of whitespace]Affiliation name and address, as LaTeX code, any characters you want
```

The directory [example/](example/) is just that. This example shows:
* Where whitespace does and doesn't go
* Where `LaTeX` code goes
* The affiliation list order determined from the author list
* Multiple affiliations per author keep their order
* [Makefile](example/Makefile) usage is encouraged and the rule is very simple

I haven't put in any error checking or other niceties. Feel free to
fork and send me a pull request if you want to improve the code! :)
