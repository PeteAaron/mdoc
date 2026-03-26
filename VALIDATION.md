# MDOC Validation Rules (v0.1 Draft)

## 1. Purpose

Validation ensures that MDOC documents are:
- structurally coherent
- reference-safe
- profile-conformant
- machine-reliable

A document may be parseable without being valid.

## 2. General Validation Rules

### 2.1 Metadata validity

If front matter is present:
- it MUST be valid YAML
- duplicate keys are invalid
- profile value, if present, MUST name a known profile

### 2.2 Identifier validity

Explicit identifiers:
- MUST be unique within a document
- MUST NOT contain whitespace
- SHOULD use stable semantic names
- MUST NOT rely on rendered numbering as identity

### 2.3 Reference validity

Every reference:
- MUST resolve to exactly one target
- MUST fail if unresolved
- MUST fail if ambiguous

### 2.4 Semantic fence validity

Semantic fences:
- MUST begin with `::type`
- MAY include attributes
- MAY bind to the next block only if unclosed
- MUST close with standalone `::` if used as a container
- MUST preserve unknown types even when validation warns

## 3. Ambiguity Rules

Duplicate headings are allowed.

Ambiguous references are not.

If duplicate headings exist:
- authors MUST disambiguate by path or explicit ID
- profiles MAY allow scoped resolution rules
- if scoped resolution still produces multiple matches, validation fails

## 4. Conformance Levels

### 4.1 Core validity

A Core document is valid if it satisfies:
- general Markdown parsing
- metadata rules
- identifier rules
- reference rules
- any core-specific profile rules

### 4.2 Legal validity

A Legal document is valid only if it satisfies:
- all general validation rules
- all Legal profile rules

### 4.3 Technical validity

A Technical document is valid only if it satisfies:
- all general validation rules
- all Technical profile rules

## 5. Severity Model

Validators SHOULD distinguish:
- error
- warning
- informational notice

Recommended meanings:
- **error** = document is non-conformant
- **warning** = document is valid but risky or weak
- **info** = quality suggestion

## 6. Recommended Warnings

Validators SHOULD warn when:
- implicit heading references are used where explicit IDs would be safer
- duplicate headings occur in highly structured documents
- semantic roles are inferred but not explicit in high-risk contexts
- legal or technical references use weak natural language instead of machine-linked references

## 7. Profile Override Rule

Profiles MAY strengthen validation.

Profiles MUST NOT weaken:
- identifier uniqueness
- reference uniqueness
- core parsing determinism
