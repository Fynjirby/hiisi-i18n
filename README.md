# Hiisi Translations

This repository contains UI translations for the Hiisi language learning app.

## Format

Translations are stored as S-expressions in `.lisp` files, keyed by keywords.

## Structure

```
i18n/
├── en.lisp              # English (base language)
├── fi.lisp              # Finnish
├── cs.lisp              # Czech
└── ...                  # Other languages
```

## File Format

Each language file is a single alist (association list) keyed by keywords:

```lisp
;;; English translations (base language)

(
 ;; Navigation
 (:nav-translate . "Translate")
 (:nav-review . "Review")
 (:nav-dashboard . "Dashboard")

 ;; App title
 (:app-title . "Hiisi")
 (:app-tagline . "Learn languages through translations")

 ;; ... more keys
)
```

## Adding a New Language

1. Copy `en.lisp` to `XX.lisp` (where XX is the ISO 639-1 code)
2. Translate all string values
3. Add metadata keys at the top:
   - `:lang-name` - Language name in that language (e.g., "Suomi" for Finnish)
   - `:lang-flag` - Emoji flag (e.g., "🇫🇮")

## Required Metadata Keys

Each language file should include these keys for the language selector:

```lisp
(:lang-name . "English")  ; Name in the language itself
(:lang-flag . "🇬🇧")       ; Flag emoji
```

## Usage in Code

The `cl/i18n.lisp` module loads these files and provides:

```lisp
;; Get a translation for current language
(tr :nav-translate)  ; => "Translate"

;; With format arguments
(tr :review-progress 5 10)  ; => "Card 5 of 10"

;; Bind language from cookie for a request
(with-i18n
  (tr :app-title))
```
