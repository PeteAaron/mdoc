# MDOC Document Model (v0.1 Draft)

## 1. Overview

MDOC defines a canonical document model independent of rendering.

Source text is parsed into:
- metadata
- block structure
- inline structure
- identifiers
- references
- semantic roles

This model is the source of truth for:
- validation
- AI interpretation
- export and rendering
- document transformations

## 2. Model Principles

The model must be:
- explicit
- hierarchical
- deterministic
- profile-aware
- renderable

## 3. Root Object

The root object is `Document`.

### 3.1 Fields

| Field | Type | Description |
|---|---|---|
| `metadata` | map | Parsed YAML front matter |
| `profile` | string/null | Active profile |
| `blocks` | list | Ordered top-level block sequence |

## 4. Block Types

### 4.1 Section

A heading-defined structural unit.

Fields:
- `level`
- `title`
- `identifier`
- `children`

A section may derive its identifier implicitly from heading text and hierarchy unless overridden by explicit ID.

### 4.2 Paragraph

A paragraph block.

Fields:
- `inlines`
- `identifier` (optional)
- `semantic_role` (optional)

### 4.3 List

Represents ordered or unordered lists.

Fields:
- `ordered`
- `items`
- `semantic_role` (optional)

### 4.4 ListItem

Represents an item within a list.

Fields:
- `blocks`
- `identifier` (optional)
- `semantic_role` (optional)

In some profiles, list items may represent clauses, steps, controls, or requirements.

### 4.5 Table

Represents tabular data.

Fields:
- `header`
- `rows`
- `identifier` (optional)
- `semantic_role` (optional)

### 4.6 CodeBlock

Represents fenced code content.

Fields:
- `language`
- `content`
- `identifier` (optional)
- `semantic_role` (optional)

### 4.7 BlockQuote

Represents blockquoted content.

Fields:
- `blocks`
- `identifier` (optional)
- `semantic_role` (optional)

Profiles may interpret some block quotes as notes or advisory content.

### 4.8 SemanticBlock

Represents explicitly fenced semantic content using `::type`.

Fields:
- `type`
- `identifier` (optional)
- `attributes`
- `blocks`

SemanticBlock is used when explicit semantic meaning cannot be inferred safely from native structure.

## 5. Inline Types

### 5.1 Text
Plain text.

### 5.2 Emphasis
Italic, bold, or other CommonMark emphasis forms.

### 5.3 InlineCode
Inline code span.

### 5.4 Link
Normal hyperlink.

### 5.5 Reference
Cross-reference target.

Fields:
- `target`
- `resolved_target`
- `reference_type` (optional)

## 6. Identifier Model

Identifiers are stable anchors.

### 6.1 Explicit identifiers

Declared directly by author using `{#id}`.

### 6.2 Implicit identifiers

Generated from headings.

### 6.3 Identifier constraints

Identifiers must be:
- unique within document scope
- stable enough for reliable referencing
- independent of presentation numbering

## 7. Reference Model

A reference resolves to a specific target node.

### 7.1 Reference resolution inputs

A reference may contain:
- explicit ID
- heading path
- typed profile target

### 7.2 Resolution outcome

A valid reference resolves to exactly one model node.

If resolution yields:
- zero targets → unresolved
- multiple targets → ambiguous

both are validation failures.

## 8. Semantic Role Model

Semantic role may arise from:

### 8.1 Native structure
Examples:
- heading → section
- ordered list → ordered structure
- fenced code → code listing

### 8.2 Profile inference
Examples:
- ordered legal list item → clause
- technical referenced code block → listing

### 8.3 Explicit annotation
Examples:
- `warning`
- `definition`
- `figure`
- `equation`
- `annex`

## 9. Profile-aware Interpretation

Profiles do not change core grammar.

Profiles change:
- how blocks are interpreted
- which blocks must have IDs
- which references are valid
- which metadata is required
- which semantic roles are required

## 10. Rendering Model

Renderers consume the canonical model and generate:
- numbering
- labels
- formatting
- styles
- captions
- links
- output-specific structure

Numbering is derived from structure and role, not from source identity.

## 11. AI and Machine Consumption

The canonical model is intended to support:
- deterministic parsing
- structured extraction
- semantic search
- reference graph construction
- transformation to JSON or other machine-readable forms

Future versions may standardize a canonical JSON representation.
