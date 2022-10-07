---
subtitle:
topic: Vim
date: 2022-10-07
tags: computing
---

# Vim text editor configuration
## Setup
   1. [Install neovim](https://neovim.io/)
   2. [See how to migrate from vim/use the config file](https://neovim.io/doc/user/nvim.html#nvim-from-vim)
   3. [Install plug-in manager](https://github.com/junegunn/vim-plug) 
   4. Install plugins(see script below)
   5. [Learn how to use it efficiently](https://missing.csail.mit.edu/2020/editors/) 

## Config files
### ~/.config/nvim/init.vim

    `set runtimepath^=~/.vim runtimepath+=~/.vim/after
    let &packpath = &runtimepath
    source ~/.vimrc

    " Plugin Section
    call plug#begin("~/.vim/plugged")
        Plug 'arzg/vim-colors-xcode'
        Plug 'sheerun/vim-polyglot'
        Plug 'vim-airline/vim-airline'
        Plug 'jiangmiao/auto-pairs'
        Plug 'mg979/vim-visual-multi', {'branch': 'master'}
    call plug#end()

    " Config Section
    if (has("termguicolors"))
        set termguicolors
    endif
    colorscheme dracula`

### ~/.vimrc

    filetype plugin indent on
    syntax enable
    set autoindent
    set backspace=indent,eol,start
    set complete-=i

    set smarttab
    set tabstop=4
    set shiftwidth=4
    set expandtab
    set wrap

    set titlestring=%t
    set title

    set ttimeout
    set ttimeoutlen=100

    set incsearch
    set ignorecase
    set number
    set laststatus=2
    set ruler
    set showcmd
    set wildmenu
    set showmatch

    set history=500

    set scrolloff=1
    set sidescrolloff=5
    set display+=lastline

    set autoread
    set fileformats+=mac

    if &encoding ==# 'latin1' && has('gui_running')
    set encoding=utf-8
    endif

    if &listchars ==# 'eol:$'
    set listchars=tab:>\ ,trail:-,extends:>,precedes:<,nbsp:+
    endif
    if has('path_extra')
    setglobal tags-=./tags tags^=./tags;
    endif
    inoremap <C-U> <C-G>u<C-U>
    set mouse-=a
    command Wq wq
    command WQ wq
    command W w
    command Q q
    nnoremap Q 
    set pastetoggle=<F2>