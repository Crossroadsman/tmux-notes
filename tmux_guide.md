Tmux
====

Anatomy of a Tmux Session
-------------------------
Tmux has 'sessions', 'windows', and 'panes'.

Sessions
--------

### Start a new session ###

```console
$ tmux new -s <session_name>
```

Note the `-s` argument is optional, omit to create an unnameed session.

### Detach from session ###

`CTRL+b d`

### List sessions ###

```console
$ tmux ls
```

or from inside a session:
`CTRL-b s`

### Attach to a session ###

```console
$ tmux a -t <session_name>|<session_id>
```

Note `a` is an optional shorthand for `attach`
Note `a` on its own without `-t <session>` will attach to the first available session

### Name a session ###

`CTRL-b $`

### Kill a session ###

```console
$ tmux kill-session -t <session_name>|<session_id>
```

Note you can also kill tmux entirely with `killall tmux`


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

`CTRL-b "`

### Split horizontally ###
(turn pane into two horizontally side-by-side panes aka create a vertical divider):

`CTRL-b %`

### Navigate to another pane ###

`CTRL-b <arrow_key>`

### Cycle through panes ###

`CTRL-b o`

### Switch between current and previous pane ###

`CTRL-b ;`

### Kill current pane ###
`CTRL-b x`

### Toggle pane zoom ###
`CTRL-b z`

### Resize panes ###

Start by entering `<prefix> :` then type:

- `resize-pane [-t <pane>] <direction> [amount]`

where `<pane>` is the id of the pane; direction is blank for down or `-U`/`-L`/`-R` for
up/left/right respectively; amount is the number of cells to resize by.


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

