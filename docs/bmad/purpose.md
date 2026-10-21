---
title: "Three — scopo del tema e come raggiungerlo meglio"
type: concept
document_type: concept
theme: Three
status: active
version: 1.0.0
language: it-IT
created: 2026-09-09
updated: 2026-09-09
tags: [tema, purpose, guscio, documentazione-senza-codice, decisione-aperta]
qmd: "tema Three scopo guscio 53 documenti un solo blade components blocks links nessuna pipeline nessun theme.json decidere se esiste"
issues:
  # DA CREARE — nessun numero inventato. gh issue create --repo $(git remote -v)
  - "https://github.com/provtv/theme_three_fila5/issues/"
discussions:
  - "https://github.com/provtv/base_ptv_fila5/discussions/"
related:
  - ../../Zero/docs/purpose.md
  - ../../One/docs/purpose.md
  - ../../../../docs/epics.md
maintainer: Laraxot
license: project-internal
---

# Three — perché esiste

## Lo scopo in una frase

**Three oggi non è un tema: è una cartella di documentazione con dentro un componente.**
Cinquantatré file `.md` e **un** `.blade.php`.

Questo file esiste per dire quel fatto, perché è l'unica cosa vera che si può scrivere sul
tema senza inventare.

## L'evidenza

| Fatto | Misura |
|---|---|
| Superficie | **1** `.blade.php` — `resources/views/components/blocks/links/…` |
| Codice PHP | **0** |
| CSS / JS | **0** |
| Documentazione | **53** file `.md` |
| Si dichiara tema? | no: **manca `theme.json`** |
| Pipeline di build | assente: nessun `vite.config.js`, `package.json`, `tailwind.config.js` |
| Traduzioni | assenti: nessun `lang/` |
| È il tema attivo? | no — `config('xra.pub_theme') === 'Zero'` |

Il contenuto reale fuori da `docs/`, per intero:

```
.gitattributes  .gitignore  .releaserc.json  _theme_three.code-workspace
README.md  CHANGELOG.md  .git/
resources/views/components/blocks/links/…  (un blade)
```

Rapporto documentazione/codice: **53 a 1**.

## Come raggiungerlo meglio

Non c'è un «meglio» finché non si risponde a una domanda, e non è una domanda tecnica.

### La decisione, e le sue tre uscite

**A. Three è un tema in preparazione.** Allora gli servono `theme.json`, la pipeline di build e
i layout — cioè la stessa dotazione che ha Zero. E soprattutto **una ragione di esistere
diversa da Zero e One**: oggi quei due differiscono già solo per due file, un terzo fork senza
un'identità visiva propria aggiunge lavoro di allineamento e nient'altro.

**B. Three è un archivio di documentazione.** Allora i 53 `.md` vanno dove appartengono — al
modulo o al tema che possiede l'argomento — e la cartella tema sparisce. La regola
`modular-bmad-story-policy` è esplicita: non si creano temi o moduli per ospitare
documentazione.

**C. Three è un residuo.** Allora va marcato tale, con la data e il perché, e i suoi 53
documenti vanno rediretti prima che qualcuno li usi come fonte.

### Cosa non fare nel frattempo

**Non aggiungere altri `.md` qui.** Ogni documento in più aumenta il costo dell'uscita B e
rende più credibile un tema che non esiste. Fra i 53 ce ne sono già di indistinguibili da
quelli di Zero e One: chi cerca «come si fa X nel tema» può trovare la risposta di un tema che
non viene servito.

## Confini

Gli stessi degli altri due temi: la logica di dominio sta nei moduli, le classi base Filament
in `Xot`, le traduzioni di dominio nei `lang/` dei moduli. Qui, per ora, non c'è nulla che
possa violarli — ed è il punto.

## Collegamenti

- [Zero — scopo](../../Zero/docs/purpose.md) — il tema effettivamente servito
- [One — scopo](../../One/docs/purpose.md) — il fork di Zero, a due file di distanza
- [docs/epics.md](../../../../docs/epics.md) — la Story Storage Policy, che indica un terzo tema ancora
