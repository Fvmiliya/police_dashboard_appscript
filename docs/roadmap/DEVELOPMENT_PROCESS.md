# Development Process

Используем практичную комбинацию Agile, Vertical Slice Development, Docs-as-Code, ADR, GitHub Flow, Conventional Commits и Semantic Versioning.

## Vertical slices
Каждая версия должна давать законченный пользовательский сценарий end-to-end. Мы не строим месяц repositories отдельно от UI. Для каждой фичи проходим полный путь: domain -> application service -> repository -> API -> UI -> tests.

## Docs-as-Code
Архитектура, version specs, решения и test strategy живут в Git рядом с кодом. Документация входит в Definition of Done.

## GitHub Flow
`main` должен оставаться запускаемым. На задачу создается короткоживущая ветка, затем PR, review, merge, удаление ветки.

Примеры: `feat/v0.2-route-ordering`, `fix/manager-conflict`, `docs/v0.3-contracts`.

## Conventional Commits
- `feat(trips): add multi-driver trip creation`
- `fix(route): use city name as tie breaker`
- `test(assignments): cover replacement driver`
- `docs(adr): document adapter decision`

## Semantic Versioning
Релизные теги: `v0.1.0`, `v0.2.0`, ... `v1.0.0`. Patch-релиз меняет только исправления без изменения feature contract.

## Definition of Ready
Перед разработкой понятны пользовательский результат, acceptance criteria, нужные источники данных и blockers.

## Version gate
Перед закрытием версии: scope review -> technical review -> implementation -> automated tests -> manual acceptance -> demo -> tag/release notes.