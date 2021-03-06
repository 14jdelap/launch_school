# What are loops?

Loops are Ruby constructs that repetitively execute the code within them until the loop is broken. At the end of a loop, if it isn't broken it'll continue execution at the top of the loop. A loop is broken when the condition is met.

## What is the anatomy of a loop?

A loop has 4 components:
- A way to execute the code repeatedly
- A way to break the loop
- Counter
- A way to retrieve the current value

## What loop constructs do we have available?

- `loop`
  - Difference: it requires a block
- `while`
- `until`
- `for`

### Analyzing the anatomy of looping constructs

```ruby
x = 0

while x < 1 # Code execution + break
  x += 1
  break 5   # Break loop
end         # => 5
```

## Iterators
Iterators are methods that naturally loop over a given set of data and allow you to operate on each collection element.

- `each`
- `select`
- `map`

## Loop and return values

`break` has a default return value of `nil` but can return another value if passed as an argument.

```ruby
loop do
  break
end     # => nil

loop do
  break 5
end     # => 5
```

`while` and `until` return `nil` by default
```ruby
while x > 5
  x -= 1
end # => nil

until x >= 10
  x += 1
end # => nil
```

But we can also use `break` statements in them
```ruby
x = 10

while x > 5
  x -= 1
  break x
end # => 9
```

## `next`

`next` tells the loop to skip the current iteration and continue to the next.

```ruby
x = 0

while x < 1 # Code execution + break
  x += 1
  next
  break 5   # Break loop
end         # => nil
```
Anne Tiotuico, Alfonzo Gonzalez, Antonio Serna, Jesse, Leena
Why do we get this value?

## Loops and variable scoping

**Loops create a leaky scope while other loops do not — what explains this?**

```ruby

loop do
  x = 5
  break
end

x # 5

while true
  y = 10
  break
end

y # NameError
```

Loops are part of the general program execution. Thus, they belong to the same scope as whereever they're located. The special case is `loop` because it requires a block. Thus, scoping works differently there because of the block.