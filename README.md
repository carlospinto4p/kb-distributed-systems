# kb-distributed-systems

A small, sourced knowledge base on distributed systems, written as linked
markdown notes. It covers how machines that fail and lose messages still
order events, agree on a value and keep copies of data in step.

It is also the example knowledge base for
[vademo](https://github.com/carlospinto4p/vademo), an Android app for reading
and editing knowledge-base repositories: open the folder to browse the notes, follow the
`[[links]]`, and read the `sources/` notes behind them.

## What is in it

| Folder | Notes |
|--------|-------|
| `concepts/` | Happened-before, logical and vector clocks, quorums, replicated state machines, consistency models, the CAP theorem |
| `consensus/` | The consensus problem, the FLP impossibility result, Paxos, Raft |
| `systems/` | Dynamo, Spanner |
| `questions/` | Open questions the notes cannot answer yet |
| `sources/` | One note per paper or page the claims rest on |

Start at [`index.md`](index.md).

## How the notes are kept honest

Every claim about the outside world is tied to a source note, an inline
citation, or an `(unverified)` marker. Where a source could not be read, the
note says so and records the gap instead of filling it from memory. The full
rules are in [`.claude/rules/knowledge-base.md`](.claude/rules/knowledge-base.md).

The notes are summaries with short quotes, written to be checked against the
originals, not a replacement for them.

## Licence

MIT, see [`LICENSE`](LICENSE).
