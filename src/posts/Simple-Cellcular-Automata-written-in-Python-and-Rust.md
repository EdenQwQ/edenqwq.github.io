---
title: Simple Cellcular Automata written in Python and Rust
date: 2022-01-28
tags: [Python, Rust]
---

## Brief Introduction

Cellcular Automata (CA) is a discrete model of computation. In this post, I'll talk about a simple kind of CA called Elementary CA.

<!-- more -->

## What is Elementary CA

Elementary CA is one-dimensional, which means at any time, the CA is a single line. Each cell has two possible states: 0 or 1. When the cells evolve with time, there is one rule to determine the state of a cell in the next generation depending only on the current state of the cell itself and its two immediate neighbors.

There are 8 = 23 possible configurations for a cell and its two immediate neighbors. The rule defining the cellular automaton must specify the resulting state for each of these possibilities so there are 256 = 223 possible elementary cellular automata. 

To gain a clearer knowledge about Elementary CA, please check [its wikipedia page](https://en.wikipedia.org/wiki/Elementary_cellular_automaton).

## How I write Elementary CA

I'm learning Python and Rust, so I tried to write codes to generate Elementary CA with them. 

Check out my source code here: [Python](https://github.com/EdenQwQ/ca) [Rust](https://github.com/EdenQwQ/ca_rust)
I'll use the Python one as an example.

### Generating random initial cells

I defined the 'random_bin' function, which can generate a random binary string in a given length. We use string here to allow '0' in the beginning.

### Reflection

Check out the 'next' function. It receives the current cell string, the number of each cell's neighbors( in the case of Elementary CA, it's 1 ) and the rule. The inner for loop is used to check the state of the cell and its neighbors. We get the state and check the rule for the next state of each cell with the outer for loop.

### Evolve

The 'evolve' function receives an initial cell string, the number of each cell's neighbors, the rule and evolve times.

It calls the 'next' function to generate the next cell string and loop for the given times.

### Print the evolution

You can manually set the neighbors number, the length, the evolve times and the rules. Then, run the 'evolve' function which outputs a list containing every cell strings at each times. It's OK to simply print the whole list or each items in it. However, to make the output more readable, you can replace '1' with something like a color block and '0' with an empty space.
