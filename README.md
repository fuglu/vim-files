Installation
============

```bash
# Clone repository
cd ~
mkdir git
cd git
git clone https://github.com/fuglu/dotvim.git

# Link files
cd ~
ln -s git/dotvim/vimrc .vimrc
ln -s git/dotvim/vim .vim

# Install plugins
vim +PlugInstall

# Install some tools
sudo aptitude install exuberant-ctags gcc libxml2-utils pylint tidy
sudo gem install sass
sudo npm install -g coffeelint csslint js-yaml jshint jsonlint less
```

Plugins
=======

* [ag.vim](https://github.com/rking/ag.vim)
* [auto-pairs](https://github.com/jiangmiao/auto-pairs)
* [ctrlp.vim](https://github.com/ctrlpvim/ctrlp.vim)
* [MatchTag](https://github.com/gregsexton/MatchTag)
* [nerdcommenter](https://github.com/scrooloose/nerdcommenter)
* [nerdtree-git-plugin](https://github.com/Xuyuanp/nerdtree-git-plugin)
* [nerdtree](https://github.com/scrooloose/nerdtree)
* [supertab](https://github.com/ervandew/supertab)
* [syntastic-local-eslint.vim](https://github.com/mtscout6/syntastic-local-eslint.vim)
* [syntastic](https://github.com/scrooloose/syntastic)
* [tlib_vim](https://github.com/tomtom/tlib_vim)
* [twig-indent](https://github.com/tokutake/twig-indent)
* [vim-addon-mw-utils](https://github.com/MarcWeber/vim-addon-mw-utils)
* [vim-ansible-yaml](https://github.com/chase/vim-ansible-yaml)
* [vim-fugitive](https://github.com/tpope/vim-fugitive)
* [vim-gitgutter](https://github.com/airblade/vim-gitgutter)
* [vim-gnupg](https://github.com/jamessan/vim-gnupg)
* [vim-gutentags](https://github.com/ludovicchabant/vim-gutentags)
* [vim-javascript](https://github.com/pangloss/vim-javascript)
* [Vim-Jinja2-Syntax](https://github.com/Glench/Vim-Jinja2-Syntax)
* [vim-jsx](https://github.com/mxw/vim-jsx)
* [vim-multiple-cursors](https://github.com/terryma/vim-multiple-cursors)
* [vim-rooter](https://github.com/airblade/vim-rooter)
* [vim-snipmate](https://github.com/garbas/vim-snipmate)
* [vim-snippets](https://github.com/honza/vim-snippets)
* [vim-trailing-whitespace](https://github.com/bronson/vim-trailing-whitespace)
* [vim-twig](https://github.com/evidens/vim-twig)
* [vim-yaml](https://github.com/stephpy/vim-yaml)

vimrc
=====

```vim
" Plugins
" =======

call plug#begin()
	" Editor
	" ------
	Plug 'jiangmiao/auto-pairs'
	Plug 'gregsexton/MatchTag'
	Plug 'scrooloose/nerdcommenter'
	Plug 'ervandew/supertab'
	Plug 'scrooloose/syntastic'
	Plug 'terryma/vim-multiple-cursors'
	Plug 'garbas/vim-snipmate'
		Plug 'tomtom/tlib_vim'
		Plug 'MarcWeber/vim-addon-mw-utils'
		Plug 'honza/vim-snippets'
	Plug 'bronson/vim-trailing-whitespace'

	" Git
	" ---
	Plug 'Xuyuanp/nerdtree-git-plugin', { 'on': 'NERDTreeToggle' }
	Plug 'tpope/vim-fugitive'
	Plug 'airblade/vim-gitgutter'

	" Movement
	" --------
	Plug 'rking/ag.vim',        { 'on': 'Ag' }
	Plug 'ctrlpvim/ctrlp.vim'
	Plug 'scrooloose/nerdtree', { 'on': 'NERDTreeToggle' }
	Plug 'ludovicchabant/vim-gutentags'
	Plug 'airblade/vim-rooter'

	" Javascript
	" ----------
	Plug 'mtscout6/syntastic-local-eslint.vim', { 'for': 'javascript' }
	Plug 'pangloss/vim-javascript',             { 'for': 'javascript' }
	Plug 'mxw/vim-jsx',                         { 'for': 'javascript' }

	" GPG
	" ---
	Plug 'jamessan/vim-gnupg', { 'for': 'gpg' }

	" PHP
	" ---
	Plug 'tokutake/twig-indent',     { 'for': 'php' }
	Plug 'Glench/Vim-Jinja2-Syntax', { 'for': 'php' }
	Plug 'evidens/vim-twig',         { 'for': 'php' }

	" YAML
	" ----
	Plug 'chase/vim-ansible-yaml', { 'for': 'yaml' }
	Plug 'stephpy/vim-yaml',       { 'for': 'yaml' }
call plug#end()



" Plugin configuration
" ====================

" Ag
" --
let g:ag_prg = 'ag --vimgrep --ignore-case --skip-vcs-ignores --ignore node_modules'
let g:ag_working_path_mode = 'r'


" CtrlP
" -----
let g:ctrlp_match_window = 'top,max:20,order:ttb'
let g:ctrlp_show_hidden = 1
let g:ctrlp_working_path_mode = 'ra'


" Gutentags
" ---------
let g:gutentags_tagfile = ".tags"


" JSX
" ---
let g:jsx_ext_required = 0


" Multiple cursors
" ----------------
let g:multi_cursor_exit_from_visual_mode = 0
let g:multi_cursor_exit_from_insert_mode = 0


" NerdCommenter
" -------------
let NERDSpaceDelims = 1


" NerdTree
" --------
let g:NERDTreeDirArrows = 1
autocmd bufenter * if (winnr("$") == 1 && exists("b:NERDTree") && b:NERDTree.isTabTree()) | q | endif


" SuperTab
" --------
let g:SuperTabDefaultCompletionType = '<c-n>'


" Syntastic
" ---------
let g:syntastic_check_on_wq = 0
let g:syntastic_javascript_checkers = ['eslint']
let g:syntastic_enable_perl_checker = 1
let g:syntastic_perl_checkers = ['perl', 'perlcritic', 'podchecker']
let g:syntastic_perl_lib_path = [ './lib', './local/lib/perl5' ]



" Vim config
" ==========

set nocompatible

syntax on
set background=dark
set autowrite
set history=500
set ignorecase
set incsearch
set ruler
set scrolloff=3
set showcmd
set showmatch
set tabpagemax=100
set tags=./.tags;,./tags;
set wildmenu
set clipboard=


" Jump to the last position when reopening a file
" -----------------------------------------------
au BufReadPost * if line("'\"") > 0 && line("'\"") <= line("$")
  \| exe "normal g'\"" | endif


" Highlight tabs
" --------------
set list
set listchars=tab:»·
set listchars+=trail:·
set listchars+=extends:>
set listchars+=precedes:<


" Enable spell checking
" ---------------------
set spell
highlight clear SpellBad
highlight SpellBad term=underline cterm=underline
highlight clear SpellCap
highlight SpellCap term=underline cterm=underline
highlight clear SpellRare
highlight SpellRare term=underline cterm=underline
highlight clear SpellLocal
highlight SpellLocal term=underline cterm=underline


" Syntax highlighting for unknown file types
" ------------------------------------------
autocmd BufNewFile,BufRead *.tt setf html
autocmd BufNewFile,BufRead *.phtml setf html
autocmd BufNewFile,BufRead *.ejs setf html




" Shortcuts
" =========

" Switch to next/previous buffer with <Alt-right/left>
" ----------------------------------------------------
map  <a-right> :bn<cr>
imap <a-right> :bn<cr>
vmap <a-right> :bn<cr>
map  <a-left>  :bp<cr>
imap <a-left>  :bp<cr>
vmap <a-left>  :bp<cr>


" Step through the program with <Ctrl-j/k/l>
" ------------------------------------------
map <c-j> zz
map <c-k> :tnext<cr>
map <c-l> <C-T>


" Search with :grep or <Ctrl-f>
" -----------------------------
cabbrev grep <c-r>=(getcmdtype()==':' && getcmdpos()==1 ? 'Ag' : 'grep')<CR>
map <c-f> :Ag <cword><cr>


" Open fuzzy finder with <Ctrl-o>
" -------------------------------
let g:ctrlp_map = '<c-o>'
let g:ctrlp_cmd = 'CtrlP .'
if executable('ag')
	let g:ctrlp_user_command = 'ag %s -l --nocolor -g ""'
	let g:ctrlp_use_caching = 0
endif


" Open directory view with <Ctrl-p>
" ---------------------------------
map <c-p> :NERDTreeToggle<cr>
imap <c-p> <esc>:NERDTreeToggle<cr>


" Jump to next/previous function with <Ctrl-up/down>
" --------------------------------------------------
autocmd FileType perl           map  <c-up>   ?^sub <cr>zz
autocmd FileType perl           imap <c-up>   <esc>?^sub <cr>zz
autocmd FileType perl           map  <c-down> /^sub <cr>zz
autocmd FileType perl           imap <c-down> <esc>/^sub <cr>zz
autocmd FileType php,javascript map  <c-up>   ?function <cr>zz
autocmd FileType php,javascript imap <c-up>   <esc>?function <cr>zz
autocmd FileType php,javascript map  <c-down> /function <cr>zz
autocmd FileType php,javascript imap <c-down> <esc>/function <cr>zz
autocmd FileType python         map  <c-up>   ?^def <cr>zz
autocmd FileType python         imap <c-up>   <esc>?^def <cr>zz
autocmd FileType python         map  <c-down> /^def <cr>zz
autocmd FileType python         imap <c-down> <esc>/^def <cr>zz


" Move lines up/down with <Alt-up/down>
" -------------------------------------
nnoremap <a-up> :m .-2<CR>==
nnoremap <a-down> :m .+1<CR>==
inoremap <a-up> <Esc>:m .-2<CR>==gi
inoremap <a-down> <Esc>:m .+1<CR>==gi
vnoremap <a-up> :m '<-2<CR>gv=gv
vnoremap <a-down> :m '>+1<CR>gv=gv


" Re factor with <R/L/K>
" ----------------------
let g:multi_cursor_next_key = 'R'
let g:multi_cursor_prev_key = 'L'
let g:multi_cursor_skip_key = 'K'


" Start multiple cursors with <Ctrl-m>
" ------------------------------------
vmap <c-m> R


" Insert debug code with <Ctrl-d>
" -------------------------------
autocmd FileType c          imap <c-d> printf("%s\n", );<left><left>
autocmd FileType java       imap <c-d> System.out.println();<left><left>
autocmd FileType javascript imap <c-d> console.log();<left><left>
autocmd FileType perl       imap <c-d> print Dumper $;<left>
autocmd FileType php        imap <c-d> var_dump($);<left><left>
autocmd FileType python     imap <c-d> import sys; print >> sys.stderr,<space>


" Toggle git blame view with <Ctrl-b>
" -----------------------------------
map <c-b> :Gblame<cr>
imap <c-b> <esc>:Gblame<cr>


" Toggle git status view with <Ctrl-g>
" ------------------------------------
map <c-g> :Gstatus<cr>
imap <c-g> <esc>:Gstatus<cr>


" Fix spelling with <Ctrl-s>
" --------------------------
map <c-s> z=
imap <c-s> <esc>z=


" Write a file using sudo with :w!!
" ---------------------------------
cmap w!! w !sudo tee % >/dev/null


" Toggle paste mode with <F5>
" ---------------------------
set pastetoggle=<F5>


" Toggle comment with <F8>
" ------------------------
map <F8> <leader>c<space>
vmap <F8> <leader>c<space>
imap <F8> <esc><leader>c<space>
```

:tada:
