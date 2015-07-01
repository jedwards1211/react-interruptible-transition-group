# robust-transition-group
an alternative to `ReactTransitionGroup` with reliable behavior when components re-enter before fully leaving or vice versa

This problem is described in [this React issue](https://github.com/facebook/react/issues/1326).

There are several solutions proposed for `React**CSS**TransitionGroup` there, but none that operate on the level of `ReactTransitionGroup`.

Just as a CSS transition can be reversed before completing, my solution allows entering and leaving to be reversed;
if a component is removed before its `componentWillEnter()` handler calls its `callback`, just go ahead and call
its `componentWillLeave()`.  Likewise, if a component is added back before its `componentWillLeave()` handler calls
its `callback`, just go ahead and call its `componentWillEnter()`.

Aside from this, `RobustTransitionGroup` ignores the `callback` of a `componentWillLeave()` if it is no longer in
leaving state (due to re-entry), and likewise for `componentWillAppear()` and `componentWillEnter()` callbacks.

These are the only reasonable semantics for that components which can enter and leave more quickly than they can
transition, and their hooks should handle these situations appropriately.
