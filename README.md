# vimcmdline: Send lines to interpreter

This plugin sends lines from either [Vim] or [Neovim] to a command line
interpreter. Supported file types are haskell, julia, lisp, matlab, prolog,
python, ruby and sh. The interpreter may run in a Tmux pane or in a Neovim
built-in terminal. The main advantage of running the interpreter in a Neovim
terminal is that the output is colorized, as in the screenshot below:

![nvim_running_octave](https://cloud.githubusercontent.com/assets/891655/7090493/5fba2426-df71-11e4-8eb8-f17668d9361a.png)

## How to install

Copy the directories *ftplugin*, *plugin* and *syntax* and their files to your
*~/.vim* or *~/.config/nvim* directory, or use a plugin manager like
[Vim-Plug], [Vundle], [Pathogen], [Neobundle], or other.

## Usage

If you are editing one of the supported file types, in Normal mode do:

  - `<LocalLeader>s` to start the interpreter.

  - `<Space>` to send the current line to the interpreter.

  - `<LocalLeader>q` to send the quit command to the interpreter.

For languages that can source chunks of code:

  - In Visual mode, press:

    - `<Space>` to send a selection of text to the interpreter.

  - And, in Normal mode, press:

    - `<LocalLeader>p` to send from the line to the end of paragraph.

    - `<LocalLeader>b` to send block of code between two closest marks.

    - `<LocalLeader>f` to send the entire file to the interpreter.

These mappings can be customized in the following way:

```vim
let g:cmdline_send_line_mapping = '<space>'
let g:cmdline_visual_send_line_mapping = '<space>'
let g:cmdline_send_file_mapping = '<LocalLeader>f'
let g:cmdline_send_paragraph_mapping = '<LocalLeader>p'
let g:cmdline_send_marked_block_mapping = '<LocalLeader>b'
let g:cmdline_quit_mapping = '<LocalLeader>q'
```


## Options

Below are examples of how to set the options in your *vimrc*:

```vim
let cmdline_vsplit = 1        " Split the window vertically
let cmdline_esc_term = 1      " Remap <Esc> to :stopinsert in Neovim terminal
let cmdline_in_buffer = 0     " Start the interpreter in a Neovim buffer
let cmdline_term_height = 15  " Initial height of interpreter window or pane
let cmdline_term_width = 80   " Initial width of interpreter window or pane
let cmdline_tmp_dir = '/tmp'  " Temporary directory to save files
let cmdline_outhl = 1         " Syntax highlight the output
```

If you are using Neovim, you can use its syntax highlight capabilities to
colorize the interpreter output, and you can customize the colors in your
*vimrc*. The example of customization below is for a terminal emulator that
supports 256 colors (see in Neovim `:h highlight-ctermfg`):

```vim
if &t_Co == 256
    let cmdline_color_input = 247
    let cmdline_color_normal = 39
    let cmdline_color_number = 51
    let cmdline_color_integer = 51
    let cmdline_color_float = 51
    let cmdline_color_complex = 51
    let cmdline_color_negnum = 183
    let cmdline_color_negfloat = 183
    let cmdline_color_date = 43
    let cmdline_color_true = 78
    let cmdline_color_false = 203
    let cmdline_color_inf = 39
    let cmdline_color_constant = 75
    let cmdline_color_string = 79
    let cmdline_color_stderr = 33
    let cmdline_color_error = 15
    let cmdline_color_warn = 1
    let cmdline_color_index = 186
endif
```

If you prefer that the output is highlighted using you current `colorscheme`,
put in your *vimrc*:

```vim
let cmdline_follow_colorscheme = 1
```

[Vim]: http://www.vim.org
[Neovim]: https://github.com/neovim/neovim
[Vundle]: https://github.com/gmarik/Vundle.vim
[Pathogen]: https://github.com/tpope/vim-pathogen
[Vim-Plug]: https://github.com/junegunn/vim-plug
[Neobundle]: https://github.com/Shougo/neobundle.vim
