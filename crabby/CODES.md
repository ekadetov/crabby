# Crabby Error Codes

Always pick the nearest matching code. Invent sub-codes (e.g. B006) when a new
distinct pattern emerges within a namespace. Keep one-line descriptions tight.

---

## B### - Bug / Behavioral

| Code | Meaning |
|------|---------|
| B001 | Stale closure captures outdated reference |
| B002 | Off-by-one index error |
| B003 | Null / undefined dereference |
| B004 | Async result used before await resolves |
| B005 | State mutation bypasses reconciliation cycle |
| B006 | Infinite loop - termination condition never met |
| B007 | Race condition - shared state written from concurrent paths |

---

## A### - Architecture

| Code | Meaning |
|------|---------|
| A001 | Circular dependency between modules |
| A002 | Business logic leaking into presentation layer |
| A003 | Tight coupling - concrete dependency instead of abstraction |
| A004 | Shotgun surgery - change requires edits across >3 unrelated files |
| A005 | God object accumulating unrelated responsibilities |
| A006 | Missing abstraction boundary - domain concepts exposed at API surface |
| A007 | Single point of failure - no fallback or redundancy path |

---

## P### - Performance

| Code | Meaning |
|------|---------|
| P001 | Unnecessary re-render / recomputation on every cycle |
| P002 | N+1 query - database hit inside loop |
| P003 | Blocking I/O on hot path |
| P004 | Missing index on frequently filtered column |
| P005 | Memory leak - object retained beyond its useful lifetime |
| P006 | Unbounded cache - grows without eviction policy |

---

## S### - Security

| Code | Meaning |
|------|---------|
| S001 | SQL injection - user input interpolated into query |
| S002 | XSS - unsanitized input rendered as HTML |
| S003 | Hardcoded secret in source code |
| S004 | Broken authentication - session or token mismanagement |
| S005 | SSRF - user-controlled URL used in server-side request |
| S006 | Insecure deserialization of untrusted data |

---

## W### - Writing / Communication

| Code | Meaning |
|------|---------|
| W001 | Buried lede - key information appears after supporting detail |
| W002 | Passive voice obscures ownership and causation |
| W003 | Undefined term used before it is explained |
| W004 | Mixed abstraction levels in the same paragraph |
| W005 | Hedging language undermines a clear recommendation |
| W006 | Wall of text - missing visual hierarchy for scannable structure |

---

## C### - Complexity

| Code | Meaning |
|------|---------|
| C001 | Function exceeds single responsibility |
| C002 | Cyclomatic complexity too high - too many branches |
| C003 | Deep nesting reduces readability and testability |
| C004 | Premature abstraction adds indirection without benefit |
| C005 | Magic number / string lacks named constant |

---

## L### - Logic

| Code | Meaning |
|------|---------|
| L001 | Condition always true or always false |
| L002 | Unreachable code path |
| L003 | Missing edge case - boundary condition not handled |
| L004 | Inverted logic - predicate reversed from intended meaning |

---

## T### - Testing

| Code | Meaning |
|------|---------|
| T001 | Test asserts implementation detail, not behavior |
| T002 | Missing negative / error path test |
| T003 | Test shares mutable state across cases |
| T004 | Mock too broad - test passes even when production code is broken |
