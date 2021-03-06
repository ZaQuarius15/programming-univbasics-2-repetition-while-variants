# Programming as Conversation 2: Repetition With `while` Variants

## Learning Goals

* Use `Integer`'s `.times` method to execute a loop _n_-times
* Use `loop` to create an infinite loop
* Use `until` to repeat

## Introduction

As we mentioned previously, a `while...do...end` loop is the most useful
general _repetition_ statement you can know. However, we often execute the same
type of loop frequently and Ruby has some variations on `while...do...end` that
are handy to know.

## Use `Integer`.times to Execute a Loop _n_-times

It's very common to want to repeat a bit of code some number of times
(typically written as _n_) . We can use a `while...do...end` for this purpose.
Let's run some code three times:

```ruby
n = 2
count = 0
while count <= n do
  puts "I ran."
  count = count + 1
end
```

With output:

```text
I ran.
I ran.
I ran.
```

There's lots of room for confusion here. We set `count` to 0 and count up to or
equal `n`. That's a confusing way of saying "do something 3 times." Ruby agrees
and lets us say

```ruby
3.times do
  puts "I ran."
end
```

This relies upon us using a _method_ (you might recall `3.class` or
`Time.now.year` as being _methods_) called `times` that all `Integer`s provide.

## Use `loop` to Create an Infinite Loop

Sometimes we want to create an infinite loop that we want to `break` from.

```ruby
count = 0
n = 3
loop do
  break if count >= n
  puts "I ran."
  count += 1
end
```

This could be duplicated with `while...do...end`, of course by giving `while` a
permanently true _condition expression_:

```ruby
count = 0
n = 3
while true do
  break if count >= n
  puts "I ran."
  count += 1
end
```

Programmers would say `loop` is more **expressive** of an intention to run
infinitely and break on a condition. The  `while...do...end` _just happens_ to
run forever. The intention of `loop` **means** "I intend to run forever." It's
a nice way to communicate to other programmers what your intention is.

## Use `until` to repeat

The _repetition_ statement `until` is the inverse of a `while` loop.

A `while` executes the block of code _while_ the _conditional expression_ is
`true`.

An `until` will execute a block _until_ a specific condition is true. In other
words, the block of code following `until` will execute while the condition is
`false`. One helpful way to think about it is to read `until` as "if not".

> **LOGICIANS / LINGUISTS**: Yet again `until` is "while-if-not," and `unless`
> is "if-not." This all part of DeMorgan's theorems, as discussed earlier!

```ruby
counter = 0
until counter == 20
  puts "The current number is less than 20."
  counter += 1
end
```

Let's break it down:

* The counter once again starts at `0`. If it is *not* true that the counter is
  equal to `20`, the program will execute the code in the block.
* Inside the block, we will `puts` a phrase and increment the counter by `1`.
* Then, the program will go back to the top of the `until` loop and once again
  check to see if the counter is equal to `20`. If it is *not* true that the
  counter is equal to `20`, then the program will continue executing the code in
  the block. Otherwise, the program will break out of the loop.

## Conclusion

The `while...do...end` repetition statement has two "descendants:" `loop` and
`Integer.times`. They allow our code to be more communicative.
