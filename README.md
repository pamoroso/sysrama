# Sysrama

Sysrama is an [Interlisp](https://interlisp.org) documentation tool for presenting information on the Lisp objects of a program. It produces reports listing the types and signatures of functions, the fields of records, global variables, property lists, Exec commands, and more. The tool can also represent and visualize programs as NoteCards hypertexts.

Sysrama lets you see the big picture of a system, a panorama. Hence the name.

![Sample output of the Sysrama Interlisp documentation tool.](https://raw.githubusercontent.com/pamoroso/sysrama/main/sysrama.png)


## Installation

Download the file `SYSRAMA` from the project repo, copy it to a file system location your Medley Interlisp installation has access to, and optionally compile the source by evaluating the following expression at the Lisp Executive:

```
(TCOMPL 'SYSRAMA)
```

Provide these answers to the questions the compiler asks:

* listing? no
* redefine? yes
* save exprs? no

Finally, load Sysrama by evaluating:

```lisp
(FILESLOAD SYSRAMA)
```

The hypertext features require NoteCards, so make sure it is loaded too.


## Usage

Suppose you want to analyze the Lisp program `MYPROG`, which must be under File Manager control. First load `MYPROG`:

```lisp
(LOAD 'MYPROG)
```

To have Sysrama print a report with information on `MYPROG` evaluate:

```lisp
(SUMMARIZE 'MYPROG)
```

You can narrow down the information to specific File Manager types such as `FNS` and `RECORDS`:

```lisp
(SUMMARIZE 'MYPROG '(FNS RECORDS))
```

or to specific objects such as the function `MYFUN`:

```lisp
(SUMMARIZE 'MYPROG 'FNS 'MYFUN)
```


### Reference

The entry point to Sysrama is this function:

`(CODECARDS FILE)` [function]: creates a NoteCards notefile that represents as a hypertext the Lisp program in the symbolic `FILE`. The function makes one filebox per File Manager type, containing one card per Lisp object of the type. The fileboxes are filed under the Table of Contents. `CODECARDS` returns the filebox.

`(SUMMARIZE FILE TYPE NAME)` [function]: prints a report describing the Lisp objects in symbolic `FILE`. The report goes to the primary output and contains information only for the File Manager type designated by the `TYPE` argument if a symbol, a list of types if the argument is as such, or all registered types if `NIL`. Prints the information only for the symbol or list of symbols `NAME` if not `NIL`.


## Release history

See the [list of releases](https://github.com/pamoroso/sysrama/releases) for notes on the changes in each version.


## Learn more

- [Sysrama project updates](https://journal.paoloamoroso.com/tag:sysrama)
- [Medley Interlisp](https://interlisp.org)


## Author

Sysrama is developed by [Paolo Amoroso](https://github.com/pamoroso).


## License

This code is distributed under the MIT license, see the `LICENSE` file.
