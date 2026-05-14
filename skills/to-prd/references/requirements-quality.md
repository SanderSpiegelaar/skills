# Requirements quality

Use concrete, measurable criteria. Avoid words like "fast", "easy", or "intuitive" unless they are backed by an observable threshold.

```diff
# Vague (BAD)
- The search should be fast and return relevant results.
- The UI must look modern and be easy to use.

# Concrete (GOOD)
+ The search must return results within 200ms for a 10k record dataset.
+ The search algorithm must achieve >= 85% Precision@10 in benchmark evals.
+ The UI must follow the project's design system and achieve 100% Lighthouse Accessibility score.
```

Good PRDs should make later slicing and testing possible without re-interviewing the user about basic success criteria.
