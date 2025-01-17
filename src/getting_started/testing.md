# Testing

You can test your Noir programs using Noir circuits.

## Testing in Noir

Nargo will automatically compile and run any functions which have the decorator `#[test]` on them if you run `nargo test`.

For example if you have a program like:

```rust,noplaypen
fn add(x: u64, y: 64) -> u64 {
    x + y
}

#[test]
fn test_add() {
    constrain add(2,2) == 4;
    constrain add(0,1) == 1;
    constrain add(1,0) == 1;
}
```

Running `nargo test` will test that the `test_add` function can be executed while satisfying the all the contraints which allows you to test that add returns the expected values. Test functions can't have any arguments currently.

This is much faster compared to testing in Typescript but the only downside is that you can't explicitly test that a certain set of inputs are invalid.
i.e. you can't say that you want add(2^64-1, 2^64-1) to fail.

`nargo test` accepts an optional pattern argument to only run tests with names containing the given pattern.
