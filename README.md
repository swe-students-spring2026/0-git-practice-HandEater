# Notes on *Python Typing Survey 2025*

## A Brief Summary of the Article

**Source:** [Engineering at Meta](https://engineering.fb.com/2025/12/22/developer-tools/python-typing-survey-2025-code-quality-flexibility-typing-adoption/)

**Date:** December 22, 2025

The 2025 survey, reflecting responses from over 1,200 developers, confirms that type hints have graduated from an optional feature to a fundamental component of modern Python development. Adoption has stabilized at a high level (86% use types often or always), driven largely by the desire for better code quality and the "developer experience" benefits of superior IDE autocompletion and navigation.

## Personal Takes

### Adoption and Sentiment

Interestingly, adoption peaks among mid-level developers (5-10 years experience) at 93%. It dips slightly for the most junior (learning curve) and the most senior developers (legacy habits/codebases). My personal interpretation is that mid level developers making contemporary softwares aims for code quality, readability, and flexibility. The ability to adopt typing gradually remains Python's killer feature here.

### Pain Points

Here are some pain points I found out from the survey data. The top complaint is the difficulty of integrating with untyped or poorly typed third-party libraries (e.g., Pandas, Django). The split between Mypy, Pyright, and newer tools creates inconsistency. And finally complex types can make Python feel "un-Pythonic" and cluttered.

### Tooling Shift

There is a notable shift toward performance. Rust-based type checkers like Pyrefly (open-sourced by Meta in May 2025), Ty, and Zuban are now used by over 20% of respondents. This suggests a community hunger for speed in their dev loops.

This reminds me of another blog from Engineering at Meta I find interesting, which can be pair-read with the python survey is [An inside look at Meta's transition from C to Rust on mobile](https://engineering.fb.com/2025/07/01/developer-tools/an-inside-look-at-metas-transition-from-c-to-rust-on-mobile/). It connects directly to the "Rust Rising" trend mentioned in the Python survey. While the survey highlights Rust-based tools *for* Python, this article details the massive architectural shift of replacing legacy C code with Rust in mobile infrastructure.

It is interesting to me to see that the drivers for this shift (developer happiness & reliability) mirror exactly why Python developers are adopting type hints. Meta found that moving to Rust:
1. Prevent memory bugs (reducing vulnerability density by 1000x on Android)
2. Actually sped up development by providing clear ownership semantics and modern tooling. 
And it's implied in these articles that "strictness" in a language often leads to greater freedom and velocity in the long run.

> [Why Tech Giants Are Going for RUST](https://www.youtube.com/watch?v=DvY1-993OBE): This video also provides excellent context on why major tech companies are aggressively adopting Rust, reinforcing the trends seen in both the Python tooling landscape and Meta's infrastructure.

---

## Comment From Frank Wu
I found the survey valuable because it frames typing as a developer-experience multiplier rather than just “more correctness.”
One point I’m curious about is how teams balance stricter typing with onboarding speed, especially when third-party libs remain partially typed.
If the ecosystem keeps moving toward faster Rust-based checkers, I think typing will become the default expectation for production Python.


