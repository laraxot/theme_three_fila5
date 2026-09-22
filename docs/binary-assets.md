---
title: "Asset binari"
type: guide
tags: [theme, three, binary, assets]
created: 2026-07-29
updated: 2026-09-01
qmd: "three theme asset binari"
---
# Asset binari

Gli asset binari sono file normali del repository.

Regole:
- non aggiungere filtri o backend di storage esterno in `.gitattributes`;
- non committare file pointer al posto del contenuto reale;
- se un asset manca, recuperare il binario originale e committarlo direttamente;
- prima del push verificare che immagini, font, archivi e PDF siano contenuti reali;
- asset serviti: `public_html/` — [public-path-public-html](./public-path-public-html.md).
