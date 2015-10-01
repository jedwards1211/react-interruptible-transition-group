# react-interruptible-transition-group

An alternative to `ReactTransitionGroup` where appearing, entering, and leaving transitions get interrupted immediately if a child isremoved/re-added before fully entering/leaving.  This behaves more like CSS transitions than `ReactTransitionGroup`.

The API looks the same but unlike `ReactTransitionGroup`: `componentDidAppear`, `componentDidEnter`, and `componentDidLeave` are not guaranteed to be called; they are only called when a component fully appears/enters/leaves.  For example, if a component is removed while it's entering, the sequence will look like:

```
componentWillEnter
componentWillLeave
componentDidLeave
```

# Requirements

React >= 0.13.3 is of course required, though I've chosen not to make it a peer dependency.
