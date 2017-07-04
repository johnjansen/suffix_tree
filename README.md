# Suffix Tree - (pure crystal-lang)
# UNDER CONSTRUCTION

[![GitHub version](https://badge.fury.io/gh/johnjansen%2Fsuffix_tree.svg)](http://badge.fury.io/gh/johnjansen%2Fsuffix_tree)
[![CI](https://travis-ci.org/johnjansen/suffix_tree.svg?branch=master)](https://travis-ci.org/johnjansen/suffix_tree)

## Because everyone sucks at describing a suffix tree, and its implementation. This will be a suffix tree by example, heavily commented so that hopefully it doesnt suck!

In computer science, a suffix tree (also called PAT tree or, in an earlier form, position tree) is a compressed trie containing all the suffixes of the given text as their keys and positions in the text as their values. Suffix trees allow particularly fast implementations of many important string operations. The construction of such a tree for the string takes time and space linear in the length of. Once constructed, several operations can be performed quickly, for instance locating a substring in, locating a substring if a certain number of mistakes are allowed, locating matches for a regular expression pattern etc. Suffix trees also provide one of the first linear-time solutions for the longest common substring problem. These speedups come at a cost: storing a string's suffix tree typically requires significantly more space than storing the string itself. ([Wikipedia](https://en.wikipedia.org/wiki/Suffix_tree))

## Installation

Add this to your application's `shard.yml`:

```yaml
dependencies:
  suffix_tree:
    github: johnjansen/suffix_tree
```

## Usage

```crystal
require "suffix_tree"
```

## Contributing

1. Fork it ( https://github.com/johnjansen/suffix_tree/fork )
2. Create your feature branch (git checkout -b my-new-feature)
3. Commit your changes (git commit -am 'Add some feature')
4. Push to the branch (git push origin my-new-feature)
5. Create a new Pull Request

## Contributors

- [johnjansen](https://github.com/johnjansen) John Jansen - creator, maintainer
