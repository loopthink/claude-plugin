---
name: query-data
description: Query databases, CRMs and internal APIs through Loopthink tools correctly and safely — choosing get vs query vs scan, paginating, joining across servers, and handling masked fields. Use when answering a question with data from Loopthink tools, or when a Loopthink query returns too much, too little, or masked output.
---

# Query data through Loopthink

Loopthink tools front real production systems. A careless call is a full table
scan against someone's live database, so pick the narrowest tool that can answer
the question.

## Pick the right access pattern

1. **`get`** — you have the full primary key. One record, cheapest, always
   prefer it.
2. **`query`** — you have a partition key or an indexed field. Bounded, fast.
3. **`scan`** — you have neither. Reads the whole table. Use it only for genuinely
   unbounded questions ("how many X are there"), and say so in your answer when
   the result may be partial.
4. **Authored tools** — a curated statement written by a workspace admin. When one
   matches the question, prefer it over assembling the same answer from `scan`:
   it is bounded, typed, and encodes the business definition the workspace agreed
   on.

For CRM servers, a `search_*` tool with a filter is the `query` equivalent; use it
rather than listing and filtering client-side.

## Volume

Results come back through the model's context, so treat every call as expensive:

- Filter server-side. Never pull a table and filter in your head.
- Ask for the fields you need when the tool supports projection.
- Paginate rather than raising a limit — follow the cursor or token the tool
  returns instead of asking for one huge page.
- Stop and tell the user when a question needs more data than is reasonable to
  pull, and propose a narrower one.

## Joining across servers

There is no server-side join between MCP servers. To combine, for example, orders
from a database with accounts from a CRM: pull the narrow side first, collect the
join keys, then look up the other side by key. Do not scan both sides.

Say explicitly in your answer that you joined client-side across two systems —
the numbers are only as consistent as the moment you pulled each half.

## Masking and read-only

- Fields returned as `***`, a pseudonym, or omitted are covered by a masking rule
  applied server-side before the result left Loopthink. Report the value as
  masked. Do not attempt another tool, another server, or a different phrasing to
  recover it, and do not ask the user to paste it in.
- Tools are read-only unless a workspace admin explicitly enabled writes. Before
  calling anything that looks mutating, confirm from its description that it is
  meant to write, and confirm the action with the user first.

## Reporting results

State which tools you called and any bound you hit (a scan that was truncated, a
page limit, a client-side join). A number without its provenance is not usable in
the kind of workspace that installs a governance layer in the first place.
