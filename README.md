LifeSaver
=========

A Sass mixin that allows for quicker changes to units and values.


#The Rundown
##Mixin
		@include ls( properties, values, units, important );

		// Input
			@include ls( margin padding, 2 4 x 16, px rem );

		// Output
			margin-top: 2px;
			margin-right: 4px;
			margin-left: 16px;
			margin-top: 0.125rem;
			margin-right: 0.25rem;
			margin-left: 1rem;
			padding-top: 2px;
			padding-right: 4px;
			padding-left: 16px;
			padding-top: 0.125rem;
			padding-right: 0.25rem;
			padding-left: 1rem;

		// Output is Indented and Commented for Demonstration

		// Margin
			// Pixels
				margin-top: 2px;
				margin-right: 4px;
				margin-left: 16px;

			// Rem
				margin-top: 0.125rem;
				margin-right: 0.25rem;
				margin-left: 1rem;

		// Padding
			// Pixels
				padding-top: 2px;
				padding-right: 4px;
				padding-left: 16px;

			// Rem
				padding-top: 0.125rem;
				padding-right: 0.25rem;
				padding-left: 1rem;

Each property is stored in a list.
+ Pass multiple properties to output them with same values.
+ Properties are output in the order you list them in.

Each unit is stored in a list.
+ Pass multiple unit types for fallback purposes.
+ Units are output in the order you list them in.

Skip values.
+ Skip values while keeping the shorthand syntax. Any value you don't want to re-define, just place an x.

Functionality has not been lost.
+ You can make things important just like you normally would. No '!' required.
+ You can still pass text values like auto and inherit, along with any other text string you throw in there.

Added support for the position property.
+ Just add 'position' to the properties and enter in values for top, right, bottom, and left as you would expect.

##Functions
		margin: em(1);
		margin: rem(1);
		margin: px(1);
		margin: pct(1);

There are 4 functions. They serve little purpose other than provide small coesmetic changes to your code that may make it more readable.

1. The em function takes a pixel value and convert it to em.
1. The rem function takes a pixel value and convert it to rem.
1. The px function takes a pixel value and appends a 'px' to the end.
1. The pct function takes a percentage value formatted as a decimal and converts it to a percentage.


##Notes
There are 2 other functions, convert and join that I used for LifeSaver things, not for usage. These are common names and may (most likely will) conflict with other Sass scripts or libraries. Luckily, LifeSaver is just a single small file, and you could do a find / replace on these 2 functions if you have any problems.

## Changelog
August 11, 2014
+ Used convert function in unit function

July 27, 2014
+ Changed $properties to $property-list

July 21, 2014
+ Multiple Properties

July 20, 2014
+ Commited Project

