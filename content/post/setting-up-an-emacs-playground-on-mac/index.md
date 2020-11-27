+++
title = "Setting Up an Emacs Playground on MacOS - Emacs Mac Port | Chemacs | Emacsclient | Spacemacs "
author = ["Aidan Scannell"]
date = 2020-03-29T00:00:00+00:00
tags = ["spacemacs", "emacs"]
draft = false
+++

This is a short post detailing how I installed Emacs and configured an environment for maintaining multiple configurations (on my MacBook Pro).
I wanted to write the post because I have been on a roller coaster getting an Emacs install that provides all of the functionality that I want (maybe even need!).

Some Emacs installs (e.g. [emacs](https://github.com/brew-stuff/homebrew-emacs) from homebrew) are not recognised by the yabai tiling window manager and don't tile properly.
This really started to bug me so I invested a hefty chunk of time (in classic Emacs style) to find a solution.
I stumbled across [Emacs-plus](https://github.com/d12frosted/homebrew-emacs-plus) which solved the issue but left me with another...
I use the [pdf-tools](https://github.com/politza/pdf-tools) package through the [pdf-tools spacemacs layer](https://develop.spacemacs.org/layers/+tools/pdf-tools/README.html) for viewing all my pdfs; writing `LaTeX` docs (using org-mode and/or auctex), reading books, reading papers (using [org-ref](https://github.com/jkitchin/org-ref)) etc.
Unfortunately, both of these installs don't support retina pdf quality in PDFView (pdf-tools).
So I set out on a second mission to get my myself a high res pdf viewing experience within Emacs.

Many GitHub issues later and [The Emacs Mac Port](https://bitbucket.org/mituharu/emacs-mac/src/master/README-mac) came to the rescue.
[This](https://ylluminarious.github.io/2019/05/23/emacs-mac-port-introduction/) is an excellent blog post detailing how [The Emacs Mac Port](https://bitbucket.org/mituharu/emacs-mac/src/master/README-mac) (which I installed using Homebrew from [this repo](https://github.com/railwaycat/homebrew-emacsmacport)) greatly improves Emacs' functionality with MacOS.
In particular, it provides a lot of native GUI support.

I personally don't like having a title bar on my beautiful editor so I choose not to install it.
I think I read somewhere that it might interfere with tiling window managers as well and we can't be having that, so let's install it without,

```zsh
brew install emacs-mac --with-no-title-bars
```

and to make sure that we are using the right install be sure to link emacs-mac with,

```zsh
brew link emacs-mac
```

Now that we are using The Emacs Mac Port we need to add the following to our config file (user-config in spacemacs) if we want to enjoy the fruits of our labour,

```lisp
  ;; combined with emacs-mac this gives good pdf quality for retina display
  (setq pdf-view-use-scaling t)
```

I also like PDFView to open with the pdf fit to the screen (show 1 page) so I also added the following,

```lisp
  ;; default page width behavior
  (setq-default pdf-view-display-size 'fit-page)
```


## Chemacs {#chemacs}

[Chemacs](https://github.com/plexus/chemacs) is an Emacs profile switcher that makes it easy to run multiple Emacs configs side by side.
I am currently running six Emacs configurations,

1.  New Spacemacs Base (Develop Branch)
    -   This is a new config that I am setting up using just spacemacs-base instead of full spacemacs. I want to understand all of the packages I am using and install only the ones I need, thus avoiding a lot of bloat.
2.  New Spacemacs Base (Master Branch)
    -   This is the same config file but running on spacemacs master instead of the develop branch.
3.  Literate Org Config File
    -   This is the same configuration but written in an Org file with lots of documentation. I use tangle/detangle to produce emacs lisp files from the org file. I haven't decided if I want to fully invest in a literate config file so this is a nice way to experiment.
4.  Vanilla Emacs
    -   Although I love spacemacs I am eager to build a full Emacs config from scratch and this config is my attempt.
5.  Spacemacs Old Develop
    -   This is my old (full) spacemacs config running on the develop branch.
6.  Spacemacs Old Master
    -   This is my old spacemacs config running on master.

It's super easy to setup, just clone the repo and run the install script.
I don't think I need to repeat the instructions that are listed in their README.
Once you have it setup the main functionality comes from two files.
First there is the `~/.emacs-profiles.el` file where you define all of your different configurations.
This is what my `~/.emacs-profiles.el` file looks like,

```lisp
  (("vanilla" . ((user-emacs-directory . "~/.dotfiles/vanilla-emacs")))

  ("spacemacs-old-m" . ((user-emacs-directory . "~/spacemacs")
                   (env . (("SPACEMACSDIR" . "~/.dotfiles/spacemacs-old")))))

  ("spacemacs-old-d" . ((user-emacs-directory . "~/spacemacs/develop")
                   (env . (("SPACEMACSDIR" . "~/.dotfiles/spacemacs-old")))))

  ("spacemacs-master" . ((user-emacs-directory . "~/spacemacs")
                   (env . (("SPACEMACSDIR" . "~/.dotfiles/spacemacs-base-new")))))

   ("new-config" . ((user-emacs-directory . "~/spacemacs/develop")
                    (env . (("SPACEMACSDIR" . "~/.dotfiles/spacemacs-base-new")))))

   ("org-config" . ((user-emacs-directory . "~/spacemacs/develop")
                    (env . (("SPACEMACSDIR" . "~/.dotfiles/spacemacs-org-config"))))))
```

1.  Chemacs will load the `init.el` file from the `user-emacs-directory`,
    -   you can change the file name/path by setting the `cutom-file` variable.
2.  You can set each configuration file to use a different server name with the `server-name` variable,
    -   this is super useful if you want to exploit emacsclient for a speedy startup, something I am currently working on!
3.  A set of environment variables with `env`,
    -   I use this to set the `SPACEMACSDIR` variable which tells spacemacs where to look for extra customisation's.

The other Chemacs file is the `~/.emacs-profile` file where you set the default config to use.
Mine is currently,

```lisp
new-config
```

Another great benefit of Chemacs is that it also makes it super easy to version control all of your emacs configuration files, layers, snippets etc.
I keep all of mine in my version controlled `~/.dotfiles` folder with their own dedicated folders.
For example I have put all of my snippets (for use with [yasnippet](https://github.com/joaotavora/yasnippet)) inside a private folder
`~/.dotfiles/spacemacs-base-new/private/snippets` and all of my layers are inside `~/.dotfiles/spacemacs-base-new/layers`.
To make my configs more portable I also set the layer path variable in the `dotspacemacs/layers` function using,

```lisp
   dotspacemacs-configuration-layer-path (list (concat dotspacemacs-directory "layers/"))
```

and set any references to the private directory with something like,

```lisp
(auto-completion :variables auto-completion-private-snippets-directory (concat dotspacemacs-directory "/private/snippets")
```


## Emacs Server/Client {#emacs-server-client}

The Emacs server is super useful if your config file takes a couple of seconds to load.
I know that some of mine do and I hate waiting...

Luckily we can run an Emacs server with the first instance we open and then connect to this server using `emacsclient` when "opening" subsequent instances.
These new instances open almost instantaneously for me.

To get this working you first have to start the server.
I have been struggling to get it setup with the spacemacs server config so I turn off all of the spacemacs server functionality,

```lisp
;; If non-nil, start an Emacs server if one is not already running.
;; (default nil)
dotspacemacs-enable-server nil

;; Set the emacs server socket location.
;; If nil, uses whatever the Emacs default is, otherwise a directory path
;; like \"~/.emacs.d/server\". It has no effect if
;; `dotspacemacs-enable-server' is nil.
;; (default nil)
dotspacemacs-server-socket-dir nil
;; dotspacemacs-server-socket-dir "~/.emacs.d/server"

;; If non-nil, advise quit functions to keep server open when quitting.
;; (default nil)
dotspacemacs-persistent-server nil
```

and start my own by adding,

```lisp
  (server-start)
```

to my `user-config`.

We now need to know if an Emacs server is running so that we can either connect to it or start a new Emacs instance if not.
To get this working I use the following shell script.

```zsh
#!/usr/bin/env zsh

EMACS='/usr/local/opt/emacs-mac/Emacs.app/Contents/MacOS/Emacs.sh'
EMACS_CLIENT='/usr/local/opt/emacs-mac/bin/emacsclient'

DEFAULT_EVAL='(switch-to-buffer "*scratch*")'
# DEFAULT_SERVER='-s '$HOME'/.emacs.d/server/server'
NO_WAIT='-nw'


# Checks if there's a frame open
if pgrep Emacs &> /dev/null; then
echo "opening emacsclient"
$EMACS_CLIENT $NO_WAIT $DEFAULT_EVAL "$@"
else
echo "opening emacs"
$EMACS
fi
```

You might have to change the `EMACS` and `EMACS_CLIENT` variables depending where brew linked your install.
Let's give our shell script permissions,

```bash
  chmod +x ~/.emacs.d/emacs-client-server.sh
```

and set an alias `e` "emacs" by executing the following (assuming you use zsh),

```bash
  echo "alias te=\"~/.emacs.d/emacs-client-server.sh\"" >> ~/.zshrc
```

If you use `bash` then it will be,

```bash
  echo "alias te=\"~/.emacs.d/emacs-client-server.sh\"" >> ~/.bashrc
```

but you should consider switching!
We can now open new Emacs instances by typing `e <file-name>` or simply `e` into terminal.

I take this one step further as I use [`skhd`](https://github.com/koekeishiya/skhd) (a simple hotkey daemon for macOS) to open my default Emacs config (utilising emacsclient) with a simple keybinding.
Creating an extra script was probably overkill but it works so I am happy.
The only difference here is that no filename is passed to `emacsclient` so we instead ask it to open a new frame.

```zsh
#!/usr/bin/env zsh

EMACS='/usr/local/opt/emacs-mac/Emacs.app/Contents/MacOS/Emacs.sh'
EMACS_CLIENT='/usr/local/opt/emacs-mac/bin/emacsclient'

# Checks if there's a frame open
if pgrep Emacs &> /dev/null; then
    echo "opening emacsclient"
    $EMACS_CLIENT -nqc
else
    echo "opening emacs"
    $EMACS
fi
```

Again let's give it permissions,

```zsh
  chmod +x ~/.emacs.d/skhd-emacs-client-server.sh
```

I then set `CMD m` to run the shell script by placing the following in my `~/.config/skhd/skhdrc` file,

```zsh
cmd - m : ~/.emacs.d/skhd-emacs-client-server.sh
```

This will either connect to the server of a previously running instance and open a new frame or open a new Emacs instance and start a server.

Fantastic, we now have a super speedy Emacs setup that we can easily use with six different configurations.
If anyone has any great ideas for improving anything I  have shown here I am all ears :ear:.
Happy hacking..
