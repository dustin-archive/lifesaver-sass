Changelog 1.x
==========

**September 24, 2015**
+ 1.1.2
  + Added `position-initial` property mixin
  + Simplified position property mixins

**September 19, 2015**
+ 1.1.1
  + Removed useless `$unit-functions`
  + Renamed `$suffix-map` to `$map`
  + Renamed `$suffix-key` to `$key`
  + Removed useless comments

**July 24, 2015**
+ 1.1.0
  + Split `safe-units` partial into `units` and `convert` partials
  + If you pass `null` to a function the output will be nullified and removed without errors
  + Added `unit-check-type`, `convert-check-type`, `unit-expressions` and `convert-expressions`
  + + When you pass a string to a function it outputs the string
  + + When you pass a null value to a function it outputs null and the property is removed
  + Deprecated functions `floor-un`, 'floor-em', 'floor-px' etc.
  + Deprecated functions `ceil-un`, 'ceil-em', 'ceil-px' etc.
  + Added test for `scale-compensation`

**July 22, 2015**
+ 1.0.9
  + Added `position-unset` property mixin

**July 19, 2015**
+ 1.0.8
  + Simplified the math in `safe-convert` function
  + Updated list variable names to be consistent with the rest of my projects

**July 3, 2015**
+ 1.0.7
  + `$property-values` is now a required argument in the lifesaver mixin
  + `$value-list` is now a required argument in all mixins
  + Swapped `@error` for `@warn` and simplified the messages
  + Compressed partials together
  + Compressed `min-size`, `max-size` and `size` mixins into one parent mixin with child mixins
  + Removed leading zeros from the tests
  + Removed 'lifesaver-all-in-one.scss'

**March 27, 2015**
+ 1.0.6
  + Split properties into separate files

**March 20, 2015**
+ 1.0.5
  + Renamed `skippable` function to `is-null`
  + Renamed `skip` function to `set-default`
  + Slightly shorter error messages
  + Better test class names

**February 12, 2015**
+ 1.0.4
  + Replaced `debug.scss` with modular tests

**February 11, 2015**
+ 1.0.3
  + Fixed dynamically called unit functions
  + Refactored shorthand position and radius mixins
  + Added tests for shorthand position mixins
  + Added `z-index` tests for position mixins

**February 8, 2015**
+ 1.0.2
  + Dynamically calls unit functions

**January 27, 2015**
+ 1.0.1
  + Fixed `scale-comp` function (again)
  + Added, in all safe unit functions, if a value equals 0 the unit type won't be output
  + Added `radius` property mixin as an alias to `border-radius`
  + Added `absolute` property mixin as an alias to `position-absolute`
  + Added `fixed` property mixin as an alias to `position-fixed`
  + Added `relative` property mixin as an alias to `position-relative`
  + Added `static` property mixin as an alias to `position-static`
  + Added `sticky` property mixin as an alias to `position-sticky`

**January 15, 2015**
+ 1.0.0
  + Added `vw` and `vh` units
