# mdoc

**mdoc** is a structured, text-readable document format designed for humans, AI and software.

It builds on the accessibility of Markdown while introducing the structure needed for richer, document-grade workflows. The goal is to make documents easy to read and edit as plain text, while also making them reliable to parse, transform, and render into polished outputs such as Word, Pages, PDF, and other publishing formats.

## Why mdoc?

Markdown made text-based writing simple and portable, but it was not designed to fully support the needs of structured documents, intelligent systems, or high-quality document production.

mdoc aims to provide a format that is:

- readable in raw text
- understandable by software and AI
- compatible with existing Markdown workflows where possible
- structured enough to support document semantics, references, and transformations
- suitable as a source format for high-quality rendered outputs

## Principles

- **Text first** — documents should remain readable and editable in plain text
- **Structured by design** — meaning and document semantics should be explicit
- **Machine-friendly** — files should be easy for software and AI systems to interpret reliably
- **Backwards-aware** — compatibility with Markdown should be preserved wherever practical
- **Output-flexible** — the same source should be usable for rich export to other formats

## What mdoc is for

mdoc is intended to serve as a source document format for:

- long-form writing
- specifications
- operational documentation
- reports
- knowledge assets
- AI-assisted document workflows
- multi-format publishing pipelines

## Example

```md
# Authentication {#auth}

Authentication is required before accessing protected resources.

See [[auth]] for more details.

```

## Goals

Create a structured text format that remains easy to read and edit
Preserve compatibility with Markdown where possible
Support explicit document semantics such as identifiers, references, and structure
Make documents easier for AI and software to process correctly
Enable reliable conversion into high-quality output formats such as Word, Pages, PDF, and web formats
Support a future tooling ecosystem for parsing, validation, rendering, and transformation

## Non-goals

Reproducing every visual feature of traditional word processors directly in source text
Making source files visually complex or markup-heavy
Locking the format to a single editor, platform or rendering tool
Optimising for styling-first authoring over structure-first authoring

## File extension

.mdoc

## Proposed MIME type

text/markdown+mdoc

## Status

Early concept. The format, syntax and tooling model are still being defined.

## Vision

mdoc is intended to be a durable document source format: simple enough to read as text, structured enough for machines to understand, and powerful enough to produce professionally formatted outputs.

## Contributing

This project is at an early stage. Feedback, discussion, and collaboration are welcome.

## Licencing

mdoc will be an open specification released under the Apache 2.0 License. The goal is to enable broad adoption across tools, platforms and ecosystems.
