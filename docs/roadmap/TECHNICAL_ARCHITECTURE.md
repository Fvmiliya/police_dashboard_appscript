# Technical Architecture

## PoC stack
- TypeScript
- React + TypeScript
- Google Apps Script V8
- Google Sheets as temporary storage
- clasp
- esbuild or Vite build step
- unit tests for pure business logic

## Target structure
```text
src/
  domain/
  application/
  repositories/interfaces/
  infrastructure/google/
  infrastructure/sharepoint/
  infrastructure/mappers/
  server/gas/
  web/
  shared/
tests/
  unit/
  contract/
  integration/
docs/
  roadmap/
  versions/
  adr/
```

## Dependency direction
`UI -> Application -> Domain`.
Infrastructure implements repository interfaces and depends inward. Domain never imports Google/SharePoint APIs.

## Platform isolation
No `SpreadsheetApp` inside domain/application. React business components do not call `google.script.run` directly; they use a typed API adapter.

## Error model
Use explicit errors/results for identity conflicts, data-quality conflicts, missing manager, missing contacts and repository failures. Never silently choose a random legacy record when data is ambiguous.