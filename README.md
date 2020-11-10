# Vim Cheat Sheat
https://vim.rtorr.com/

# How to customize vim

Settings are done on Mac OSX 10.14.6

It's all from here: https://www.linode.com/docs/guides/introduction-to-vim-customization/ and copied for savety reasons

## Install vim
* check if vim is already installed: `which vim`
* if not then install: `brew install vim`

## Customize vim
### /usr/share/vim/vimrc
add to `/usr/share/vim/vimrc`:
```
set showcmd› › " Show (partial) command in status line.
set showmatch› › " Show matching brackets.
set ignorecase›› " Do case insensitive matching
set smartcase› › " Do smart case matching
set incsearch› › " Incremental search
set autowrite› › " Automatically save before commands like :next and :make
set hidden›› " Hide buffers when they are abandoned
set mouse=a› › " Enable mouse usage (all modes)
```
### ~/.vimrc
add to `~/.vimrc`
```
" Set compatibility to Vim only.
set nocompatible

" Helps force plug-ins to load correctly when it is turned back on below.
filetype off

" Turn on syntax highlighting.
syntax on

" For plug-ins to load correctly.
filetype plugin indent on

" Turn off modelines
set modelines=0

" Automatically wrap text that extends beyond the screen length.
set wrap
" Vim's auto indentation feature does not work properly with text copied from outside of Vim. Press the <F2> key to toggle paste mode on/off.
nnoremap <F2> :set invpaste paste?<CR>
imap <F2> <C-O>:set invpaste paste?<CR>
set pastetoggle=<F2>

" Uncomment below to set the max textwidth. Use a value corresponding to the width of your screen.
" set textwidth=79
set formatoptions=tcqrn1
set tabstop=2
set shiftwidth=2
set softtabstop=2
set expandtab
set noshiftround

" Display 5 lines above/below the cursor when scrolling with a mouse.
set scrolloff=5
" Fixes common backspace problems
set backspace=indent,eol,start

" Speed up scrolling in Vim
set ttyfast

" Status bar
set laststatus=2

" Display options
set showmode
set showcmd

" Highlight matching pairs of brackets. Use the '%' character to jump between them.
set matchpairs+=<:>

" Display different types of white spaces.
set list
set listchars=tab:›\ ,trail:•,extends:#,nbsp:.

" Show line numbers
set number

" Set status line display
set statusline=%F%m%r%h%w\ [FORMAT=%{&ff}]\ [TYPE=%Y]\ [POS=%l,%v][%p%%]\ [BUFFER=%n]\ %{strftime('%c')}

" Encoding
set encoding=utf-8

" Highlight matching search patterns
set hlsearch
" Enable incremental search
set incsearch
" Include matching uppercase words with lowercase search term
set ignorecase
" Include only uppercase words with uppercase search term
set smartcase

" Store info from no more than 100 files at a time, 9999 lines of text, 100kb of data. Useful for copying large amounts of data between files.
set viminfo='100,<9999,s100

" Map the <Space> key to toggle a selected fold opened/closed.
nnoremap <silent> <Space> @=(foldlevel('.')?'za':"\<Space>")<CR>
vnoremap <Space> zf

" Automatically save and load folds
autocmd BufWinLeave *.* mkview
autocmd BufWinEnter *.* silent loadview"
```
### install Plugin-Manager
run: `curl -fLo ~/.vim/autoload/plug.vim --create-dirs https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim`
create file and folder:
```
touch ~/.vimrc.plug
mkdir ~/vimplug-plugins
```
add to `~/.vimrc':
```
" Call the .vimrc.plug file
 if filereadable(expand("~/.vimrc.plug"))
     source ~/.vimrc.plug
 endif
```
add to `~/.vimrc.plug`:
```
call plug#begin('~/.vim/plugged')

"Fugitive Vim Github Wrapper
Plug 'tpope/vim-fugitive'

call plug#end()
```

open vim and run: `:PlugInstall`

### more Plugins:
add to `~/.vimrc.plug`:
```
Plug 'mhinz/vim-startify'
Plug 'preservim/nerdtree'
```

## more useful plugins
https://medium.com/@huntie/10-essential-vim-plugins-for-2018-39957190b7a9

https://blog.codota.com/top-15-vim-plugins-100-free/
