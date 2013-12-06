## Module manifests has to comply with this style guide

### Must use two-space soft tabs
### Must not use literal tab characters
### Must not contain trailing white space
### Should not exceed an 80 character line width
### Should align fat comma arrows (=>) within blocks of attributes
 

#### In order to facilitate this, I put together a guide to install some vim tools



apt-get remove vim-puppet
apt-get install git

mkdir -p ~/.vim/autoload ~/.vim/bundle; \
curl -so ~/.vim/autoload/pathogen.vim https://raw.github.com/tpope/vim-pathogen/master/autoload/pathogen.vim

cd ~/.vim/bundle
git clone https://github.com/scrooloose/syntastic.git

download Tabular (.tar.gz)
https://github.com/godlygeek/tabular
and unpack it inside .vim/bundle

download vim-puppet (.tar.gz)
https://github.com/rodjek/vim-puppet
and unpack it inside .vim/bundle

--- 

### add to .vimrc

set nocompatible " We're running Vim, not Vi!
syntax on " Enable syntax highlighting
filetype plugin indent on " Enable filetype-specific indenting and plugins

" Load matchit (% to bounce from do to end, etc.)
runtime macros/matchit.vim

augroup myfiletypes
" Clear old autocmds in group
autocmd!
" autoindent with two spaces, always expand tabs
autocmd FileType ruby,eruby,yaml set ai sw=2 sts=2 et
"autocmd FileType puppet set ai sw=2 sts=2 et
augroup END

call pathogen#infect()
call pathogen#helptags()

---


This will let you have a set of commands:

=                                        automatic indentation

:Tabularize /=?        automatic aligment of the '=>' signs

 

also when you will ':w' the file, syntax will be checked with Syntastic, and you will be able to spot straight away coding errors.


