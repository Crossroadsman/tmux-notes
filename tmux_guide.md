Tmux
====

Anatomy of a Tmux Session
-------------------------
Tmux has 'sessions', 'windows', and 'panes'.


General Commmands
-----------------

- `<prefix> ?`: get help

Sessions
--------

### Start a new session ###

```console
$ tmux new [-s <session_name>]
```

Note the `-s` argument is optional, omit to create an unnamed session. 

Throughout tmux, depending on context, `-s` ('`s`ession') and `-t` 
('[`t`arget] client') get used to refer to the subject entity 
(session/window/etc).

### Detach from session ###

```console
$ tmux detach
```

`<prefix> d`


### List sessions ###

```console
$ tmux ls
bash: 4 windows (created Mon Feb 11 23:10:06 2019) [80x50]
tmux: 1 windows (created Tue Feb 12 14:15:01 2019) [80x50] (attached)
```

or from inside a session:
`<prefix> s`

You can use the cursors to preview and select a session.


### Attach to a session ###

```console
$ tmux a [-t <session_name>]
```

Notes:
- `a` is shorthand for `attach`
- `a` on its own without `-t <session>` will attach to the first available 
  session
- `<session_name>` is the name if a named session, number if unnamed

Attempting to attach to a session while already attached to another session
will be treated as an attempt to create a nested sessions, which by default 
tmux disallows.


### Name a session ###

`<prefix> $`


### Kill a session ###

```console
$ tmux kill-session -t <session_name>
```

Note you can also kill tmux entirely with `killall tmux`.


Windows
-------

### Create a new window ###

`<prefix> c`

or 

```console
$ tmux new-window
```

### Rename current window ###

`<prefix> ,`

or

```console
$ tmux rename-window
```

### Kill current window ###

`<prefix> &`

### Switch windows ###

- cycle next: `<prefix> n`
- cycle previous: `<prefix> p`
- toggle last selected: `<prefix> l`
- list all windows (and sessions?): `<prefix> w`
- switch to window #: `<prefix> <number>` or `tmux select-window -t :<number>`
- find window: `<prefix> f`


Panes
-----

### Split vertically ###
(i.e., turn pane into two vertically-stacked panes aka create a horizontal divider):

`<prefix ">`

(or remap to `<prefix> -`)

You can also use the command:
```console
$ tmux split-window -v [-p <n>]
```

Where `<n>` is the size of the new pane as a percentage of the pre-split pane.

### Split horizontally ###
(turn pane into two horizontal side-by-side panes aka create a vertical divider):

`<prefix> %`

(or remap to `<prefix> |`)

### Navigate to another pane ###

`<prefix> <arrow_key>`

### Cycle through panes ###

`<prefix> o`

### Switch between current and previous pane ###

`<prefix> ;`

### Kill current pane ###

`<prefix> x`

### Toggle pane zoom ###

`<prefix> z`

### Break a pane into its own window ###

`<prefix> !`

See this [Superuser answer](https://superuser.com/a/272901) for a guide to
joining a window back into a pane of another window (i.e., the closest thing to
a reverse of this operation).

### Resize panes ###

Start by entering `<prefix> :` then type:

- `resize-pane [-t <pane>] <direction> [amount]`

where `<pane>` is the id of the pane; direction  `-U`/`-D`/`-L`/`-R` for
up/down/left/right respectively; amount is the number of cells to resize by (1
cell if unspecified).


Server
------

Kill the tmux server, along with all sessions:
```console
$ tmux kill-server
```

Customisation
-------------

It's possible to customise tmux, including replacing the `CTRL-b` keystroke (e.g.,
`CTRL-a`).

The config file lives at `~/.tmux.conf`. To rebind the prefix keystroke, add the 
following line:
```
set -g prefix C-a
```

See also
--------

<https://gist.github.com/MohamedAlaa/2961058>

