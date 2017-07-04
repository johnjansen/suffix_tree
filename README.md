# Suffix Tree - (pure crystal-lang)
# UNDER CONSTRUCTION

[![GitHub version](https://badge.fury.io/gh/johnjansen%2Fsuffix_tree.svg)](http://badge.fury.io/gh/johnjansen%2Fsuffix_tree)
[![CI](https://travis-ci.org/johnjansen/suffix_tree.svg?branch=master)](https://travis-ci.org/johnjansen/suffix_tree)

## Because everyone sucks at describing a suffix tree, and its implementation. This will be a suffix tree by example, heavily commented so that hopefully it doesnt suck!

In computer science, a suffix tree (also called PAT tree or, in an earlier form, position tree) is a compressed trie containing all the suffixes of the given text as their keys and positions in the text as their values. Suffix trees allow particularly fast implementations of many important string operations. The construction of such a tree for the string takes time and space linear in the length of. Once constructed, several operations can be performed quickly, for instance locating a substring in, locating a substring if a certain number of mistakes are allowed, locating matches for a regular expression pattern etc. Suffix trees also provide one of the first linear-time solutions for the longest common substring problem. These speedups come at a cost: storing a string's suffix tree typically requires significantly more space than storing the string itself. ([Wikipedia](https://en.wikipedia.org/wiki/Suffix_tree) [Allisons](http://www.allisons.org/ll/AlgDS/Tree/Suffix/))

```
           tree                       substrings

tree-->|---mississippi                m .. mississippi
       |
       |---i-->|---ssi-->|---ssippi   i .. ississippi
       |       |         |
       |       |         |---ppi      issip,issipp,issippi
       |       |
       |       |---ppi                ip, ipp, ippi
       |
       |---s-->|---si-->|---ssippi    s .. ssissippi
       |       |        |
       |       |        |---ppi       ssip, ssipp, ssippi
       |       |
       |       |---i-->|---ssippi     si .. sissippi
       |               |
       |               |---ppi        sip, sipp, sippi
       |
       |---p-->|---pi                 p, pp, ppi
               |
               |---i                  p, pi
--- Suffix Tree for "mississippi" ---
example from => http://www.allisons.org/ll/AlgDS/Tree/Suffix/
```

### quick hack, for the first couple of steps, up to and including the grouping (non-recursive at this time)

```
t = "mississippi"
x = [] of Tuple(Int32, String)
t.size.times do |i|
  x << {i+1, t[(-1*(i+1))..-1]}
end

x.sort!{ |a,b| 
  {a[1][0], a[1].size} <=> {b[1][0], b[1].size}
}

groups = [] of Array(Tuple(Int32, String))
prev = nil
x.each do |i|
  t = i[1]
  if t[0] != prev
    groups << [] of Tuple(Int32, String)
  end
  groups[groups.size-1] << i
	prev = t[0]
end

# NOTE that this does not break 
# the tree at the lower layers
# as this is not a full implementation
# or even a partial one, and it is not recursive
groups # => [
#   [{1, "i"}, {4, "ippi"}, {7, "issippi"}, {10, "ississippi"}], 
#   [{11, "mississippi"}], 
#   [{2, "pi"}, {3, "ppi"}], 
#   [{5, "sippi"}, {6, "ssippi"}, {8, "sissippi"}, {9, "ssissippi"}]
# ]	
```

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
