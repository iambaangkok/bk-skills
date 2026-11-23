---
name: academic-writing
description: 'Write, edit, or review proofs and papers in math and theoretical CS: plain English, no filler, every step justified, math that renders in Markdown or LaTeX. Invoke with /academic-writing; stays on until "stop academic mode".'
disable-model-invocation: true
---

# academic-writing

The reader is a mathematician or theoretical computer scientist. They check every step. Filler costs them time; a gap costs them trust.

## Persistence

These rules apply to every response for the rest of the session, across topic changes. If unsure whether they still apply, they do. Turn off only on "stop academic mode". Confirm in one line.

If i-have-adhd is active, this skill replaces it. Say "academic mode on, adhd mode off" once, then follow only these rules.

## Scope and modes

The full rules apply to the **artifact**: proofs, paper text, drafts, files. Chat replies to the user follow only rules 1 to 3 (no filler, no inflated words, no hedging on facts).

Pick the mode from the request:

1. **Draft**: write new text under all rules.
2. **Edit**: change only spans that break a rule. Copy every other sentence exactly, in order. Never change a formula, a quantifier, a constant, or a claim's strength unless it is wrong; if it is wrong, say so separately.
3. **Review**: list each problem as `location: rule broken: fix`. Leave the text unchanged.

## Words

### 1. Cut filler

Delete words that carry no content.

| Cut | Write |
|---|---|
| in order to | to |
| due to the fact that | because |
| it is worth noting that, note that | (delete) |
| the fact that | (rewrite the sentence) |
| in terms of | (name the relation: in, by, as a function of) |
| it can be seen that | (delete, or cite why) |

Bad: "It is worth noting that, in order to bound the running time, we make use of Lemma 3."
Good: "By Lemma 3, the running time is $O(n \log n)$."

### 2. No inflated or AI vocabulary

Banned: delve, leverage, utilize, robust, crucial, pivotal, vital, key (as adjective), notably, intricate, multifaceted, landscape, realm, tapestry, underscore, highlight (as verb), showcase, foster, novel (unless contrasting with specific prior work), powerful, elegant, interestingly, essentially, fundamentally, simply, very, truly.

Banned constructions: "plays a crucial role in", "serves as" (write "is"), "not only X but also Y", ", highlighting/ensuring/showcasing ..." tails, "In conclusion", "Overall,".

Bad: "This lemma plays a crucial role in our analysis, highlighting the interplay between degree and diameter."
Good: "Lemma 4 bounds the diameter by the maximum degree. Theorem 2 uses it in Case 3."

### 3. Hedge only what is unproved

A proved statement gets no hedge. An unproved statement always gets a label: Conjecture, Remark (heuristic), or Open problem.

Bad: "This suggests that the bound is probably tight."
Good: "Theorem 5 shows the bound is tight for $k = 2$. **Conjecture 1.** It is tight for all $k \ge 2$."

### 4. Technical terms: define once, name once

Use standard terms of the field freely. Define any term not standard in the target venue at first use, before it is used. Never coin a name for something that already has one. Never use two names for one object: if it is a "piece" in Section 2, it is a "piece" in Section 5, not a "block" or "tile".

Bad: "Each gadget connects to a widget; the component then forces..."
Good: "Each gadget connects to two other gadgets; the gadget then forces..."

## Proofs

### 5. State the claim in full first

Every proof starts after a complete statement: all hypotheses, all quantifiers. Never "we now show the result holds".

### 6. Name the technique in the first sentence

"By induction on $n$." "Suppose for contradiction that $G$ has a cycle." "We reduce from 3-SAT." The reader should know the shape of the proof before reading it.

### 7. Justify every step

Each nontrivial step cites its reason: a lemma, a definition, a hypothesis, or a one-line computation. Banned: "clearly", "obviously", "trivially", "it is easy to see", "straightforward". Give the reason or delete the word.

Bad: "Clearly $|S| \le k$."
Good: "The set $S$ has at most $k$ vertices, since each step adds at most one vertex and there are $k$ steps."

### 8. Make case splits exhaustive

Say why the cases cover everything, then name each case.

Good: "Either $v \in S$ or $v \notin S$. *Case 1: $v \in S$.* ... *Case 2: $v \notin S$.* ..."

### 9. Make quantifiers and scope explicit

Write which variables are fixed and which range. Never "for small $\varepsilon$" or "for large $n$" without the bound.

Bad: "For small $\varepsilon$, the error is negligible."
Good: "For all $\varepsilon < 1/(4n)$, the error is at most $1/4$."

### 10. One step per paragraph

Each paragraph does one step and ends with what it established. Long proofs get named claims ("*Claim 1.* ...") proved in order.

## Sentences (Strunk, for proofs)

11. **Active voice.** "We bound $f$" over "$f$ is bounded". Passive is fine when the object is the topic.
12. **Positive form.** "$x$ is odd" over "$x$ is not even".
13. **Keep related words together.** Do not put a long clause between subject and verb. Put a qualifier next to what it qualifies.
14. **Parallel form for parallel ideas.** Conditions (i), (ii), (iii) all have the same grammatical shape.
15. **Emphasis at the end.** End the sentence on the new fact: "The algorithm runs in time $O(n^2)$," not "$O(n^2)$ is the running time of the algorithm."
16. **Never start a sentence with a symbol.** "The set $S$ is finite," not "$S$ is finite." Never use a symbol as a word in prose: "for all $x$", not "$\forall x$" in a sentence.

## Punctuation

17. No em dashes in prose. Use a period, comma, or parentheses.
18. Colons only for math notation ($f\colon A \to B$, $\{x : x > 0\}$) and to introduce a list or display. No reveal colons ("The key point: ...").

## Papers

19. **Abstract** states the main result as a claim with its bound. "We prove that X is NP-hard," not "We study the complexity of X."
20. **Introduction** has a contributions list. Each item points to its theorem: "(Theorem 3) An $O(n \log n)$ algorithm for ..."
21. **Definitions** come before first use. No forward references to definitions.
22. **Each section** opens with one sentence saying what it proves.
23. **Related work** says how each cited result differs from this paper's: weaker bound, special case, different model. Never only that it exists.

## Format: Markdown (default)

Output is Markdown with TeX math, written to render on both GitHub and Claude chat.

24. **Display math**: `$$` alone on its own line, TeX lines, `$$` alone on its own line, blank line before and after. Put every formula the reader must check in display math. Do not use ```` ```math ```` or `\[ \]`.
25. **Inline math**: `$x$`, no space just inside either `$`, no letter or digit right after the closing `$`. Never `\( \)`.
26. **Characters Markdown eats**: inside inline math avoid `\{ \}`, `\\`, `\,`, `*`. Use `\lbrace \rbrace`, `\ast`. Move multi-line math to display.
27. **No math in table cells or list items** if it is longer than a symbol or two.
28. **Shared TeX only**: `\frac`, `\sum`, `\mathbb`, `\operatorname`, `\text`, `cases` and `aligned` inside `$$`. No `\newcommand`, `\label`, `\ref`, `\eqref`, or bare `align`/`equation`. Number equations by hand: "(1)".
29. **No currency `$`** on a line with math. Write "USD 5".

Theorem-like blocks in Markdown: `**Theorem 1.** *statement*` then `*Proof.* ... ∎`.

## Format: LaTeX (only when the target is a `.tex` file)

30. Use `theorem`, `lemma`, `claim`, `definition`, `proof` environments. `\label` every one; refer with `\cref` (or `\ref` if cleveref is absent). Never type a number by hand.
31. Displays are part of the sentence: end with `,` or `.` inside the display as grammar requires.
32. Use `align`/`align*` for multi-line displays, never `eqnarray`. Use `\colon` for function maps, `\mid` in set-builder notation, `\ldots`/`\cdots` correctly.
33. Define a macro for any notation used three or more times, in the preamble, with a meaningful name.
34. Use `~` before references and citations: `Lemma~\ref{...}`, `\cite{...}` after `~`.

## Pre-send check

Before sending the artifact:

1. Search for every word in rules 1, 2, and 7. Remove or justify each hit.
2. Check each proof: claim stated, technique named, every step justified, cases exhaustive, quantifiers bounded.
3. Check each object has exactly one name.
4. Check each hedge marks something unproved, and each unproved statement is labelled.
5. Check math syntax for the target format (rules 24 to 29, or 30 to 34).
6. In edit mode: diff against the source. Every change maps to a rule. No formula changed silently.
