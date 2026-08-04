---
title: "Strumenti AI nel tema Three"
type: guide
tags: [ai-tooling, graphify, headroom, caveman, tema]
created: 2026-08-03
updated: 2026-08-03
qmd: "graphify headroom caveman tema Three indicizzazione scaffold"
related:
  - ../../../Modules/Xot/docs/ai-tooling-stack.md
  - ../../Zero/docs/no-ai-tool-scaffold-dirs.md
---

# Strumenti AI nel tema Three

Canonico dello stack (versioni, installazione, configurazione):
[Xot — ai-tooling-stack](../../../Modules/Xot/docs/ai-tooling-stack.md).

## graphify

Three è oggi minimale: un solo blade e un file PHP sotto `resources/`. Un grafo dedicato non serve
— finché il tema resta a questa dimensione, la lettura diretta dei file costa meno
dell'estrazione. Se il tema cresce:

```bash
graphify update laravel/Themes/Three/resources
```

## La trappola: scaffold nel tema

Vale anche qui: `graphify update <path>` scrive `<path>/graphify-out/`, cioè cache dentro un
sotto-albero che è anche repo Git indipendente. Vedi
[no-ai-tool-scaffold-dirs](../../Zero/docs/no-ai-tool-scaffold-dirs.md) e la regola canonica
[module-theme-root-cleanup](../../../../docs/wiki/rules/module-theme-root-cleanup.md).

Mitigazione applicata: `graphify-out/` e `.headroom/` sono nel `.gitignore` del tema.

## headroom e caveman

Nessuna configurazione per tema. Non tenere caveman attivo quando si scrivono testi destinati
all'interfaccia.
