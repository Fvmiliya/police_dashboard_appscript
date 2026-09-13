# Test Strategy and Definition of Done

## Test pyramid

### Unit tests
Pure business logic: departure calculation, city grouping, alphabetical tie-break, participant sorting, message generation, board normalization and date interval rules.

### Contract tests
Different legacy source schemas must return the same clean domain contracts.

### Integration tests
Storage/platform adapters are tested against fixtures or an authorized test environment.

### UI smoke tests
Create trip, add multiple participants, open day/range, see on-vehicle state, see off-vehicle state, copy generated text.

## Mandatory edge cases
Missing driver ID, driver not found, no assignment, trainee/replacement roles, duplicate manager mapping for one board, missing manager, missing contacts, boundary `validTo`, empty participants, same earliest time in two cities.

## Definition of Done
A feature is done when it works end-to-end, business logic is outside UI/infrastructure, platform APIs are isolated, new business rules have tests, loading/empty/error states are handled, ambiguous data is never silently accepted, acceptance criteria are checked, docs are updated and `main` remains runnable after merge.

For v1.0 additionally: security review, permissions, UAT, rollback plan, monitoring and production deployment procedure.