## Changelog

November 25, 2015
+ Added `main.scss` that imports all partials
+ Added basic property debugging
+ Added more `position` properties
+ Added `border-width` and `border-radius` properties
+ Moved `size` property logic out of `lifesaver.scss` into `properties.scss`
+ Changed from tabs to 2 spaces
+ Removed `lifesaver` prefix from partials

November 21, 2014
+ Added compression of matching values
+ Changed debug class names

November 19, 2014
+ Rewrote almost everything
+ Used maps instead of lists
+ Improved compile time
+ Added error messages for invalid unit types
+ Added `size` LifeSaver property for width and height properties
+ Added `skippable` function to `skip.scss`
+ Renamed `lifesaver-singles.scss` to `lifesaver-properties.scss`
+ Replaced the stress test with a debug test
+ Merged `scale-compensation` into `safe-units` unit functions
+ Removed the `append-unit` function

November 13, 2014
+ Fixed px and percentage values

November 12, 2014
+ Added partial support for unitless values
+ Reverted the way important works
+ Stored redundant logic in variables
+ Used the skip function when necessary

November 10, 2014
+ Added font size scale compensation and a function `scale-compensation`
+ Added the use of null as an alternative to x for skipping values
+ Added `singles` functions
+ Added more tests to `_lifesaver-stress-test.scss`
+ Added and simplified inline docs
+ Split off `append-unit` function

October 26, 2014
+ Added `_lifesaver-stress-test.scss` partial
+ Re-added `convert` function
+ Compressed duplicate logic into a variables
+ Fixed everything I broke on October 24, 2014

October 25, 2014
+ Split off unit functions into `_safe-units.scss`
+ Added more functions to `_safe-units.scss`

October 24, 2014
+ Re-organized if statements and chunks of code to speed up compilation
+ Added inline documentation
+ Changed `add-unit` function name to `append-unit`

October 15, 2014
+ Added various rounding convert functions
+ Renamed `safe-convert` to `round-convert`
+ Changed `rem` and `em` functions to use `ceil-convert`
+ Changed a few double quotes to single quotes

September 23, 2014
+ Fixed `safe-convert` function
+ Change `rem` and `em` functions to use `safe-convert`

September 22, 2014
+ Changed adding unit types to values to multiplying by unit type

Septermber 21, 2014
+ Added `safe-convert` function that may help prevent browser rounding errors

August 21, 2014
+ Changed double quotes to single quotes

August 16, 2014
+ Changed `join` function name to `add-unit`

August 11, 2014
+ Used `convert` function in unit functions

July 27, 2014
+ Changed `$properties` to `$property-list`

July 21, 2014
+ Added multiple properties

July 20, 2014
+ Committed Project
