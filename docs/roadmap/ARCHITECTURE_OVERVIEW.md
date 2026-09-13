# Architecture Overview

## Principle
Police Service - отдельный application layer поверх существующих источников. Legacy не переделывается глобально; различия схем скрываются за adapters.

```text
React UI
  -> Application Services
    -> Repository Interfaces
      -> Adapters
        -> PoC storage / legacy corporate sources
```

## Domain flow
```text
PoliceTrip 1:N TripParticipant
TripParticipant -> Driver -> Contacts
TripParticipant -> Assignment(date) -> Vehicle/Board -> Responsible Manager
```

## Routing rule
1. Участники группируются по городу.
2. Для каждого города вычисляется самое раннее время записи.
3. Города сортируются по этому времени.
4. При равенстве - по названию города.
5. После выбора города выводятся все его участники.
6. Внутри города сортировка по времени, затем по имени.

## Departure rule
`departure = earliest appointment in trip - 90 minutes`.

## Decision branch
- assignment найден -> board -> manager -> manager message;
- assignment не найден -> contacts -> driver message.

## Anti-Corruption Layer
Legacy column names, mixed values and inconsistent source schemas remain inside infrastructure mappers. UI и application services работают с clean domain contracts.