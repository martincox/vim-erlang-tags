vimtags-erlang
==============

`vimtags-erlang` **creates a tags file** (from Erlang source files), which can
be used by Vim.

When using Exuberant ctags or etags, the genereted tags will contain function
names, but there will be no `module:function` tags. This is a problem
because if several functions (in different modules) have the same name, the
text editor will not know which one to jump to.

The idea of this script is to generate `module:function` tags too. This way the
code will be **easier to navigate than with ctags or etags**. The original idea
is from László Lövei.

Since `:` is not a keyword character when editing Erlang files in Vim, this
repository also contains a Vim plugin, which modifies the following normal mode
commands to add `:` to the `iskeyword` option for Erlang files while they are
jumping to the location of the tag that is under the cursor:

    CTRL-]
    g<LeftMouse>
    <C-LeftMouse>
    g]
    g CTRL-]

Installation
------------

- Clone this repository.
- Make sure the `bin/vimtags-erlang` is executable and add it to the `PATH`.
- Add the following line to your `.vimrc` (replace the path with your own):

        :set runtimepath^=/path/to/vimtags-erlang

Usage
-----

Let's say you would like to use tags for your Erlang project.

Generate the tags (you have to do this periodically to keep the tags file
up-to-date):

    $ cd /path/to/my_erlang_project
    $ vimtags-erlang

Add the following line to your `.vimrc` (this add the tags file to the list of
known tags files):

    :set tags^=/path/to/my_erlang_project/tags

Reopen Vim or just execute `:source $MYVIMRC` – now all your function names,
records, macros and file names are available with the Vim tag commands. For
more information on those commands, see `:help tagsrch.txt`.