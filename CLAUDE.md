# C# Code Style

Follow them for all C# code.

## Naming

| Element | Convention | Example |
|---|---|---|
| Types, namespaces, classes, structs, enums, delegates | PascalCase | `MatchmakingService` |
| Interfaces | `I` + PascalCase | `IEquatable` |
| Type parameters | `T` + PascalCase | `TValue` |
| Methods, properties (public), local functions | PascalCase | `GetPlayer` |
| Properties (private) | `_` + PascalCase | `_CachedState` |
| Private instance fields | `_` + PascalCase | `_playerCount` → `_PlayerCount` |
| Private static fields | `_` + PascalCase | `_Instance` |
| Private static readonly fields | `_` + PascalCase | `_DefaultConfig` |
| Non-private instance fields | camelCase or PascalCase | `playerCount` |
| Non-private static readonly | PascalCase | `MaxPlayers` |
| Constants (private) | `_` + SCREAMING_SNAKE_CASE | `_MAX_RETRIES` |
| Constants (non-private) | SCREAMING_SNAKE_CASE | `MAX_RETRIES` |
| Enum members | PascalCase | `PendingReview` |
| Parameters, locals, local constants | camelCase | `playerId` |
| Unity serialized fields | `_` + PascalCase (not inspected) | `_Prefab` |

Auto-detected naming rules are **disabled** — apply the rules above explicitly, don't infer from surrounding code.

## Formatting

- Multiline constructs are **aligned**: LINQ queries, call chains, expressions, base-type lists, `for` statements, parameters, multiple declarations, type-parameter lists and constraints, tuple components.
- **Introduce alignment** (vertical/column alignment) for consecutive: assignments, comments, fields, invocations, methods, properties, variables, nested ternaries, switch expressions, switch sections.
- **Outdent** binary operators, commas, and dots (operators go at line start when wrapping).
- No blank lines after block statements.
- Empty blocks: braces together on the same line (`{ }`).
- Preprocessor `#if` and other preprocessor directives use usual indentation.
- Do **not** auto-insert XML doc comment stubs.

## Code

- `CheckNamespace` (namespace must match folder): **disabled** — namespaces need not match folder structure - usually one global namespace per project.
