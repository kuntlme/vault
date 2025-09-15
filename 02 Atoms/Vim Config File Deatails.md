---
aliases:
tags:
  - atom
Reference Link: (insert link to book)
Page Number:
Topics:
---

Got it 🚀
Here’s a clean **Markdown document** that explains all the commands in your Mini Vimrc config in a structured way. You can save this as `mini-vimrc-explained.md` inside your vault if you want.

---

# 📖 Mini Vimrc for Obsidian – Explained

This document explains each section of the provided Mini Vimrc configuration for Obsidian.
The goal of this config is to improve navigation, editing, folding, and integration with Obsidian commands while keeping Vim-like keybindings.

---

## 1. Leader Key Setup

```vim
unmap <Space>
" let mapleader = " "
" exmap leader <Space>
```

* Removes the default mapping of `<Space>`.
* Prepares `<Space>` to be used as the **leader key** (though it’s commented out here).
* In this config, `<Space>` is used as a prefix for many commands.

---

## 2. Escape Key Alternatives

```vim
imap kj <Esc>
imap jk <Esc>
imap jj <Esc>
```

* In **insert mode**, pressing:

  * `kj`, `jk`, or `jj` → behaves like `<Esc>`.
* Makes exiting insert mode faster without reaching for the Esc key.

---

## 3. Navigation with Wrapped Lines

```vim
noremap <C-j> j
noremap <C-k> k
nmap j gj
nmap k gk
```

* `Ctrl+j` → move down by one line.
* `Ctrl+k` → move up by one line.
* `j` → move down by **visual line** (useful when text is wrapped).
* `k` → move up by **visual line**.

---

## 4. Better Scrolling and Search Centering

```vim
noremap <c-d> <C-d>zz
noremap <c-u> <C-u>zz
noremap <n> nzzzv
noremap <N> Nzzzv
```

* `Ctrl+d` → half-page down + center the cursor (`zz`).
* `Ctrl+u` → half-page up + center.
* `n` → next search match + keep it centered.
* `N` → previous search match + keep it centered.

---

## 5. Folding (Code/Note Sections)

```vim
exmap unfoldall obcommand editor:unfold-all
nmap zR :unfoldall<CR>

exmap foldall obcommand editor:fold-all
nmap zM :foldall<CR>

exmap foldtoggle obcommand editor:toggle-fold
nmap za :foldtoggle<CR>
```

* `zR` → unfold all sections.
* `zM` → fold all sections.
* `za` → toggle fold under cursor.
* These call Obsidian’s folding commands.

---

## 6. Searching and Replacing

```vim
exmap local_search obcommand editor:open-search
nmap <Space>/ :local_search<CR>
vmap <Space>/ :local_search<CR>

exmap omnisearch_search obcommand omnisearch:show-modal
nmap <Space>f :omnisearch_search<CR>

exmap search_replace obcommand editor:open-search-replace
nmap <Space>s :search_replace<CR>
```

* `<Space>/` → open search (works in normal & visual mode).
* `<Space>f` → open **OmniSearch** plugin modal.
* `<Space>s` → open search & replace dialog.

---

## 7. Theme Management

```vim
exmap theme_switch obcommand theme:switch
nmap <Space>ts :theme_switch<CR>

exmap theme_dark obcommand theme:use-dark
exmap theme_light obcommand theme:use-light
nmap <Space>td :theme_dark<CR>
nmap <Space>tl :theme_light<CR>
```

* `<Space>ts` → open theme switcher.
* `<Space>td` → switch to dark theme.
* `<Space>tl` → switch to light theme.

---

## 8. Quick Switching & Linting

```vim
exmap quick_switch obcommand switcher:open
nmap <Space>O :quick_switch<CR>

exmap lint_current_file obcommand obsidian-linter:lint-file
nmap <Space>lf :lint_current_file<CR>
```

* `<Space>O` → quick switch between notes.
* `<Space>lf` → lint current file with **Obsidian Linter** plugin.

---

## 9. Zen Mode / UI Toggles

```vim
exmap toggle_tab obcommand obsidian-hider:toggle-tab-containers
exmap toggle_right obcommand app:toggle-right-sidebar
nmap <Space>z :toggle_tab<CR>:toggle_right<CR>
```

* `<Space>z` → toggle Zen Mode (hides tab bar + right sidebar).

---

## 10. File Path & Outline

```vim
exmap copy_path obcommand workspace:copy-path
nmap <Space>y :copy_path<CR>

exmap outline obcommand outline:open
nmap <Space>o :outline<CR>
```

* `<Space>y` → copy file path of current note.
* `<Space>o` → open outline view.

---

## 11. Duplicate Folding Mappings

```vim
exmap unfoldall obcommand editor:unfold-all
nmap zR :unfoldall<CR>

exmap foldall obcommand editor:fold-all
nmap zM :foldall<CR>

exmap toggle_fold obcommand editor:toggle-fold
nmap za :toggle_fold<CR>
```

(Same as section 5, repeated for consistency).

---

## 12. Workspace Management

```vim
exmap close_others obcommand workspace:close-others
nmap <Space>q :close_others<CR>
```

* `<Space>q` → close all notes except current one.

---

## 13. Clipboard Integration

```vim
set clipboard=unnamed
```

* Makes yanks and deletes copy to the system clipboard (not just Vim registers).

---

## 14. Commented Out Options

```vim
" exmap toggle_sidebar obcommand app:toggle-left-sidebar
" nmap <Space>e :toggle_sidebar<CR>
" nmap <Space>l :toggle_sidebar<CR>

" set scrolloff=8

" exmap back obcommand app:go-back
" nmap <C-o> :back<CR>
" exmap forward obcommand app:go-forward
" nmap <C-i> :forward<CR>
```

* Toggle sidebar (`<Space>e`) is disabled.
* `scrolloff=8` (always keep 8 lines above/below cursor) is commented out.
* Back/forward navigation with `Ctrl+O` and `Ctrl+I` is disabled here.

---

# ✅ Summary

This Mini Vimrc setup gives you:

* **Escape with jk/jj/kj**.
* **Better navigation** for wrapped lines.
* **Centered scrolling and searching**.
* **Powerful folding** mapped to Vim’s `z` keys.
* **Leader key (`Space`) shortcuts** for search, replace, theme switching, quick switch, outline, linter, Zen mode, etc.
* **Clipboard integration** with your system.

---

Would you like me to also create a **simplified Markdown “cheatsheet” table** (like `Key → Action`) so you can quickly glance at what each mapping does without reading all the detail?

for simple command check [[1d Vim Binding]].