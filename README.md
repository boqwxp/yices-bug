Yices bug repo
====

See SRI-CSL/yices2#207.
Run `yices-smt2 yices-bug.smt2`.

Actual behavior:
----

When using `(get-value ...)` after a `(check-sat)` in a `BV`-logic exists-forall SMT-LIBv2 problem, I get the following error:
```
(error "can't build a model. Call (check-sat) first")
```

Obviously this is wrong, because I just called `(check-sat)`.  Interestingly, `(get-model)` still works (see `yices_out`).

Expected behavior:
----

Yices should print the specified value and not generate an error.  Z3, for example, has no trouble with the exact same input file (see `z3_out`).
