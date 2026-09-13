# Architecture Decisions

## ADR-001 - Reuse legacy sources
Status: Accepted. Existing sources remain source of truth; Police uses adapters and changes legacy only when a blocker exists.

## ADR-002 - Trip 1:N Participants
Status: Accepted. One trip contains one or many participants. An individual trip is a trip with one participant.

## ADR-003 - City route ordering
Status: Accepted. Cities sort by earliest appointment; equal time -> alphabetical order; then process the entire city before moving to the next.

## ADR-004 - Messages are derived in MVP
Status: Accepted. Manager/driver text is generated on demand and is not a persistent business entity until send/confirm/retry lifecycle exists.

## ADR-005 - Repository adapters isolate platforms
Status: Accepted. Application depends on repository interfaces; PoC/corporate platforms implement adapters outside the domain.

## ADR-006 - Business identifiers are not automatically technical PKs
Status: Accepted. Driver business code and board code may be unique business identifiers, while internal entities may use immutable technical IDs.

## ADR rule
Если решение меняется, старое не удаляется задним числом. Создается новый ADR со статусом `Supersedes ADR-XXX` и описанием причины.