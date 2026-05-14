# Anti-pattern: horizontal slices

Do not write all tests first, then all implementation. That treats RED as "write all tests" and GREEN as "write all code."

This produces weak tests:

- Tests written in bulk test imagined behavior, not actual behavior.
- Tests focus on shapes, data structures, and signatures instead of user-facing behavior.
- Tests become insensitive to real behavior changes.
- You commit to test structure before understanding the implementation.

```text
WRONG:
  RED:   test1, test2, test3, test4, test5
  GREEN: impl1, impl2, impl3, impl4, impl5

RIGHT:
  RED -> GREEN: test1 -> impl1
  RED -> GREEN: test2 -> impl2
  RED -> GREEN: test3 -> impl3
```

Correct TDD uses vertical tracer bullets: one test, one minimal implementation, then repeat.
