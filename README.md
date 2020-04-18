What is "dynamic programming"!?
===

"Dynamic programming" combines two things:
1. Depth-first search; and,
2. A table.

The basic idea is that *before* traversing down a branch of the tree,
we check in our table if we've already traversed a branch that looks
like the current branch. If so, we return the value in the table.
If we haven't traversed the branch before, we traverse the branch and
put the result of the branch (whatever that is) in to the table.

Thus, if our function for traversing looks like this:

    int traverse(int, double, double)

Then the table has, as keys, a tuple `<int, double, double>`, and as
values `int`:

    table : <int, double, double> => int

Now we ask ourselves: why would this speed anything up!?

Answer: in *general*, it doesn't.

We only get a speed up if the following condition is met:

> The size of the table grows more slowly than the number
> of branches we have to visit.

Let's consider a problem of traversing the fibonacci sequence:

    int fib(N)

The size of the table is proportional to the integer passed in,
that is, the size of the table is `O(N)` for an input of `N`.
However, the recursive definition of fibonacci (the naive one)
grows *exponentially* with respect to `N`: `O(2^N)`.
Since the size of the tree is large than the size of the table,
"dynamic programming" will speed up the fibonacci function.
