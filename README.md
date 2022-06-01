# neovim-config

## commands
~~~
:PlugStatus  -check status of plugins
:PlugInstall  -install plugins
:PlugUpdate  -update plugins
:PlugDiff -after update press d to see the differences or run
:PlugClean  -To remove plugins that are no longer defined in the plugins.vim file
:PlugUpgrade -uprade vim-plug itself
~~~
## how this works

### make directory for your Neovim config
~~~
mkdir ~/.config/nvim
~~~

### create an init.vim file
~~~
touch ~/.config/nvim/init.vim
~~~

### install vim-plug
~~~
curl -fLo ~/.config/nvim/autoload/plug.vim --create-dirs https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim
~~~
* should now have the plug.vim in autoload directory so it will load of on start

### add a new file for plugins
* manage plugins in a separate file to make them easier to find and change
~~~
mkdir ~/.config/nvim/vim-plug
touch ~/.config/nvim/vim-plug/plugins.vim
~~~

### add the plugins
* add the following to ~/.config/nvim/vim-plug/plugins.vim
~~~
" auto-install vim-plug
if empty(glob('~/.config/nvim/autoload/plug.vim'))
  silent !curl -fLo ~/.config/nvim/autoload/plug.vim --create-dirs
    \ https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim
  "autocmd VimEnter * PlugInstall
  "autocmd VimEnter * PlugInstall | source $MYVIMRC
endif

call plug#begin('~/.config/nvim/autoload/plugged')

    " Better Syntax Support
    Plug 'sheerun/vim-polyglot'
    " File Explorer
    Plug 'scrooloose/NERDTree'
    " Auto pairs for '(' '[' '{'
    Plug 'jiangmiao/auto-pairs'

call plug#end()
~~~

### source the plugins
* add the following line to init.vim
~~~
source $HOME/.config/nvim/vim-plug/plugins.vim
~~~
