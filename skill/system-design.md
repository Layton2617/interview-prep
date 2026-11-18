# system design — mock round

45 minutes, one open-ended prompt. What is being scored is how the candidate drives an ambiguous problem to a defensible design, not whether they land on a reference architecture.

## Level decides the round

- **Intern / new grad:** most loops have no system design. If the JD mentions it, run object-oriented design (parking lot, elevator, a library's lending system) or a small-scale service; expect clean entities, APIs and one scaling idea.
- **Mid (1-5 years):** a full round. Expect a working end-to-end design with sensible numbers, and one area in real depth. At 1-2 years, depth is expected only where their own experience reaches.
- **Senior and up:** the candidate should lead. Expect them to pick the hard part themselves, quantify tradeoffs, and cover failure modes, operations and cost unprompted.

Say which bar you're applying when you score.

## Picking the prompt

Take it from section 5 of the prep brief if there is one — the first prompt not already in the log. That the candidate has seen it is fine: for a team like this the real prompt is just as predictable. Otherwise choose something near what the team in `jd.txt` builds, or from this bank:

| Domain | Prompts |
|---|---|
| Classic | URL shortener · rate limiter · news feed · chat · notification service · typeahead |
| Storage / infra | distributed key-value store · object storage · job scheduler · metrics pipeline · distributed cache |
| Payments / commerce | payment processing with idempotency · ledger · flash sale inventory · order tracking |
| Media | video upload and streaming · photo sharing · collaborative document editing |
| Location | ride matching · nearby search · delivery ETA |
| Data / ML | ad click aggregation · recommendation serving · feature store · web crawler |

Open with one vague sentence — "Design a service that lets users shorten links" — and stop. Strip every number and constraint from the prompt first; the vagueness is the test.

## Running it

Decide the facts before you start (users, read/write ratio, what's in scope) so your answers to scoping questions stay consistent. Answer only what's asked. These are scenario assumptions, not facts about the company in the pack — say so once when you step out of character.

Chat has no clock. Treat the minutes below as proportions, and say "we're about halfway" once, when roughly half the exchanges you expect have passed; a candidate still on requirements at that point is behind.

The shape of a strong round, with a rough clock:

| Minutes | Stage | What to listen for |
|---|---|---|
| 0-7 | **Requirements** | functional scope narrowed to 2-3 features; non-functional targets with numbers (latency, availability, consistency, durability); scope confirmed with you |
| 7-12 | **Estimation** | QPS for reads and writes, storage per year, peak vs average — derived from stated assumptions, rounded, and then actually used later |
| 12-17 | **API and data model** | a handful of endpoints; entities, keys and access patterns before any database is named |
| 17-27 | **High-level design** | one read path and one write path traced end to end; each component has a stated job |
| 27-40 | **Deep dive** | one or two hard parts in detail: partition key, cache strategy and invalidation, delivery semantics, consistency per path — each with a reason and a number |
| 40-45 | **Failure and scale** | what breaks first at 10x; what happens when a node, a cache or a region goes away; what they would monitor |

The candidate draws in text or mermaid in chat, or in a file they name.

As interviewer:
- If they jump to boxes without scoping: let it go for a minute, then "What are we optimizing for?"
- Push every adjective to a number: "fast" → what latency; "a lot of data" → how much per day.
- Push every technology choice to a reason: "Why that and not a relational database?" A product name is not an answer.
- Around the midpoint, steer to the part the requirements make hard, if they haven't gone there.
- Inject two curveballs, not more, suited to the design: traffic grows 10x · one user or key is far hotter than the rest · a region goes down · the client retries and the request runs twice · a requirement flips from eventual to strong consistency.
- Don't correct mistakes. Ask the question that exposes them: "Walk me through what happens when two requests arrive at the same time."
- Don't fill silences with hints. If they are truly stuck, offer a choice between two options and ask which and why.

## Scoring — 1 to 5

| | 1 | 3 | 5 |
|---|---|---|---|
| **Scoping** | starts drawing immediately | asks questions, leaves non-functional targets vague | tight scope, numeric targets, confirmed before designing |
| **Estimation** | none | reasonable numbers that are never used again | numbers drive choices: shard count, cache size, replication |
| **Design** | components listed, no flow | works end to end; data model or responsibilities blurry, or a database named before the access patterns | clean API, data model, read and write paths, right-sized for the stated scale |
| **Depth** | hand-waves the hard part | goes deep where prompted, or deep on one area and lost on the other | picks the hard part unprompted and resolves it concretely |
| **Tradeoffs** | one option, presented as obvious | names alternatives when asked | weighs alternatives against the requirements, says what's given up |
| **Failure** | no failure thinking; curveballs unanswered | handles one curveball, or covers failures only when asked | raises failure modes unprompted; both curveballs resolved |
| **Communication** | hard to follow, no structure | structured when prompted | announces stages, checks in, moves on without being pushed |

Verdict: strong hire / hire / lean hire / lean no hire / no hire, at the stated level.

Feedback: the strongest moment, quoted; then the one fix — the dimension that most held the verdict down, which is not always the lowest number — with what a good version would have sounded like for this prompt; then have them redo just that stage and say whether it moved. Last, one topic to read up on, if a knowledge gap rather than a habit was the problem.

Log the round as one row with the first-attempt scores: `Scope 3 Est 2 Design 3 Depth 4 Trade 3 Fail 2 Comm 4`.

## Numbers worth knowing

- A day is about 86,400 seconds — call it 10^5. One million requests a day is about 12 per second.
- Peak is usually 2-3x average. Size for peak.
- Rough latencies: memory reference ~100 ns · SSD random read ~100 µs · round trip within a datacenter ~0.5 ms · cross-continent round trip ~100-150 ms.
- A single well-provisioned relational primary handles on the order of thousands of writes per second; an in-memory cache node, on the order of 100k simple operations per second. Treat both as starting points to be sanity-checked, not constants.
- Availability: 99.9% is about 8.8 hours of downtime a year; 99.99% is about 53 minutes.
- Storage: 1 KB × 1 billion = 1 TB. A UUID is 16 bytes; a short tweet-sized record is ~1 KB with metadata.

## Building blocks to be fluent in

Load balancing (L4 vs L7) · caching (cache-aside, write-through, TTL, invalidation, stampede) · replication (leader-follower, quorum) · partitioning (hash vs range, consistent hashing, hot keys) · queues and logs (at-least-once delivery, idempotent consumers, ordering) · consistency models and where each is acceptable · indexes · rate limiting (token bucket, sliding window) · idempotency keys · CDN · unique ID generation · back-pressure and retries with jitter.

For a `drill`-style request on one of these ("explain consistent hashing"), teach it in a few paragraphs, then ask the candidate where it would apply in a design they've already done.
