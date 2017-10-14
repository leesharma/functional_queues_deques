# Simple and Efficient Purely Functional Queues and Deques

This repo contains Elixir implementations of the algorithms described in Chris
Okasaki's [Simple and Efficient Purely Functional Queues and Deques][paper]
(1995).

[paper]: https://www.westpoint.edu/eecs/SiteAssets/SitePages/Faculty%20Publication%20Documents/Okasaki/jfp95queue.pdf

The following implementations are included:

#### 2 Queues as paired lists

This is the standard implementation of a functional queue. All operations
require only O(1) time on a standard operation, but any given reduce *may*
require O(n) time.

```elixir
# Initializing a queue

iex> Queue.empty
# Queue#<[]>
iex> q = Queue.from([1,2,3])
# Queue#<1,2,3>


# Basic queue operations

iex> q |> Queue.insert(4) |> Queue.insert(5)
# Queue#<1,2,3,4,5>
iex> q |> Queue.remove
# {1, Queue#<2,3>}

# Other useful functions

iex> q |> Queue.append(Queue.from([8,9]))
# Queue#<1,2,3,8,9>
iex> q |> Queue.reverse
# Queue#<3,2,1>
iex> q |> Queue.take(2)
# Queue#<1,2>
iex> q |> Queue.drop(2)
# Queue#<3>
```
