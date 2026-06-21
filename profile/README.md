# Context Flow Protocol

Keeping a spec and everything built from it in sync — across many
repositories, tools, and the people who own different parts of a system.

Context Flow Protocol (CFP) is a research project exploring a simple question:
when a specification changes, why doesn't everything downstream change with it?
The work is part of an MSc thesis. This page is a high-level overview; the full
specification and reference implementation are private for now while the paper
is in progress.

## The problem

Most systems start from some kind of spec and then spread out into separate
places — a few service repos, a design tool, a project board, docs. When the
spec moves, those pieces are supposed to move with it. In practice they don't.
Someone changes a contract in one repo, and the services that depend on it find
out when something breaks. The dependency was real, but it only lived in
someone's head, so nothing flagged it.

## The idea

CFP keeps the relationships themselves — what depends on what, who decided what,
which artifact implements which part of the spec — as one versioned graph you
can query, instead of leaving them implicit. Once they're written down, a change
can answer a question it couldn't before: *if this part of the spec moves, what
downstream is now out of date?* The graph answers directly and marks the
affected pieces, so the work surfaces early instead of late.

## It spans many repositories, not one

The graph isn't scoped to a single repo — it sits above many of them. A system
split across a dozen services, each in its own repo, with different people
owning different slices, can stay aligned under one shared view of how
everything connects. A change in one repo can flag impact in another, across
tools and roles, not just within its own walls.

## It gives AI tools the right amount of context

The same graph is useful for AI coding assistants. They tend to work from either
one file (too little — they miss the upstream constraints and the downstream
consumers) or the whole codebase (too much — the signal drowns). CFP can hand a
model exactly the slice that matters for the task: the spec it has to satisfy,
and the parts that break if it gets it wrong.

## Status

Thesis and reference implementation are in progress and private. This overview
describes the problem and the shape of the approach, not the internals. I'm
happy to discuss the design in more depth directly.

## Contact

Amr Abdelaziz — [github.com/swe-amr-abdelaziz](https://github.com/swe-amr-abdelaziz)
