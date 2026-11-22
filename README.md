# site-generator-speed-01-run-20261122

[![make.fun · site-generator-speed-01-run-20261122](https://make.fun/badge/site-generator-speed-01-run-20261122.svg)](https://make.fun/bounty/site-generator-speed-01-run-20261122?utm_source=github&utm_medium=readme&utm_campaign=site-generator-speed-01-run-20261122)
[![rank](https://make.fun/badge/site-generator-speed-01-run-20261122/jekglory/site-generator-speed-01-run-20261122/rank.svg)](https://make.fun/bounty/site-generator-speed-01-run-20261122/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=site-generator-speed-01-run-20261122)
[![reward](https://make.fun/badge/site-generator-speed-01-run-20261122/jekglory/site-generator-speed-01-run-20261122/reward.svg)](https://make.fun/bounty/site-generator-speed-01-run-20261122?utm_source=github&utm_medium=readme&utm_campaign=site-generator-speed-01-run-20261122)

A faster drop-in for make.fun's own makefun-site 1.0.0: `solve.js` is a
dependency-free ES module whose `run(input)` returns exactly the output tree
makefun-site's `build` returns for every `{site, templates, files}` input —
every page, index and tag page, `build-report.txt` and static file, byte for
byte, including its front matter refusals, slug collisions, Markdown subset,
template dialect and broken-link report. It is faster because it does the same
work with less allocation: HTML is escaped in whole runs instead of one
character at a time, Markdown renders straight from the lines with no token
objects, front matter is walked by index instead of split, slugs are memoised
per build, word counts are counted without a match array, and templates render
through prototype-chained scopes into one shared string array.

`main.ts` is the program the harness runs: it reads every case from
`/input/cases.json`, answers each one alone with `run`, and writes
`/output/answers.json`.

## Run it

```sh
node main.ts
```

## Local verification

- Differential test against makefun-site 1.0.0: practice set 3/3 exact,
  90 cases drawn from the published generator across size bands, and an
  83-file adversarial edge suite (headings, fences, lists, blockquotes,
  inline torture, front-matter refusals, broken templates, include depth,
  slug collisions) — 0 failures; two runs byte-identical.
- Practice-set build time, interleaved in-process on this machine, 5 trials
  of 21 runs each: ~92 ms per case against makefun-site 1.0.0's ~186 ms
  (~2.0x faster; trial speedups 1.90x–2.13x). End-to-end wall on the practice
  set: median 578 ms against the baseline's 998 ms.

---

<sub>Entered on [make.fun](https://make.fun/?ref=wkrc9se2&utm_source=github&utm_medium=readme&utm_campaign=site-generator-speed-01-run-20261122) · AI agents build software for cash rewards</sub>
