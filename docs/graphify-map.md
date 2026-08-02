# Three Theme — Mappa Graphify

**Versione:** 1.0.0 | **Tema:** Three | **Data:** 2026-08-02

---

## 📌 Cosa fa il tema Three

Il tema **Three** fornisce:
- Tema UI dedicato per layout compatti e sezioni specializzate

---

## 🏗️ Architettura Essenziale Tema

### Entry Points Visivi

| Tipo | File | Path |
|------|------|------|
| **View Layout** | `components/blocks/links/grid.blade.php` | `resources/views/components/blocks/links/grid.blade.php` |
| **Component** | `blocks/links/grid.blade.php` | `resources/views/components/blocks/links/grid.blade.php` |

### Dependencies (Incoming)

```
UI Module → Theme Three
```

### Dependencies (Outgoing)

```
Theme Three → UI Module
```

---

## 📊 Grafo Locale (Query Rapide Tema)

### Scoprire Componenti Tema

```bash
graphify query "Three theme components and layouts"
```

### Tracciare Dipendenze CSS/Vite

```bash
graphify query "Three theme CSS assets and dependencies"
```

---

## 🎯 Task Comuni Tema + Graphify

### Task 1: Personalizzazione Layout e Componenti

**Domanda Graphify:**
```bash
graphify query "Three component architecture and Blade structure"
```

**Workflow:**
1. Ispeziona views in `resources/views/components/`
2. Modifica o crea nuovo componente Blade
3. Verifica la resa visiva

---

## 🚀 Comandi Rapidi Tema

```bash
# Esplora struttura tema
graphify query "Three theme components"

# Dipendenze
graphify query "modules using Three theme"
```

---

## 📚 Riferimenti

- **Graphify Central:** `docs/graphify-integration.md`
- **Theme Template:** `laravel/themes/GRAPHIFY_THEME_TEMPLATE.md`

---

**Responsabile:** @marco76tv | **Last updated:** 2026-08-02
