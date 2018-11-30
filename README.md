# Coqtail
## Interactive Coq Proofs in Vim

Coqtail is a rewrite of
[Coquille](https://github.com/the-lambda-church/coquille).
The main improvements are:
- Better support for editing multiple files simultaneously
- Support for both Python 2 and 3.
- Support for Coq 8.4 - 8.8

Installation and Requirements
-----------------------------
Coqtail can be installed using
[pathogen](https://github.com/tpope/vim-pathogen).
Follow the setup instructions and then:

    cd ~/.vim/bundle && git clone https://github.com/whonore/Coqtail.git

Coqtail requires:
- vim compiled with either +python or +python3
- [vimbufsync](https://github.com/let-def/vimbufsync)
- [Coq 8.4](https://coq.inria.fr/coq-84),
  [8.5](https://coq.inria.fr/coq-85),
  [8.6](https://coq.inria.fr/coq-86),
  [8.7](https://coq.inria.fr/coq-87), or
  [8.8](https://github.com/coq/coq/releases/tag/V8.8.1)

If you are using pathogen, documentation can be generated by
`:call pathogen#helptags()`. Alternatively, you can do `:helptags
{path-to-coqtail}/doc`.

Usage
-----
Coqtail provides the following commands (see `:help coqtail` for more detail)
- CoqStart (`<leader>cc`) - Launches Coq
- CoqStop (`<leader>cq`) - Quits Coq
- CoqNext (`<leader>cj`) - Submits the next line to Coq for checking
- CoqUndo (`<leader>ck`) - Steps back
- CoqToCursor (`<leader>cl`) - Submits all lines up to the cursor
- CoqToTop (`<leader>cT`) - Resets the checked part to the beginning of the
  file
- Coq \<arg> - Sends arbitrary commands to Coq (such as Check, About, Print,
  etc)
  + \<arg>=SearchAbout (`<leader>cs`) - Search for theorems about the Coq term
    under the cursor
  + \<arg>=Check (`<leader>ch`) - Check the type of the Coq term under the
    cursor
  + \<arg>=About (`<leader>ca`) - Print information about the Coq term under
    the cursor
  + \<arg>=Print (`<leader>cp`) - Print the definition of the Coq term under
    the cursor
  + \<arg>=Locate (`<leader>cf`) - Find where the Coq term under the cursor was
    defined
- JumpToEnd (`<leader>cG`) - Moves the cursor to the end of the checked region
- FindDef (`<leader>co`) - Searches the LoadPath for the definition of the Coq
  term under the cursor and opens it in another file if possible
- MakeMatch (`<leader>cm`) - Insert a 'match' template for a given Inductive
  type at the cursor location
- ToggleDebug (`<leader>cd`) - Toggle logging of debug messages to a file (off
  by default)

The mappings shown above are set by default by `coqtail#Mapping()`, but you can
disable these and define your own by setting `g:coqtail_nomap = 1` in your
.vimrc.

Coqtail also comes with an ftdetect script for Coq, as well as modified
versions of Vincent Aravantinos'
[syntax](http://www.vim.org/scripts/script.php?script_id=2063) and
[index](http://www.vim.org/scripts/script.php?script_id=2079) scripts for Coq.
These scripts are used by default but can be disabled by setting
`g:coqtail_nosyntax = 1` and `g:coqtail_noindent = 1` respectively.
