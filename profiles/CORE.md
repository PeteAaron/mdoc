# MDDoc Core Profile (v0.1 Draft)

## 1. Purpose

The Core profile is the default general-purpose profile for MDDoc.

It aims to:
- stay lightweight
- stay readable
- remain close to Markdown
- provide enough structure for basic validation and conversion

## 2. Interpretation Rules

### 2.1 Headings

Headings define sections.

Implicit heading IDs are allowed.

### 2.2 Lists

Lists retain their normal Markdown meaning unless explicitly annotated.

### 2.3 Tables

Tables are interpreted as tables.

Referenced tables SHOULD have explicit IDs.

### 2.4 Code blocks

Fenced code blocks are interpreted as code/listing blocks.

Referenced code blocks SHOULD have explicit IDs.

## 3. Semantic Annotation in Core

Semantic fences are optional.

They are recommended for:
- note
- warning
- tip
- definition
- figure

They are not required for ordinary document structure.

## 4. Reference Rules

Core references may target:
- explicit IDs
- heading paths
- unique implicit heading matches

Explicit IDs are preferred for stable long-lived documents.

## 5. Required Metadata

No fields are universally required beyond validity.

Recommended:
- `title`
- `author`
- `date`
- `version`
- `profile: core`

## 6. Core Best Practices

- use descriptive headings
- avoid excessive duplicate headings
- assign IDs to anything likely to be referenced repeatedly
- use semantic fences only for genuinely special content
