---
title: "Glossario di dominio Theme Three"
type: glossary
owner: Three
updated: 2026-11-24
qmd: "glossario Theme Three blocco links grid tema non registrabile"
---

# Glossario di dominio Theme Three

Three contiene un solo elemento di presentazione; il glossario riporta solo ciò che è verificato. Percorsi relativi a `laravel/Themes/Three/`.

| Termine | Significato | Nel codice |
|---|---|---|
| Blocco `links/grid` | Sezione con titolo, descrizione e griglia di link opzionali, con stili inline; unico file Blade del tema. | `resources/views/components/blocks/links/grid.blade.php` |
| Tema non registrabile | Tema senza `theme.json`, `composer.json`, `package.json`, `vite.config.js`, `app/`, `lang/`, `public/`: non è selezionabile come `pub_theme`. | README del tema, sezione «Scopo e confini»; assenza dei file verificata con `ls` (2026-11-24) |
| Blocco duplicato | Il file `links/grid.blade.php` è identico (stesso md5) in One, Three e Zero. | `laravel/Themes/{One,Three,Zero}/resources/views/components/blocks/links/grid.blade.php` |
| Release automatica | Configurazione semantic-release del repository del tema. | `.releaserc.json`, `README.md` |
