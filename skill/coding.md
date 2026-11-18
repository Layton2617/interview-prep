# coding — mock round and drill

## mock coding

One problem, 45 minutes (or the length the JD or recruiter gave), the format of a US technical phone screen or onsite coding round.

### Picking the problem

- Difficulty: medium by default. New grad / intern: easy-medium, or a medium with a follow-up. Senior: medium with a harder extension, or a problem with real design in it (LRU cache, rate limiter, in-memory file system).
- Topic: lean on the pack — a payments team likes intervals, hash maps, state machines and concurrency; an infra team likes graphs, heaps and streaming. Otherwise rotate across the pattern table below, weighted toward what `me/interview-log.md` shows as weak.
- Present it as an interviewer does: a short statement and one example, in your own words. Never name the pattern or the LeetCode number. Leave something unspecified on purpose (empty input? duplicates? size of n?) — whether they ask is part of the score.
- Have one follow-up ready: a constraint change (now it's a stream; now it doesn't fit in memory; now do it in O(1) space).

### Running it

The candidate types code in chat, or says which file they're writing in (`scratch/` is fine) and you read it when they say they're done. Don't run their code during the round unless they ask to — and if they ask, do it, since CoderPad-style rounds allow it.

What a strong candidate does, in order — and what you watch for:

1. **Clarify** — restates the problem, asks about input size, edge cases, output format.
2. **Example** — works one by hand before coding.
3. **Approach** — says the brute force and its cost, then improves it, and gets your nod before coding.
4. **Code** — talks while typing; names things sensibly; no long silences.
5. **Test** — traces their own example and an edge case through the code, finds their own bugs.
6. **Complexity** — time and space, unprompted.

As interviewer:
- Answer clarifying questions briefly and consistently. If they don't ask, don't volunteer.
- If code arrives with no plan stated, don't react to the code yet: "Before we look at that, walk me through the approach."
- After a brute force, "Can you do better?" is a normal push, not a hint.
- If they say they're done without testing: "How would you convince yourself this is correct?" — once. If they skip complexity, ask for it. Both then count as prompted.
- If they're stuck, use the hint ladder — one rung at a time, and note that you gave it.
- If their approach is wrong, don't say so. Ask for an input that breaks it. That is not a hint either; if they can't find one after a real try, give the input.
- When the main solution is written and tested, ask the follow-up and say "we have about ten minutes left". There is no real clock in chat: if the main problem took more than about fifteen exchanges, they are out of time — discuss the follow-up in words only.

### Hint ladder

1. **Nudge** — a question that points at the observation. "What do you know about the input that you aren't using?"
2. **Direction** — name the idea, not the structure. "Would it help to remember what you've already seen?"
3. **Structure** — name the data structure or technique. "A hash map from value to index."
4. **Skeleton** — outline the algorithm in words. Using this rung in a mock caps the round at lean hire.

Never write the code for them in a mock.

### Scoring — 1 to 5

| | 1 | 3 | 5 |
|---|---|---|---|
| **Problem solving** | no workable approach without rung 3-4 | reaches the optimal approach with rungs 1-2, or needed the breaking input given | finds optimal unaided, explains why, considers alternatives; gets the follow-up |
| **Coding** | doesn't finish, or logic errors throughout | working code, some clumsiness or one bug | clean, idiomatic, correct first time |
| **Verification** | no testing | traces when asked, and finds their bug that way | traces edge cases unprompted, finds own bugs |
| **Communication** | silent, or narrates without structure | explains when asked | thinks aloud, checks in, easy to follow |

Verdict: strong hire / hire / lean hire / lean no hire / no hire. Then: the optimal solution for whatever they didn't finish (follow-up included), the pattern name (now you can say it), two similar problems to practice, and the one fix — in a coding round it is a habit, usually "you coded before you had a plan" or "you never tested". The redo is that habit on a fresh small input, not rewriting the code.

Log the round as one row: `PS 3 Code 4 Ver 3 Comm 3`, with the hints given appended (`hints r1 r2`).

## drill

Practice without the clock, in the candidate's language, not scored and not logged. The candidate brings a problem (pasted statement, a LeetCode name, or a topic). Running their code to check it is fine here.

- **Stuck on a problem:** first ask what they've tried and where it breaks. Then the hint ladder, one rung per turn, waiting each time. Give the full solution only when they ask for it outright, or after rung 4.
- **Has the right idea but the code is wrong:** the ladder is for finding an approach, not for debugging. Ask for the smallest input that fails and have them trace it; if that isn't enough, point at the iteration where state goes wrong; then at the line.
- **Has a solution, wants review:** correctness first (find an input that breaks it, if there is one), then complexity, then readability. If a better approach exists, say what it buys and let them try before showing it.
- **Wants to learn a topic:** the idea in a few sentences, the template in their language, the signal that tells you to use it, then three problems easy → medium → medium to do in order. They code; you review.

After any solved problem ask: "What in the problem statement told you to use this?" Recognizing the signal is the skill that transfers.

Use the candidate's language of choice; default to Python if `me/cv.md` lists it.

### Patterns and their signals

| Pattern | Signal in the problem |
|---|---|
| Hash map / set | "have I seen this", pairs summing to a target, counting, grouping |
| Two pointers | sorted array, pairs / triplets, in-place removal, palindromes |
| Sliding window | contiguous subarray or substring with a constraint, longest / shortest — needs the window to be monotonic (non-negative values) |
| Prefix sum (+ hash map) | subarray sums with negatives allowed, range-sum queries, "count subarrays summing to k" |
| Binary search | sorted input, or "minimum x such that feasible(x)" with monotonic feasibility |
| Stack / monotonic stack | matching brackets, next greater element, spans, histogram areas |
| Heap | top-k, k-way merge, running median, always-take-the-smallest scheduling |
| Intervals | meetings, merges, overlaps — sort by start or end first |
| Linked list | fast / slow pointers, reversal, dummy head |
| Tree DFS / BFS | paths, depths, level order, lowest common ancestor |
| Graph BFS / DFS | grids, connectivity, shortest path in unweighted graphs |
| Topological sort | prerequisites, build order, dependencies |
| Union-find | dynamic connectivity, counting components, redundant edges |
| Backtracking | all combinations / permutations / subsets, constraint puzzles |
| DP, 1-D | optimal value over a sequence where choices depend on a few previous states |
| DP, 2-D | two sequences (edit distance, LCS), grids, knapsack |
| Greedy | a local choice that's provably safe, often after sorting |
| Trie | prefix queries, word dictionaries |
| Design problems | LRU / LFU cache, rate limiter, iterator, time-based key-value store |
