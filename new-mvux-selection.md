---
name: mvux-selection
description: Implement item selection in MVUX lists. Use when tracking selected items in ListView/GridView, implementing single or multi-selection, or reacting to selection changes.
metadata:
  author: uno-platform
  version: "2.0"
  category: uno-platform-mvux
---

# MVUX Selection — Agent Skill

This skill guides you through implementing item selection tracking in MVUX lists, from single selection to multi-selection.

## When to Use

- Tracking the selected item(s) in a `ListView`, `GridView`, or other selector
- Implementing single-item selection with `IState<T>`
- Implementing multi-item selection with `IState<IImmutableList<T>>`
- Reacting to selection changes in the Model
- Manual (programmatic) selection of items

## Workflow

### Step 1: Fetch the Selection Documentation

Search for and fetch the selection documentation:

```
uno_platform_docs_search("MVUX selection Selection method IListFeed IListState")
```

Primary documentation pages:
- **Selection Reference**: `https://platform.uno/docs/articles/external/uno.extensions/doc/Learn/Mvux/Advanced/Selection.html`
- **Selection How-To**: `https://platform.uno/docs/articles/external/uno.extensions/doc/Learn/Mvux/Walkthrough/Selection.howto.html`
- **Selection in Chefs App**: `https://platform.uno/docs/articles/external/uno.chefs/doc/mvux/Selection.html`

Fetch the reference page:

```
uno_platform_docs_fetch("https://platform.uno/docs/articles/external/uno.extensions/doc/Learn/Mvux/Advanced/Selection.html")
```

### Step 2: For How-To Walkthroughs

For step-by-step examples:

```
uno_platform_docs_fetch("https://platform.uno/docs/articles/external/uno.extensions/doc/Learn/Mvux/Walkthrough/Selection.howto.html")
```

This covers single selection, multi selection, checking selection from commands, and programmatic selection.

### Step 3: Understand Selection Patterns

From the fetched docs:
- **Single selection**: `.Selection(selectedState)` where `selectedState` is `IState<T?>`
- **Multi-selection**: `.Selection(selectedStates)` where `selectedStates` is `IState<IImmutableList<T>>`
- **Manual selection**: Use `IListState<T>` instead of `IListFeed<T>` for programmatic item selection

### Step 4: For Selection with Commands

If the user needs to use the selected item in a command (e.g., "Edit" button):

```
uno_platform_docs_search("MVUX selection command check current selected item button")
```

## Key Principles (Stable)

- Use `.Selection(state)` operator on `IListFeed<T>` or `IListState<T>` to enable selection tracking
- Single selection: `IState<T?>` holds the selected item
- Multi-selection: `IState<IImmutableList<T>>` holds selected items
- The `ListView` SelectionMode must be set appropriately (Single, Multiple, Extended)
- Selection sync happens automatically between the UI control and the state
- For programmatic/manual selection, use `IListState<T>` (not `IListFeed<T>`)

## Related Skills

- `mvux-listfeed` — Read-only collections with selection
- `mvux-liststate` — Mutable collections with selection
- `mvux-commands` — Commands that use selected items
