# Hiisi Translations

This repository contains UI translations for the Hiisi language learning app.

## Format

Translations are stored as S-expressions in `.lisp` files, keyed by keywords.

## Structure

```
i18n/
├── translations.lisp    # Translation loader and accessor
├── en.lisp              # English (base language)
├── fi.lisp              # Finnish
├── cs.lisp              # Czech
└── ...                  # Other languages
```

## Usage

Each language file exports an alist keyed by keywords:

```lisp
((:app-title . "Hiisi")
 (:nav-translate . "Translate")
 (:nav-review . "Review")
 ...)
```
