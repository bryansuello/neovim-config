# neovim-config

:PlugStatus  -check status of plugins
:PlugInstall  -install plugins
:PlugUpdate  -update plugins
:PlugDiff -after update press d to see the differences or run
:PlugClean  -To remove plugins that are no longer defined in the plugins.vim file
:PlugUpgrade -uprade vim-plug itself

~~~
### HOW THIS WORKED:

Make directory for your Neovim config
mkdir ~/.config/nvim

Create an init.vim file
touch ~/.config/nvim/init.vim

INSTALL vim-plug
curl -fLo ~/.config/nvim/autoload/plug.vim --create-dirs https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim
*should now have the plug.vim in autoload directory so it will load of on start.


ADD A NEW FILE FOR PLUGINS
We will manage our plugins in a separate file for the sake of my own sanity
mkdir ~/.config/nvim/vim-plug
touch ~/.config/nvim/vim-plug/plugins.vim


ADD THE PLUGINS:
Add the following to ~/.config/nvim/vim-plug/plugins.vim
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

SOURCE YOUR PLUGINS
Add the following line to init.vim
source $HOME/.config/nvim/vim-plug/plugins.vim

~~~
