<div id="table-of-contents">
<h2>Table of Contents</h2>
<div id="text-table-of-contents">
<ul>
<li><a href="#what-is-this">1. What is this?</a></li>
<li><a href="#quick-start">2. Quick start</a>
<ul>
<li><a href="#how-do-i-install-it">2.1. How to I install it?</a></li>
<li><a href="#first-run">2.2. First run</a></li>
<li><a href="#modified-key-bindings">2.3. Important key bindings</a>
<ul>
<li><a href="#orgd40e7ba">2.3.1. Standard keyboard shortcuts</a></li>
<li><a href="#org187862c">2.3.2. Searching and Completion</a></li>
<li><a href="#org45806db">2.3.3. REPL interaction</a></li>
<li><a href="#org5bb03ba">2.3.4. Window management keys</a></li>
<li><a href="#other-key-bindings">2.3.5. Other key bindings</a></li>
</ul>
</li>
</ul>
</li>
<li><a href="#org69719d0">3. Interacting with external programs</a></li>
<li><a href="#implementation">4. Implementation</a>
<ul>
<li><a href="#version-check">4.1. Version check and preparation</a></li>
<li><a href="#install-useful-packages">4.2. Install useful packages</a></li>
<li><a href="#add-custom-lisp-directory-to-load-path">4.3. Add custom lisp directory to load path</a></li>
<li><a href="#miscellaneous">4.4. Tweak default Emacs settings</a></li>
<li><a href="#org0adb543">4.5. Make Emacs friendlier to newcomers</a></li>
<li><a href="#window-management">4.6. Window Management</a></li>
<li><a href="#spell-checking">4.7. Spell checking and dictionaries</a></li>
<li><a href="#printing">4.8. Printing</a></li>
<li><a href="#minibuffer-hints-and-completion">4.9. Minibuffer hints and completion</a></li>
<li><a href="#auto-complete-configuration">4.10. Auto-complete configuration</a></li>
<li><a href="#which-key">4.11. Which-key</a></li>
<li><a href="#org3c0d875">4.12. Flycheck</a></li>
<li><a href="#outline-magic">4.13. Outline-magic</a></li>
<li><a href="#major-modes-configuration">4.14. Major modes configuration</a>
<ul>
<li><a href="#general-repl-config">4.14.1. General REPL (comint) config</a></li>
<li><a href="#run-r-in-emacs">4.14.2. Run R in emacs (ESS)</a></li>
<li><a href="#run-python-in-emacs">4.14.3. Run python in emacs (python-mode)</a></li>
<li><a href="#emacs-lisp-repl">4.14.4. emacs lisp REPL (ielm)</a></li>
<li><a href="#light-weight-markup-language">4.14.5. Haskell mode</a></li>
<li><a href="#light-weight-markup-language">4.14.6. Light-weight markup language (Markdown mode)</a></li>
<li><a href="#typesetting-markup">4.14.7. Typesetting markup (AucTeX)</a></li>
<li><a href="#org1f2604b">4.14.8. Citations (ivy-bibtex)</a></li>
<li><a href="#note-taking-and-outlining">4.14.9. Note taking and outlining (Org-mode)</a></li>
<li><a href="#multiple-modes-in-one-buffer">4.14.10. Multiple modes in one "buffer" (polymode)</a></li>
<li><a href="#orgcd5f636">4.14.11. Email (mu4e)</a></li>
<li><a href="#file-browsing">4.14.12. File browsing (Dired+)</a></li>
<li><a href="#shell-modes">4.14.13. Shell modes (term, shell and eshell)</a></li>
</ul>
</li>
<li><a href="#orgd8c8f04">4.15. Demonstration tools (command-log-mode)</a></li>
<li><a href="#org5a65433">4.16. Final touches</a></li>
</ul>
</li>
<li><a href="#orgb056937">5. Concluding remarks</a></li>
</ul>
</div>
</div>


<a id="what-is-this"></a>

# What is this?

This is an [Emacs](https://www.gnu.org/software/emacs/) configuration. There are many like it, but this one is mine. If you like it, make it yours! It provides lots of functionality while keeping things light and fast.

The main goal of this project is to provide an Emacs configuration that works more or less they way you would expect an editor or IDE to work in the second decade of the twenty-first century, without losing the things that make Emacs special. This is challenging because basic Emacs commands often conflict with de facto standards. Each of these conflicts is a judgment call; hopefully a good balance has been reached. 

Note that this documentation mostly uses Emacs notation for keybindings, e.g., `C` means "the Ctrl key", `M` means "the Meta (aka Alt) key", and `S` means "the Shift key". Refer to <https://www.emacswiki.org/emacs/EmacsKeyNotation> if you are not familiar with this notation.

Highlights of this Emacs configuration include:

-   More standard select/copy/paste keys and right-click behavior makes it more familiar to those new to Emacs.
-   Consistent use of the `shift` key to for related functionality. For example:
    -   `C-z` is undo, `C-Z` is redo
    -   `M-q` is hard warp, `M-Q` is unwrap
    -   `C-s` searches in current buffer, `C=S` searches all buffers in the directory
    -   `C-x f` (or `C-o`) opens files in the current directory, `C-x F` (or `C-O`) searches for files to open
-   Consistent and familiar code completion using the `tab` key.
-   Consistent and familiar code evaluation using `C-ret`.
-   IDE-like configuration for R, Python, and LaTeX coding.
-   Literate programming configuration for running R, python, or other programming languages inside markdown or org-mode files.
-   Powerful and simple search-based tools for finding commands, files and buffers, inserting citations etc.
-   Convenient window management, including navigation with `C-x O`, and undo/redo with `C-c left` and `C-c right`.
-   Dictionary-lookup using `C-c d`.

The upshot is that if you have never used Emacs before many things will work as you expect; a few will not, in which case you will need to search the web or read the Emacs documentation to learn the Emacs way. You can launch a built-in tutorial by pressing `C-h t` (that's "Control+h, then t"), or read the getting started documentation at <https://www.gnu.org/software/emacs/tour/>. A cheat-sheet / survival guide is available at <https://www.gnu.org/software/emacs/refcards/pdf/survival.pdf>. 

If you are an Emacs user, most things will mostly work as you expect, though you may wish to familiarize yourself with the alternative "de facto standard" bindings configured here. The most glaring exception is the use of `C-v` to paste rather than scroll. My advice is to get in the habit of toggling read-only/view mode with `C-x C-q` (or `M-x read-only-mode`) when you need to do a lot of scrolling. In this mode `SPC` scrolls down and `S-SPC` scrolls up, just like it does in your web browser. When you must scroll down without toggling read-only mode you can use `Page Up` and `Page Down` (if your keyboard doesn't dedicated `Page Up` / `Page Down` keys try `Fn down` and `Fn up`). If you are an Emacs user and you find other key bindings that don't work as they should please open an issue in the [github repo](https://github.com/izahn/dotemacs).


<a id="quick-start"></a>

# Quick start


<a id="how-do-i-install-it"></a>

## How to I install it?

1.  Make sure emacs >= version 25.1 is installed on your computer. See [this list of useful programs](UsefullPrograms.md) for installation instructions.
2.  Make sure you have [git](http://git-scm.com/downloads) installed on your computer. If you don't know what git is you might be interested in John McDonnell's [git tutorial](http://nyuccl.org/pages/GitTutorial/).
3.  Determine your emacs configuration directory. Open emacs and type `C-x f ~/ RET`. This should open a directory listing buffer. Note the path at the top of this file. This is were your `s.d` should go.
4.  Close Emacs.
5.  Back up your existing `~/.emacs` file and `~/.emacs.d` directory (e.g., rename `.emacs` to `OLD.emacs` and rename `.emacs.d` to `OLD.emacs.d`).
6.  Clone this repository into `~/.emacs.d` by opening a terminal and running `git clone http://github.com/izahn/dotemacs ~/.emacs.d`.

If you don't know how to use git, you can skip steps 2 and 6 and simply [download the files as a zip archive](https://github.com/izahn/dotemacs/archive/master.zip), extract them, and move them into your .emacs.d directory instead.


<a id="first-run"></a>

## First run

Note that after installing this configuration emacs will be slow to start up the first time. This is due to package installation; just be patient and wait for it to finish&#x2013;subsequent start-ups will be much faster.


<a id="modified-key-bindings"></a>

## Important key bindings

This configuration loads a lot of useful emacs packages, many of which add key bindings. Documenting them all here would be too much (see the documentation for each package if you need the details), so this section describes only most important ones.


<a id="orgd40e7ba"></a>

### Standard keyboard shortcuts

-   **S-arrow:** Select a region, as in many other programs.
-   **C-c:** Copy selection, as in most other programs.
-   **C-v:** Paste, as in most other programs. Select from the clipboard history with `S-C-v`.
-   **C-z:** Undo, as in most other programs.
-   **S-C-z:** Redo, as in most other programs. Use `C-x U`  or `M-z` to visualize your undo/redo history.
-   **C-o:** Open file, as in most other programs.

Note that some things still work "the Emacs way". Notably:

-   **C-a:** Goes to the beginning of the line. To select all use `C-x h`.
-   **C-s:** Searches. To save, use `C-x s`.
-   **C-f:** Moves forward one character. To search use `C-s`.


<a id="org187862c"></a>

### Searching and Completion

Utilities have been configured to make it easy to search by file name as well as to search the contents of files. Some of this functionality works much better if certain system utilities are found. See [this list of useful programs](UsefullPrograms.md), especially *everything* (windows only) and *the silver search* or *ripgrep*.

-   **C-s:** Searches the active buffer using `swiper`.
-   **C-S:** Searches files in the current directory (recursively) using `counsel-rg` or similar.
-   **C-x F:** (or **C-x O**) Searches by file name &#x2013; requires `mlocate` on linux, `everything` (<http://www.voidtools.com/>) on windows.

Many standard Emacs keybindings have been replaced with versions that provide completion suggestions. In-buffer completion can be triggered with the `tab` key.

-   **tab:** Mapped to `company-complete`, use for completion indentation and completion.
-   **M-y:** Remapped to `counsel-yank-pop` to browse the kill ring interactively. `S-C-v` also works for this.
-   **M-x:** Remapped to `counsel-M-x` to interactively search for interactive functions.
-   **C-c r:** Mapped to `ivy-bibtex` to search for a citation to insert. You must set `bibtex-completion-bibliography` to your BibTeX files for this to work.


<a id="org45806db"></a>

### REPL interaction

This should be easy, and hopefully it is.

-   **C-RET:** Mapped to language specific line/selection/expression evaluation. Want to evaluate code from a script? `C-RET` should "just work".


<a id="org5bb03ba"></a>

### Window management keys

Some convenient window management keys are provided, in addition to the standard Emacs `C-x o` binding to navigate to "other window".

-   **C-x O:** (Ctrl-x shift-o) mapped to `ace-window`, use to quickly navigate to a window by number.
-   **C-c left:** Mapped to `winner-undo`, use to undo a window change.
-   **C-c right:** Mapped to `winner-redo`, use to redo a window change.
-   **C-c C-l #:** Mapped to `eybrowse-switch-to-window-config`, use to save/restore window layouts.


<a id="other-key-bindings"></a>

### Other key bindings

-   **S-C-SPC:** Mapped to `cua-rectangle-mark-mode`, use to edit rectangular regions.
-   **C-up:** Mapped to `scroll-down-1`.
-   **C-down:** Mapped to `scroll-up-1`.
-   **M-Q:** Mapped to `unfill-paragraph`, use to remove line breaks from a paragraph.
-   **C-c C-o t:** Mapped to `outline-cycle`, use to hide/show when outline-minor-mode is active (outline-minor mode is enabled in programming modes and in LaTeX-mode).
-   **C-x cl:** Mapped to `global-command-log-mode`, use to echo keybindings for tutorials.
-   **M-q:** Remapped to `bibtex-fill-entry` (bibtex mode only).
-   **E:** Open in external application (dired mode only)

Other key bindings can be discovered by `describe-bindings` (bound to `C-h b`) or `counsel-descbinds` (access with `M-x counsel-descbinds RET`), or via the menus.


<a id="org69719d0"></a>

# Interacting with external programs

Many of the Emacs features configured here are designed to make it easier to interact with external programs. For example, [ESS](http://ess.r-project.org) makes it easy to interact with [R](http://r-project.org), and [AUCTEX](https://www.gnu.org/software/auctex/) makes it easy to interact with [LaTeX](http://tug.org/texlive/). If you need help installing these programs, [this short guide](UsefullPrograms.md) may help. 


<a id="implementation"></a>

# Implementation

I used to have a long description about all the packages this configuration sets up, but showing you the actual code is better. Each section starts with a description of what it does, followed by the code that implements it.


<a id="version-check"></a>

## Version check and preparation

It is difficult to support multiple versions of emacs, so we will pick an arbitrary cutoff and throw an error if the version of emacs is "too old".

    (when (< (string-to-number 
               (concat 
                (number-to-string emacs-major-version) 
                "." 
                (number-to-string emacs-minor-version)))
              25.1)
      (error "Your version of emacs is very old and must be upgraded before you can use these packages!"))
    
    ;; set coding system so emacs doesn't choke on melpa file listings
    (set-language-environment 'utf-8)
    (setq locale-coding-system 'utf-8)
    (set-default-coding-systems 'utf-8)
    (set-terminal-coding-system 'utf-8)
    (unless (eq system-type 'windows-nt)
      (set-selection-coding-system 'utf-8))
    (prefer-coding-system 'utf-8)
    (setq buffer-file-coding-system 'utf-8)
    (setq x-select-request-type '(UTF8_STRING COMPOUND_TEXT TEXT STRING))
    
    (require 'cl)
    
    ;; set things that need to be set before packages load
    (setq outline-minor-mode-prefix "\C-c\C-o")
    (add-hook 'outline-minor-mode-hook
              (lambda () (local-set-key "\C-c\C-o"
                                        outline-mode-prefix-map)))
    (setq save-abbrevs 'silently)


<a id="install-useful-packages"></a>

## Install useful packages

The main purpose of these emacs configuration files is to install and configure useful emacs packages. Here we carry out the installation.

    ;; load the package manager
    (require 'package)
    (package-initialize t)
    
    ;; Add additional package sources
    (add-to-list 'package-archives 
                 '("melpa" . "http://melpa.milkbox.net/packages/") t)
    
    ;; Make a list of the packages you want
    (setq package-selected-packages
          '(;; gnu packages
            auctex
            windresize
            diff-hl
            adaptive-wrap
            ;; melpa packages
            command-log-mode
            undo-tree
            better-defaults
            diminish
            dired+
            ace-window
            howdoi
            auctex-latexmk
            multi-term
            with-editor
            git-commit
            magit
            eyebrowse
            mouse3
            swiper
            counsel
            flx-ido
            smex
            ivy-bibtex
            hydra
            ivy-hydra
            which-key
            outline-magic
            smooth-scroll
            unfill
            company
            ess
            markdown-mode
            polymode
            eval-in-repl
            haskell-mode
            ghc
            company-ghci
            flycheck
            scala-mode
            ensime
            sbt-mode
            exec-path-from-shell
            htmlize
            sdcv ;; stardictionary
            osx-dictionary
            define-word
            ox-pandoc
            untitled-new-buffer))
    ;; install packages if needed
    (unless (every 'package-installed-p package-selected-packages)
      (package-refresh-contents)
      ;; org needs to be installed first
      (package-install (cadr (assq 'org package-archive-contents)))
      (package-install-selected-packages))
    (package-initialize)


<a id="add-custom-lisp-directory-to-load-path"></a>

## Add custom lisp directory to load path

We try to install most things using the package manager, but a few things need to be included in a custom lisp directory. Add it to the path so we can load from it easily.

    ;; add custom lisp directory to path
    (let ((default-directory (concat user-emacs-directory "lisp/")))
      (setq load-path
            (append
             (let ((load-path (copy-sequence load-path))) ;; Shadow
               (append 
                (copy-sequence (normal-top-level-add-to-load-path '(".")))
                (normal-top-level-add-subdirs-to-load-path)))
             load-path)))
    
    ;; on OSX Emacs needs help setting up the system paths
    (when (memq window-system '(mac ns))
      (exec-path-from-shell-initialize))


<a id="miscellaneous"></a>

## Tweak default Emacs settings

This section sets up various utilities and conveniences. Many of these are low priority, so we set them first in order to allow any conflicting settings to be overridden later.

    ;; better defaults are well, better... but we don't always agree
    (menu-bar-mode 1)
    
    ;; Mouse scrolling behavior
    (setq mouse-wheel-scroll-amount '(1 ((shift) . 1))) ;; one line at a time
    (setq mouse-wheel-follow-mouse 't) ;; scroll window under mouse
    
    ;; Use y/n instead of yes/no
    (fset 'yes-or-no-p 'y-or-n-p)
    
    (transient-mark-mode 1) ; makes the region visible
    (line-number-mode 1)    ; makes the line number show up
    (column-number-mode 1)  ; makes the column number show up
    
    ;; ;; smooth scrolling with C-up/C-down
    (require 'smooth-scroll)
    (smooth-scroll-mode)
    (global-set-key [(control down)] 'scroll-up-1)
    (global-set-key [(control up)] 'scroll-down-1)
    (global-set-key [(control left)] 'scroll-right-1)
    (global-set-key [(control right)] 'scroll-left-1)
    
    ;; make home and end behave
    (global-set-key (kbd "<home>") 'move-beginning-of-line)
    (global-set-key (kbd "<end>") 'move-end-of-line)
    
    ;; enable toggling paragraph un-fill
    (define-key global-map "\M-Q" 'unfill-paragraph)
    
    ;;; line wrapping
    ;; neck beards be damned, we don't need to hard wrap. The editor can soft wrap for us.
    (remove-hook 'text-mode-hook 'turn-on-auto-fill)
    (add-hook 'visual-line-mode-hook 'adaptive-wrap-prefix-mode)
    (add-hook 'text-mode-hook 'visual-line-mode 1)
    (add-hook 'prog-mode-hook
              (lambda()
                (toggle-truncate-lines t)
                  (outline-minor-mode t)))
    
    ;; indicate visual-line-mode wrap
    (setq visual-line-fringe-indicators '(left-curly-arrow right-curly-arrow))
    (setq visual-line-fringe-indicators '(left-curly-arrow right-curly-arrow))
    ;; but be gentle
    (defface visual-line-wrap-face
    '((t (:foreground "gray")))
    "Face for visual line indicators.")
    (set-fringe-bitmap-face 'left-curly-arrow 'visual-line-wrap-face)
    (set-fringe-bitmap-face 'right-curly-arrow 'visual-line-wrap-face)
    
    ;; don't require two spaces for sentence end.
    (setq sentence-end-double-space nil)
    
    ;; The beeping can be annoying--turn it off
    (set-variable 'visible-bell t)
    
    ;; save place -- move to the place I was last time I visited this file
    (save-place-mode t)
    
    ;; easy navigation in read-only buffers
    (setq view-read-only t)
    (define-key view-mode-map (kbd "s") 'swiper)


<a id="org0adb543"></a>

## Make Emacs friendlier to newcomers

Emacs will never to as simple as Notepad, but perhaps it can be made more consistent with the way most other programs behave.

    ;; Use CUA mode to make life easier. We _do_ use standard copy/paste etc. 
    (cua-mode t)
    
    ;; (cua-selection-mode t) ;; uncomment this to get cua goodness without copy/paste etc.
    
    ;; ;; Make control-z undo
    (global-undo-tree-mode t)
    (global-set-key (kbd "C-z") 'undo)
    (define-key undo-tree-map (kbd "C-S-z") 'undo-tree-redo)
    (define-key undo-tree-map (kbd "C-x u") 'undo)
    (define-key undo-tree-map (kbd "C-x U") 'undo-tree-visualize)
    (define-key undo-tree-map (kbd "M-z") 'undo-tree-visualize)
    ;; Make C-g quit undo tree
    (define-key undo-tree-visualizer-mode-map (kbd "C-g") 'undo-tree-visualizer-quit)
    (define-key undo-tree-visualizer-mode-map (kbd "<escape> <escape> <escape>") 'undo-tree-visualizer-quit)
    
    
    
    ;; ;; 
    ;; Make right-click do something close to what people expect
    (global-set-key (kbd "<mouse-3>") 'mouse3-popup-menu)
    ;; (global-set-key (kbd "C-f") 'isearch-forward)
    ;; (global-set-key (kbd "C-s") 'save-buffer)
    ;; (global-set-key (kbd "C-o") 'counsel-find-file)
    (define-key cua-global-keymap (kbd "<C-S-SPC>") nil)
    (define-key cua-global-keymap (kbd "<C-return>") nil)
    (setq cua-rectangle-mark-key (kbd "<C-S-SPC>"))
    (define-key cua-global-keymap (kbd "<C-S-SPC>") 'cua-rectangle-mark-mode)


<a id="window-management"></a>

## Window Management

Emacs has [window layout management](https://www.gnu.org/software/emacs/manual/html_node/emacs/Configuration-Registers.html#Configuration-Registers), built-in but it's not convenient to use. [Eyebrowse](https://github.com/wasamasa/eyebrowse) makes it easier, so we use that. Create a new layout with `C-c C-l C-n`, switch with `C-c C-l #` . 

The basic window navigation with `C-c C-o` does not make it easy to navigate quickly to a specific window, so we use `ace-window` for that. Use `C-x O` to quickly navigate to a window.

`winner-mode` allows you to undo/redo window configuration changes. Use `C-c <left>` to undo adn `C-c <right>` to redo.

    ;; Work spaces
    (setq eyebrowse-keymap-prefix (kbd "C-c C-l"))
    (eyebrowse-mode t)
    
    ;; Undo/redo window changes
    (winner-mode 1)
    
    ;; use ace-window for navigating windows
    (global-set-key (kbd "C-x O") 'ace-window)
    (with-eval-after-load "ace-window"
      (set-face-attribute 'aw-leading-char-face nil :height 2.5))


<a id="spell-checking"></a>

## Spell checking and dictionaries

Emacs comes with spell checking built-in, it just needs to be turned on. By default automatic spell checking is enabled in `text-mode` and `prog-mode` buffers. You can also spell-check on demand with `ispell-word`, bound to `M-$`. Finally, dictionaries look-up is available and bound to `C-c d`.

More information is available at <https://www.gnu.org/software/emacs/manual/html_node/emacs/Spelling.html> and <https://github.com/abo-abo/define-word>.

    ;; enable on-the-fly spell checking
    (add-hook 'text-mode-hook
              (lambda ()
                (flyspell-mode 1)))
    ;; prevent flyspell from finding mistakes in the code
    (add-hook 'prog-mode-hook
              (lambda ()
                ;; `ispell-comments-and-strings'
                (flyspell-prog-mode)))
    
    ;; ispell should not check code blocks in org mode
    (add-to-list 'ispell-skip-region-alist '(":\\(PROPERTIES\\|LOGBOOK\\):" . ":END:"))
    (add-to-list 'ispell-skip-region-alist '("#\\+BEGIN_SRC" . "#\\+END_SRC"))
    (add-to-list 'ispell-skip-region-alist '("#\\+begin_src" . "#\\+end_src"))
    (add-to-list 'ispell-skip-region-alist '("^#\\+begin_example " . "#\\+end_example$"))
    (add-to-list 'ispell-skip-region-alist '("^#\\+BEGIN_EXAMPLE " . "#\\+END_EXAMPLE$"))
    
    ;; Dictionaries
    
    ;; default in case we don't find something local
    (global-set-key (kbd "C-c d") 'define-word-at-point)
    (global-set-key (kbd "C-c S-D") 'define-word)
    
    ;; use dictionary app on os x
    (when (memq window-system '(mac ns))
      (global-set-key (kbd "C-c d") 'osx-dictionary-search-word-at-point)
      (global-set-key (kbd "C-c S-D") 'osx-dictionary-search-input))
    
    ;; Use stardict if we find a usable interface
    (when (executable-find "sdcv")
      (require 'sdcv)
      (global-set-key (kbd "C-c d") 'sdcv-search-input)
      (global-set-key (kbd "C-c S-D") 'sdcv-search-pointer+)
      (add-hook 'sdcv-mode-hook
                '(lambda()
                   (setq-local font-lock-string-face 'default))))


<a id="printing"></a>

## Printing

If you're using [Vincent Goulet's emacs](http://vgoulet.act.ulaval.ca/en/emacs/windows/) on Windows printing should work out of the box. If you're on Linux or Mac the experience of printing from emacs may leave something to be desired. Here we try to make it work a little better by making it easier to preview buffers in a web browser (you can print from there as usual) and by using [gtklp](http://sourceforge.net/projects/gtklp/) on Linux if it is available.

    (when (eq system-type 'gnu/linux)
      (setq hfyview-quick-print-in-files-menu t)
      (require 'hfyview)
      (setq mygtklp (executable-find "gtklp"))
      (when mygtklp
        (setq lpr-command "gtklp")
        (setq ps-lpr-command "gtklp")))
    
    (when (eq system-type 'darwin)
      (setq hfyview-quick-print-in-files-menu t)
      (require 'hfyview))


<a id="minibuffer-hints-and-completion"></a>

## Minibuffer hints and completion

There are several different systems for providing completion hints in emacs. The default pcomplete system shows completions on demand (usually bound to tab key) in an emacs buffer. Here we set up ivy, which instead shows these completions on-the-fly in the minibuffer. These completions are primarily used to show available files (e.g., with `find-file`) and emacs functions (e.g., with `execute-extended-command`). More information is available at <http://oremacs.com/swiper/>.

Note that completion for in-buffer text (e.g., methods in python-mode, or arguments in R-mode) are handled separately by [company-mode](#auto-complete-configuration).

    (ivy-mode 1)
    
    (setq counsel-find-file-ignore-regexp "\\`\\.")
    (setq ivy-use-virtual-buffers t)
    (setq ivy-count-format "(%d/%d) ")
    (setq ivy-display-style nil)
    
    ;; Ivy-based interface to standard commands
    (global-set-key (kbd "C-s") 'swiper)
    (global-set-key (kbd "C-r") 'swiper)
    ;; Search files in directory with C-S
    (global-set-key (kbd "C-S-s") 'find-grep-dired); default if we don't find something better
    (cond
     ((executable-find "rg") ; search with ripgrep if we have it
      (global-set-key (kbd "C-S-s") 'counsel-rg))
     ((executable-find "ag") ; otherwise search with ag if we have it
      (global-set-key (kbd "C-S-s") 'counsel-ag))
     ((executable-find "pt") ; otherwise search with pt if we have it
      (global-set-key (kbd "C-S-s") 'counsel-pt)))
    (global-set-key (kbd "M-x") 'counsel-M-x)
    (global-set-key (kbd "M-y") 'counsel-yank-pop)
    (global-set-key (kbd "C-S-v") 'counsel-yank-pop)
    (global-set-key (kbd "C-x C-f") 'counsel-find-file)
    (global-set-key (kbd "C-o") 'counsel-find-file)
    ;; search for files to open with "C-O=
    (when (memq window-system '(mac ns)) ; use mdfind on Mac. TODO: what about windows?
      (setq locate-command "mdfind")
      (setq counsel-locate-cmd 'counsel-locate-cmd-mdfind))
    (global-set-key (kbd "C-x C-S-F") 'find-name-dired) ; default in case we don't have something better
    (global-set-key (kbd "C-x C-S-F") 'counsel-locate)
    (global-set-key (kbd "C-S-O") 'counsel-locate)
    (global-set-key (kbd "C-x C-r") 'counsel-recentf)
    (global-set-key (kbd "<C-tab>") 'counsel-company)
    (global-set-key (kbd "<f1> f") 'counsel-describe-function)
    (global-set-key (kbd "<f1> v") 'counsel-describe-variable)
    (global-set-key (kbd "<f1> l") 'counsel-load-library)
    (global-set-key (kbd "<f2> i") 'counsel-info-lookup-symbol)
    (global-set-key (kbd "<f2> u") 'counsel-unicode-char)
    ;; Ivy-based interface to shell and system tools
    (global-set-key (kbd "C-c g") 'counsel-git)
    (global-set-key (kbd "C-c j") 'counsel-git-grep)
    (global-set-key (kbd "C-c k") 'counsel-ag)
    (global-set-key (kbd "C-x l") 'counsel-locate)
    (global-set-key (kbd "C-S-o") 'counsel-rhythmbox)
    ;; Ivy-resume and other commands
    
    (global-set-key (kbd "C-c i") 'ivy-resume)
    
    ;; Make Ivy more like ido
    (define-key ivy-minibuffer-map (kbd "<return>") 'ivy-alt-done)
    (define-key ivy-minibuffer-map (kbd "C-d") 'ivy-done)
    (define-key ivy-minibuffer-map (kbd "C-b") 'ivy-immediate-done)
    (define-key ivy-minibuffer-map (kbd "C-f") 'ivy-immediate-done)
    
    ;; show recently opened files
    (setq recentf-max-menu-items 50)
    (recentf-mode 1)


<a id="auto-complete-configuration"></a>

## Auto-complete configuration

Here we configure in-buffer text completion using the company-mode package. These completions are available on-demand using `tab` for in-buffer popup or `C-tab` for search-able minibuffer list. More information is available at <https://company-mode.github.io/>.

    (require 'company)
    ;; cancel if input doesn't match, be patient, and don't complete automatically.
    (setq company-require-match nil
          company-async-timeout 6
          company-idle-delay nil
          company-global-modes '(not term-mode))
    ;; complete using C-tab
    (global-set-key (kbd "<C-tab>") 'counsel-company)
    ;; use C-n and C-p to cycle through completions
    ;; (define-key company-mode-map (kbd "<tab>") 'company-complete)
    (define-key company-active-map (kbd "C-n") 'company-select-next)
    (define-key company-active-map (kbd "<tab>") 'company-complete-common)
    (define-key company-active-map (kbd "C-p") 'company-select-previous)
    (define-key company-active-map (kbd "<backtab>") 'company-select-previous)
    
    (require 'company-capf)
    ;; put company-capf and company-files at the beginning of the list
    (setq company-backends
          '(company-files company-capf company-nxml company-css company-cmake company-semantic company-clang company-xcode company-eclim))
    (setq-default company-backends
                  '(company-files company-capf company-nxml company-css company-cmake company-semantic company-clang company-xcode company-eclim))
    
    ;;Use tab to complete.
    ;; See https://github.com/company-mode/company-mode/issues/94 for another approach.
    
    ;; this is a copy-paste from the company-package with extra conditions to make
    ;; sure we don't offer completions in the middle of a word.
    
    (defun my-company-indent-or-complete-common ()
      "Indent the current line or region, or complete the common part."
      (interactive)
      (cond
       ((use-region-p)
        (indent-region (region-beginning) (region-end)))
       ((and (not (looking-at "\\w\\|\\s_"))
             (memq indent-line-function
                   '(indent-relative indent-relative-maybe)))
        (company-complete-common))
       ((let ((old-point (point))
              (old-tick (buffer-chars-modified-tick))
              (tab-always-indent t))
          (call-interactively #'indent-for-tab-command)
          (when (and (eq old-point (point))
                     (eq old-tick (buffer-chars-modified-tick))
                     (not (looking-at "\\w\\|\\s_")))
            (company-complete-common))))))
    
    (define-key company-mode-map (kbd "<tab>") 'my-company-indent-or-complete-common)
    
    ;; not sure why this should be set in a hook, but that is how the manual says to do it.
    (add-hook 'after-init-hook 'global-company-mode)


<a id="which-key"></a>

## Which-key

This mode shows a keymap when an incomplete command is entered. It is especially useful for families of commands with a prefix, e.g., `C-c C-o` for `outline-mode` commands, or `C-c C-v` for `org-babel` commands. Just start typing your command and pause if you want a hint.

    ;; (require 'which-key)
    (which-key-mode)


<a id="org3c0d875"></a>

## Flycheck

Provides on-the-fly syntax checking. Depends on external tools, e.g, [lintr](https://cran.rstudio.com/web/packages/lintr/index.html) for R code, [flake8](https://flake8.readthedocs.io/en/latest/) for python. See <http://www.flycheck.org/en/latest/languages.html#flycheck-languages> for supported languages and tools.

Note that active on-the-fly syntax checking is <span class="underline">disabled</span> by default since I find it too annoying. You can still use `flycheck` to check your syntax on demand using `flycheck-compile`, and you can enable on-the-fly checking with `M-x flycheck-mode`.

    (require 'flycheck)
    ;; (global-flycheck-mode)


<a id="outline-magic"></a>

## Outline-magic

I encourage you to use [org-mode](#note-taking-and-outlining) for note taking and outlining, but it can be convenient to treat arbitrary buffers as outlines. The outline-magic mode can help with that.

    ;;; Configure outline minor modes
    ;; Less crazy key bindings for outline-minor-mode
    (setq outline-minor-mode-prefix "\C-c\C-o")
    ;; load outline-magic along with outline-minor-mode
    (add-hook 'outline-minor-mode-hook 
              (lambda () 
                (require 'outline-magic)
                (define-key outline-minor-mode-map "\C-c\C-o\t" 'outline-cycle)))


<a id="major-modes-configuration"></a>

## Major modes configuration


<a id="general-repl-config"></a>

### General REPL (comint) config

Many programs using REPLs are derived from `comint-mode`, so we can affect all of them by changing `comint-mode` settings. Here we disable line wrapping and ask programs to echo the input.

Load eval-in-repl for bash, elisp, and python interaction.

    ;; require the main file containing common functions
    (require 'eval-in-repl)
    (setq comint-process-echoes t)
    
    ;; truncate lines in comint buffers
    (add-hook 'comint-mode-hook
              (lambda()
                (setq truncate-lines 1)))
    
    ;; Scroll down for input and output
    (setq comint-scroll-to-bottom-on-input t)
    (setq comint-scroll-to-bottom-on-output t)
    (setq comint-move-point-for-output t)


<a id="run-r-in-emacs"></a>

### Run R in emacs (ESS)

Support for R in Emacs is good, thanks to <http://ess.r-project.org/>. As with other programming languages this configuration enables completion via the `tab` key and code evaluation with `C-ret`. Many more features are provided by ESS, refer to <http://ess.r-project.org/> for details.

      ;;;  ESS (Emacs Speaks Statistics)
    
    ;; Start R in the working directory by default
    (setq ess-ask-for-ess-directory nil)
    
    ;; Make sure ESS is loaded before we configure it
    (autoload 'julia "ess-julia" "Start a Julia REPL." t)
    (with-eval-after-load "ess-site"
      ;; see https://github.com/emacs-ess/ESS/pull/390 for ideas on how to integrate tab completion
      ;; disable ehoing input
      (setq ess-eval-visibly nil)
      ;; Start R in the working directory by default
      (setq ess-ask-for-ess-directory nil)
      ;; Use tab completion
      (setq ess-tab-complete-in-script t)
      ;; extra ESS stuff inspired by https://github.com/gaborcsardi/dot-emacs/blob/master/.emacs
      (ess-toggle-underscore nil)
      (defun my-ess-execute-screen-options (foo)
        "cycle through windows whose major mode is inferior-ess-mode and fix width"
        (interactive)
        (setq my-windows-list (window-list))
        (while my-windows-list
          (when (with-selected-window (car my-windows-list) (string= "inferior-ess-mode" major-mode))
            (with-selected-window (car my-windows-list) (ess-execute-screen-options t)))
          (setq my-windows-list (cdr my-windows-list))))
      (add-to-list 'window-size-change-functions 'my-ess-execute-screen-options)
      (define-key ess-mode-map (kbd "<C-return>") 'ess-eval-region-or-function-or-paragraph-and-step)
      ;; truncate long lines in R source files
      (add-hook 'ess-mode-hook
                (lambda()
                  ;; don't wrap long lines
                  (toggle-truncate-lines t)
                  (outline-minor-mode t)))
      ;; highlight function calls and operators
      (setq ess-R-font-lock-keywords
            (quote
             ((ess-R-fl-keyword:modifiers)
              (ess-R-fl-keyword:fun-defs . t)
              (ess-R-fl-keyword:keywords . t)
              (ess-R-fl-keyword:assign-ops . t)
              (ess-R-fl-keyword:constants . 1)
              (ess-fl-keyword:fun-calls . t)
              (ess-fl-keyword:numbers)
              (ess-fl-keyword:operators . t)
              (ess-fl-keyword:delimiters)
              (ess-fl-keyword:=)
              (ess-R-fl-keyword:F&T)
              (ess-R-fl-keyword:%op% . t)))))


<a id="run-python-in-emacs"></a>

### Run python in emacs (python-mode)

Emacs has decent python support out of the box. As with other programming languages you can get completion suggestions with the `tab` key, and evaluate code with `C-ret`. Many more features are provided and are accessible via the menu.

    (with-eval-after-load "python"
      ;; try to get indent/completion working nicely
      (setq python-indent-trigger-commands '(my-company-indent-or-complete-common indent-for-tab-command yas-expand yas/expand))
      ;; readline support is wonky at the moment
      (setq python-shell-completion-native-enable nil)
      ;; simple evaluation with C-ret
      (require 'eval-in-repl-python)
      (define-key python-mode-map "\C-c\C-c" 'eir-eval-in-python)
      (define-key python-mode-map (kbd "<C-return>") 'eir-eval-in-python))


<a id="emacs-lisp-repl"></a>

### emacs lisp REPL (ielm)

If you want to get the most out of Emacs, you'll eventually need to learn a little Emacs-lisp. This configuration helps by providing a standard `C-ret` evaluation key binding, and by providing completion with the `tab` key.

    (with-eval-after-load "elisp-mode"
      (require 'company-elisp)
      ;; ielm
      (require 'eval-in-repl-ielm)
      ;; For .el files
      (define-key emacs-lisp-mode-map "\C-c\C-c" 'eir-eval-in-ielm)
      (define-key emacs-lisp-mode-map (kbd "<C-return>") 'eir-eval-in-ielm)
      ;; For *scratch*
      (define-key lisp-interaction-mode-map "\C-c\C-c" 'eir-eval-in-ielm)
      (define-key emacs-lisp-mode-map (kbd "<C-return>") 'eir-eval-in-ielm)
      ;; For M-x info
      (define-key Info-mode-map "\C-c\C-c" 'eir-eval-in-ielm)
      ;; Set up completions
      (add-hook 'emacs-lisp-mode-hook
                (lambda()
                  ;; make sure completion calls company-elisp first
                  (require 'company-elisp)
                  (setq-local company-backends
                              (delete-dups (cons 'company-elisp (cons 'company-files company-backends)))))))


<a id="light-weight-markup-language"></a>

### Haskell mode

I just recently started learning Haskell. There's not much to the configuration at this point, but you should get completion with `tab`.

    (require 'company-ghci)
    (add-hook 'haskell-mode-hook (lambda ()
                                   (setq-local company-backends
                                               (delete-dups (cons 'company-ghci (cons 'company-files company-backends))))))
    (add-hook 'haskell-interactive-mode-hook 'company-mode)


<a id="light-weight-markup-language"></a>

### Light-weight markup language (Markdown mode)

Markdown is a light-weight markup language that makes easy things easy and stays out of your way. You can export Markdown documents to a wide range of formats including .pdf (via latex), .html, .doc, and more using `pandoc`. For more information about authoring markdown in Emacs refer to <http://jblevins.org/projects/markdown-mode/>. For information about Markdown syntax or exporting to other formats refer to <http://pandoc.org>.

    ;; Use markdown-mode for files with .markdown or .md extensions
    (add-to-list 'auto-mode-alist '("\\.markdown\\'" . markdown-mode))
    (add-to-list 'auto-mode-alist '("\\.md\\'" . markdown-mode))


<a id="typesetting-markup"></a>

### Typesetting markup (AucTeX)

I don't write nearly as much in LaTeX as I used to, as Markdown and/or Org mode are simpler and good enough for my needs. But LaTeX is still the tool of choice for much academic writing, so we use AUCTEX and turn on lots of features. Completion of math and latex commands is available with `tab`, and auto-compile is available with `C-ret`.

See <https://www.gnu.org/software/auctex/> for more details about AUCTEX. 

    ;; AucTeX config
    (with-eval-after-load "Latex"
      ;; Easy compile key
      (define-key LaTeX-mode-map (kbd "<C-return>") 'TeX-command-run-all)
      ;; Allow paragraph filling in tables
      (setq LaTeX-indent-environment-list
            (delq (assoc "table" LaTeX-indent-environment-list)
                  LaTeX-indent-environment-list))
      (setq LaTeX-indent-environment-list
            (delq (assoc "table*" LaTeX-indent-environment-list)
                  LaTeX-indent-environment-list))
      ;; Misc. latex settings
      (setq TeX-parse-self t
            TeX-auto-save t)
      (setq-default TeX-master nil)
      ;; Add beamer frames to outline list
      (setq TeX-outline-extra
            '((".*\\\\begin{frame}\n\\|.*\\\\begin{frame}\\[.*\\]\\|.*\\\\begin{frame}.*{.*}\\|.*[       ]*\\\\frametitle\\b" 3)))
      ;; reftex settings
      (setq reftex-enable-partial-scans t)
      (setq reftex-save-parse-info t)
      (setq reftex-use-multiple-selection-buffers t)
      (setq reftex-plug-into-AUCTeX t)
      (add-hook 'LaTeX-mode-hook
                (lambda ()
                  (turn-on-reftex)
                  (TeX-PDF-mode t)
                  (LaTeX-math-mode)
                  (TeX-source-correlate-mode t)
                  (imenu-add-to-menubar "Index")
                  (outline-minor-mode)))
      (add-hook 'bibtex-mode-hook
                (lambda ()
                  (define-key bibtex-mode-map "\M-q" 'bibtex-fill-entry))))


<a id="org1f2604b"></a>

### Citations (ivy-bibtex)

This allows you to search your BibTeX files for references to insert into the current document. For it to work you will need to set \`bibtex-completion-bibliography\` to the location of your BibTeX files.

Initiate a citation search with `ivy-bibtex`, bound to `C-c r`.

See <https://github.com/tmalsburg/helm-bibtex> for information about reading attached .pdf files, searching online bibliography sources and more.

    (setq ivy-bibtex-default-action 'ivy-bibtex-insert-citation)
    (global-set-key (kbd "C-c r") 'ivy-bibtex)


<a id="note-taking-and-outlining"></a>

### Note taking and outlining (Org-mode)

Org mode is a powerful markup-language native to Emacs. It can be compared to markdown, but it has many more features. I use it for note taking a preparing lecture materials, but people use it for all kinds of things, from TODO lists to project planning to authoring academic papers. The settings below try to make Org mode play nicely with other packages, and enable many of the literate programming features. More information about Org mode can be found at <http://orgmode.org>. 

    (with-eval-after-load "org"
      ;; no compay mode in org buffers
      (add-hook 'org-mode-hook (lambda() (company-mode -1)))
      (setq org-replace-disputed-keys t)
      (setq org-support-shift-select t)
      (setq org-export-babel-evaluate nil)
      ;; (setq org-startup-indented t)
      ;; increase imenu depth to include third level headings
      (setq org-imenu-depth 3)
      ;; Set sensible mode for editing dot files
      (add-to-list 'org-src-lang-modes '("dot" . graphviz-dot))
      ;; Update images from babel code blocks automatically
      (add-hook 'org-babel-after-execute-hook 'org-display-inline-images)
      ;; configure org-mode when opening first org-mode file
      ;; Load additional export formats
      (require 'ox-ascii)
      (require 'ox-md)
      (require 'ox-html)
      (require 'ox-latex)
      (require 'ox-odt)
    
      (require 'org-capture)
      (require 'org-protocol)
    
      ;; Enable common programming language support in org-mode
      (require 'ob-shell)
      (require 'ob-emacs-lisp)
      (require 'ob-org)
      (when (executable-find "R") 
          (require 'ess-site)
          (require 'ob-R))
      (when (executable-find "python") (require 'ob-python))
      (when (executable-find "matlab") (require 'ob-matlab))
      (when (executable-find "octave") (require 'ob-octave))
      (when (executable-find "perl") (require 'ob-perl))
      (when (executable-find "dot") (require 'ob-dot))
      (when (executable-find "ditaa") (require 'ob-ditaa))
    
      ;; Fontify code blocks in org-mode
      (setq org-src-fontify-natively t)
      (setq org-src-tab-acts-natively t)
      (setq org-confirm-babel-evaluate nil))


<a id="multiple-modes-in-one-buffer"></a>

### Multiple modes in one "buffer" (polymode)

Emacs uses different *modes* for different kinds of files and buffers. This is what makes is possible to have one set of behaviors when editing LaTeX, and a different set of behaviors when writing R code. But what if we want to do both, in the same file? Then we need to have multiple modes, in the same buffer, and we can thanks to [polymode](https://github.com/vspinu/polymode). 

    ;;; polymode
    ;; polymode requires emacs >= 24.3, does not work on the RCE. 
    (when (>= (string-to-number 
               (concat 
                (number-to-string emacs-major-version) 
                "." 
                (number-to-string emacs-minor-version)))
              24.3)
      ;; Activate polymode for files with the .md extension
      (add-to-list 'auto-mode-alist '("\\.md" . poly-markdown-mode))
      ;; Activate polymode for R related modes
      (add-to-list 'auto-mode-alist '("\\.Snw" . poly-noweb+r-mode))
      (add-to-list 'auto-mode-alist '("\\.Rnw" . poly-noweb+r-mode))
      (add-to-list 'auto-mode-alist '("\\.Rmd" . poly-markdown+r-mode))
      (add-to-list 'auto-mode-alist '("\\.rapport" . poly-rapport-mode))
      (add-to-list 'auto-mode-alist '("\\.Rhtml" . poly-html+r-mode))
      (add-to-list 'auto-mode-alist '("\\.Rbrew" . poly-brew+r-mode))
      (add-to-list 'auto-mode-alist '("\\.Rcpp" . poly-r+c++-mode))
      (add-to-list 'auto-mode-alist '("\\.cppR" . poly-c++r-mode))
      ;; polymode doesn't play nice with adaptive-wrap, turn it off
      (add-hook 'polymode-init-host-hook
                '(lambda()
                   (adaptive-wrap-prefix-mode -1)
                   (electric-indent-mode -1)
                   (unless (featurep 'ess-site)
                     (require 'ess-site)))))


<a id="orgcd5f636"></a>

### Email (mu4e)

Not everyone wants to read email in Emacs, but you can if you want. The settings below configure some basic things, but you will need additional configuration to set up your email accounts. See the [mue4 manual](http://www.djcbsoftware.nl/code/mu/mu4e/index.html#Top) and [example configurations](http://www.djcbsoftware.nl/code/mu/mu4e/Example-configurations.html#Example-configurations) for details.

    (when (executable-find "mu")
      (autoload 'mu4e "mu4e" "Read your mail." t)
      (with-eval-after-load "mu4e"
        (setq mu4e-headers-include-related t
              mu4e-headers-skip-duplicates t
              mu4e-headers-fields '(
                                    (:human-date . 12)
                                    (:flags . 6)
                                    ;; (:mailing-list . 10)
                                    (:from-or-to . 22)
                                    (:thread-subject)))
        ;; don't keep message buffers around
        (setq message-kill-buffer-on-exit t)
        ;; enable notifications
        (setq mu4e-enable-mode-line t)
        ;; use org for composing rich text emails
        (require 'org-mu4e)
        (setq org-mu4e-convert-to-html t)
        (define-key mu4e-headers-mode-map (kbd "C-c c") 'org-mu4e-store-and-capture)
        (define-key mu4e-view-mode-map    (kbd "C-c c") 'org-mu4e-store-and-capture)
        ;; render html
        (require 'mu4e-contrib)
        (setq mu4e-html2text-command 'mu4e-shr2text)
        (add-hook 'mu4e-view-mode-hook 'visual-line-mode)))


<a id="file-browsing"></a>

### File browsing (Dired+)

Emacs makes a decent file browser, we just need to tweak a few things to make it nicer. In particular you can open files in an external program using the `E` key.

    ;;; Dired and Dired+ configuration
    (add-hook 'dired-mode-hook 
              (lambda()
                (diff-hl-dired-mode)
                (diff-hl-margin-mode)))
    
    ;; show details by default
    (setq diredp-hide-details-initially-flag nil)
    
    ;; set dired listing options
    (if (eq system-type 'gnu/linux)
        (setq dired-listing-switches "-alDhp"))
    
    ;; make sure dired buffers end in a slash so we can identify them easily
    (defun ensure-buffer-name-ends-in-slash ()
      "change buffer name to end with slash"
      (let ((name (buffer-name)))
        (if (not (string-match "/$" name))
            (rename-buffer (concat name "/") t))))
    (add-hook 'dired-mode-hook 'ensure-buffer-name-ends-in-slash)
    (add-hook 'dired-mode-hook
              (lambda()
                 (setq truncate-lines 1)))
    
    ;; open files in external programs
    ;; (from http://ergoemacs.org/emacs/emacs_dired_open_file_in_ext_apps.html
    ;; consider replacing with https://github.com/thamer/runner
    (defun xah-open-in-external-app (&optional file)
      "Open the current file or dired marked files in external app.
    
    The app is chosen from your OS's preference."
      (interactive)
      (let (doIt
            (myFileList
             (cond
              ((string-equal major-mode "dired-mode")
               (dired-get-marked-files))
              ((not file) (list (buffer-file-name)))
              (file (list file)))))
        (setq doIt (if (<= (length myFileList) 5)
                       t
                     (y-or-n-p "Open more than 5 files? "))) 
        (when doIt
          (cond
           ((string-equal system-type "windows-nt")
            (mapc
             (lambda (fPath)
               (w32-shell-execute "open" (replace-regexp-in-string "/" "\\" fPath t t)))
             myFileList))
           ((string-equal system-type "darwin")
            (mapc
             (lambda (fPath)
               (shell-command (format "open \"%s\"" fPath)))
             myFileList))
           ((string-equal system-type "gnu/linux")
            (mapc
             (lambda (fPath)
               (let ((process-connection-type nil))
                 (start-process "" nil "xdg-open" fPath))) myFileList))))))
    ;; use zip/unzip to compress/uncompress zip archives
    (with-eval-after-load "dired-aux"
      (add-to-list 'dired-compress-file-suffixes 
                   '("\\.zip\\'" "" "unzip"))
      ;; open files from dired with "E"
      (define-key dired-mode-map (kbd "E") 'xah-open-in-external-app))


<a id="shell-modes"></a>

### Shell modes (term, shell and eshell)

There are several different shells available in Emacs by default. In addition `multi-term` is available to give you a nicer way of running your default shell in Emacs. Convenience functions are enabled to set your EDITOR variable so that Emacs will be used as your editor when running shell commands inside Emacs. 

    ;; term
    (with-eval-after-load "term"
    (define-key term-mode-map (kbd "C-j") 'term-char-mode)
    (define-key term-raw-map (kbd "C-j") 'term-line-mode))
    
    (with-eval-after-load "multi-term"
    (define-key term-mode-map (kbd "C-j") 'term-char-mode)
    (define-key term-raw-map (kbd "C-j") 'term-line-mode))
    
    ;; shell
    (require 'essh) ; if not done elsewhere; essh is in the local lisp folder
    (require 'eval-in-repl-shell)
    (add-hook 'sh-mode-hook
              (lambda()
                 (local-set-key "\C-c\C-c" 'eir-eval-in-shell)))
    
    
    ;; Automatically adjust output width in commint buffers
    ;; from http://stackoverflow.com/questions/7987494/emacs-shell-mode-display-is-too-wide-after-splitting-window
    (defun comint-fix-window-size ()
      "Change process window size."
      (when (derived-mode-p 'comint-mode)
        (let ((process (get-buffer-process (current-buffer))))
          (unless (eq nil process)
            (set-process-window-size process (window-height) (window-width))))))
    
    (defun my-shell-mode-hook ()
      ;; add this hook as buffer local, so it runs once per window.
      (add-hook 'window-configuration-change-hook 'comint-fix-window-size nil t))
    
    (add-hook 'shell-mode-hook
              (lambda()
                 ;; add this hook as buffer local, so it runs once per window.
                 (add-hook 'window-configuration-change-hook 'comint-fix-window-size nil t)))
    
    ;; extra completion for eshell
    (add-hook 'eshell-mode-hook
              (lambda()
                 ;; programs that don't work well in eshell and should be run in visual mode
                 (add-to-list 'eshell-visual-commands "ssh")
                 (add-to-list 'eshell-visual-commands "tail")
                 (add-to-list 'eshell-visual-commands "htop")
                 (setq eshell-visual-subcommands '(("git" "log" "diff" "show")))))
    
    ;; Use emacs as editor when running external processes or using shells in emacs
    (when (and (string-match-p "remacs" (prin1-to-string (frame-list)))
               (executable-find "remacsclient"))
      (setq with-editor-emacsclient-executable (executable-find "remacsclient")))
    
    (require 'with-editor)
    (add-hook 'shell-mode-hook
              (lambda()
                (with-editor-export-editor)
                (with-editor-export-git-editor)
                (sleep-for 0.5) ; this is bad, but thinking hurts and it works.
                (call-interactively 'comint-clear-buffer)))
    (add-hook 'term-exec-hook
              (lambda()
                (with-editor-export-editor)
                (with-editor-export-git-editor)
                (sleep-for 0.5) ; see comment above
                (call-interactively 'comint-clear-buffer)))
    (add-hook 'eshell-mode-hook
              (lambda()
                (with-editor-export-editor)
                (with-editor-export-git-editor)))
    
    (shell-command-with-editor-mode t)
    (require 'git-commit)


<a id="orgd8c8f04"></a>

## Demonstration tools (command-log-mode)

`command-log-mode` is useful for giving emacs demonstrations/tutorials. It shows the keys you've pressed and the commands they called. More information is available at <https://github.com/lewang/command-log-mode>.

    (setq command-log-mode-auto-show t)
    (global-set-key (kbd "C-x cl") 'global-command-log-mode)


<a id="org5a65433"></a>

## Final touches

This Emacs configuration sets up lots of packages and configures a number of keybindings. To add our own customizations, place them in `~/.emacs.d/custom.el`. This file will be sourced last, so you always have the ability to override any settings provided here.

    ;; save settings made using the customize interface to a sparate file
    (setq custom-file (concat user-emacs-directory "custom.el"))
    (unless (file-exists-p custom-file)
      (write-region ";; Put user configuration here" nil custom-file))
    (load custom-file 'noerror)
    
    ;; ;; clean up the mode line
    ; (require 'diminish)
    (diminish 'visual-line-mode)
    (diminish 'which-key-mode)
    (diminish 'company-mode "comp")
    (diminish 'outline-minor-mode "outline")
    (diminish 'undo-tree-mode)
    (diminish 'smooth-scroll-mode)
    
    ;; No, we do not need the splash screen
    (setq inhibit-startup-screen t)
    
    ;; start with untitled new buffer
    (add-hook 'after-init-hook
              '(lambda()
                     (untitled-new-buffer-with-select-major-mode 'text-mode)))
    
    (setq untitled-new-buffer-major-modes '(text-mode emacs-lisp-mode))
    ;; Change default buffer name.
    (setq untitled-new-buffer-default-name "Untitled")


<a id="orgb056937"></a>

# Concluding remarks

That's all folks, report any bugs or feature requests at <https://github.com/izahn/dotemacs>.

