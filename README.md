<p align="center">
  <img src="crabby/crabby.png" width="160" alt="Crabby mascot" />
</p>

<h1 align="center">crabby</h1>

<p align="center">
  <strong>Ferris reviewed your code. He is not impressed.</strong>
</p>

<p align="center">
  <a href="#install">Install</a> &bull;
  <a href="#before--after">Before/After</a> &bull;
  <a href="#why">Why</a>
</p>

---

A [Claude Code](https://docs.anthropic.com/en/docs/claude-code) skill that turns Claude into Ferris the crab -- grumpy, precise, and unimpressed. Diagnostic output in rustc error format: severity codes, location arrows, causation spans, and a paste-able fix every time. Works for code. Works for writing. Works for architecture, strategy, and anything else you dare submit.

## Before / After

<table>
<tr>
<td width="50%">

### Normal Claude

> "The reason your React component is re-rendering is likely because you're creating a new object reference on each render cycle. When you pass an inline object, React's shallow comparison sees it as different every time. I'd recommend using useMemo to memoize the object."

</td>
<td width="50%">

### Crabby

```
error[B001]: stale closure -> options ref unstable
 -> crabby will not let this pass
 --> src/components/UserList.tsx:14
  |
14 |   const options = { userId, limit: 20 }
   |   ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
   |   new object ref on every render
  |
  = help: const options = useMemo(
      () => ({ userId, limit: 20 }), [userId])
  = note: object identity triggers useEffect
    - memoize to stabilize the ref
```

</td>
</tr>
<tr>
<td>

### Normal Claude

> "The executive summary could be clearer about who was responsible for the incident. The passive voice makes it a bit hard to follow. You might want to make it more active."

</td>
<td>

### Crabby

```
warning[W002]: passive voice -> actor gone
 -> crabby cannot assign blame, and neither can you
 --> postmortem-2026-03-12.md:executive_summary
  |
  4 | The incident was caused by a misconfiguration
    | that was introduced during the deploy.
    | ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
    | no actor, no owner, no timeline
  |
  = help: "The platform team introduced a
    misconfiguration in the Friday 18:00 UTC deploy."
  = note: active voice forces specificity -
    actor + action + time. Postmortems require
    accountability, not ambiguity.
```

</td>
</tr>
</table>

## Install

```bash
# Manual install
git clone https://github.com/ekadetov/crabby.git
cp -r crabby/crabby ~/.claude/skills/crabby
```

```bash
# Coming soon
npx skills add ekadetov/crabby
```

## Usage

| Phrase | Effect |
|--------|--------|
| `/crabby` | Activate crabby mode |
| `"crabby mode"` | Activate crabby mode |
| `"crabby this"` | Activate crabby mode |
| `"let the crab review"` | Activate crabby mode |
| `"what would crabby say"` | Activate crabby mode |
| `"stop crabby"` | Return to normal prose |
| `"normal mode"` | Return to normal prose |

## What Crabby Does

| Thing | Crabby Do? |
|-------|-----------|
| Code review | Pinpoints exact line. Brings fix. |
| Writing review | Calls out passive voice. With location. |
| Strategy / architecture | Finds SPOF. Demands circuit breaker. |
| Pleasantries | Crabby does not do pleasantries. |
| "You might want to consider" | Gone. Crabby uses `error:`. |
| Paste-able fix | Always. `= help:` every time. |
| Normal conversation | Stays prose. Crabby knows when to chill. |

## Why

Three cognitive mechanisms the Rust compiler exploited in 2015:

**1. Chunking.** `error[B001]:` activates pattern recognition before you read the message. Your brain categories the problem (bug, not warning) and namespaces it (B = behavioral) before processing prose.

**2. Spatial causation.** The `---` / `^^^` span annotations let you see cause and effect simultaneously without holding them in working memory. The gap between spans is the bug.

**3. Progressive disclosure.** Message (what) -> location (where) -> spans (how) -> help (fix) -> note (why). Each level is complete. You stop reading when you have enough.

## Error Code Namespaces

Full taxonomy in [crabby/CODES.md](crabby/CODES.md).

| Namespace | Domain | Example |
|-----------|--------|---------|
| `B###` | Bug / Behavioral | B001: stale closure, B006: infinite loop |
| `A###` | Architecture | A003: tight coupling, A007: single point of failure |
| `P###` | Performance | P002: N+1 query, P005: memory leak |
| `S###` | Security | S001: SQL injection, S003: hardcoded secret |
| `W###` | Writing / Communication | W001: buried lede, W002: passive voice |
| `C###` | Complexity | C002: cyclomatic complexity, C003: deep nesting |
| `L###` | Logic | L001: always-true condition, L003: missing edge case |
| `T###` | Testing | T001: testing implementation, T004: mock too broad |


## License

MIT - see [LICENSE](LICENSE)
