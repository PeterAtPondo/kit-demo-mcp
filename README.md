# Kit memory demo · hosted MCP servers

Three live, public, **read-only** MCP servers, each backed by a running
[Kit](https://kit-project.com). Kit is an identity substrate for AI agents:
not another agent, not a memory API, but the durable, local-first self beneath
your tools, holding memory with provenance and context that outlives any
context window, consolidating while it dreams. It has no chat window of its
own; it lives under the ones you already use.
Point your agent at them and ask questions the model cannot answer from
training. No signup; the bearer keys below are deliberately public.

| server | endpoint | what it holds |
|---|---|---|
| Lady Whiskerdown (the Society Papers) | `https://demo-mcp.kit-project.com/mcp` | An invented regency world seen from the ballroom. 118 memories. Half of a mystery. |
| The Area Cat (The Mews) | `https://mews-mcp.kit-project.com/mcp` | The same town from below stairs. 88 memories. The other half. |
| The ballast case file | `https://real-mcp.kit-project.com/mcp` | A real five-year engineering decision (OpenTelemetry Collector's memory ballast), every entry with its GitHub source URL. 65 memories. |

Why fiction: none of it exists in any training corpus, so a correct citation
is provably retrieval. Why the two archives are separate servers: the central
mystery (who leaked the Fluffington affair?) was split across them on purpose;
no single entry states the answer, the full corroborated case assembles only
across both, and your agent is the bridge. Why the real one:
so the same machinery is checkable against the living public record.

## Quickstart

Claude Code:

```bash
claude mcp add --transport http kit-papers https://demo-mcp.kit-project.com/mcp \
  --header "Authorization: Bearer kbr_live_Kh9eO_ZfLldveFf1KXJEEvepfOpdgRqf7KoDDU3rB18"
claude mcp add --transport http kit-mews https://mews-mcp.kit-project.com/mcp \
  --header "Authorization: Bearer kbr_live_UN8-2LUlKmP2uxWQB5vpn-fzkJIuRb5zmq-apQeTU7U"
claude mcp add --transport http kit-case-file https://real-mcp.kit-project.com/mcp \
  --header "Authorization: Bearer kbr_live_ISWsqW39NkqT659FEkQjv0OjJDmyD4O3wx3wcCfA03c"
```

Any MCP client: see [`examples/mcp.json`](examples/mcp.json).

Then tell your agent: *"Call wake on each server, then work out who leaked the
Fluffington affair, and cite every step."* Or the real-world flagship:
*"Should we still use the memory_ballast extension, and why did the
recommendation change?"*

**Keys rotate without notice.** The authoritative copy of each key is printed
in that kit's own map: [demo llms.txt](https://demo.kit-project.com/llms.txt),
[mews llms.txt](https://mews.kit-project.com/llms.txt),
[real llms.txt](https://real.kit-project.com/llms.txt). If a call starts
failing, re-read the map.

## No MCP client? No problem

Every kit also serves keyless HTTP GETs (search, read, graph pivot), documented
in its llms.txt. A browser-only version of the whole exam runs at
[demo.kit-project.com/investigate](https://demo.kit-project.com/investigate).

## Scoped access, demonstrated

The papers kit also publishes **the apprentice key**, a deliberately narrowed
credential (`allowed_areas: columns`): the same kit through a smaller window.
Run the same leak query with the full key and with the apprentice key and
watch the private journals vanish from the answers. That mechanism, a company
kit sharing one knowledge area with a contractor's agent, is enforced in the
read path, not in copy. Current apprentice key, same rotation rule:

```
kbr_live_FoAauFWl7_IoDswh8rJrFvCw2qnblQTOF8DuSBkbj7A
```

## What these servers are, honestly

Read-only museum copies of Kit substrates: hybrid semantic + keyword recall,
typed knowledge graphs (including `supersedes` edges that keep replaced truth
citable), source artifacts with real URLs, and honest empty results when
nothing is held. They demonstrate read-time behavior; a full Kit also writes,
consolidates while it sleeps, and hands off between sessions on your own
machine. There is a replayable benchmark built on these exact servers:
[kit-memory-eval](https://github.com/PeterAtPondo/kit-memory-eval).

The build story: [kit-project.com/blog](https://kit-project.com/blog/), note
No. 022 in particular. The product: [kit-project.com](https://kit-project.com),
local-first, invite beta.

## License

MIT (code and examples in this repo). The demo worlds themselves are licensed
with the benchmark: see kit-memory-eval's DATA-LICENSE.
