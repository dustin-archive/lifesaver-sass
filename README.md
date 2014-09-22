LifeSaver
=========

A Sass mixin that allows for quicker changes to units and values.


##Mixin
		@include ls( [properties], [values], [units], [important] );

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

All the arguments are treated as lists.

Properties
+ Pass multiple properties to output them with same values.
+ Properties are output in the order you list them in.

Units
+ Pass multiple unit types for fallback purposes.
+ Units are output in the order you list them in.

Skips
+ Skip values while keeping the shorthand syntax. Any value you don't want to re-define, just place an x.

Functionality
+ You can make things important just like you normally would. No '!' required.
+ You can still pass text values like auto and inherit, along with any other text string you throw in there.

Position Property
+ Just add 'position' to the properties and enter in values for top, right, bottom, and left as you would expect.

##Functions
		margin: em(1);
		margin: rem(1);
		margin: px(1);
		margin: pct(1);

There are 4 regular functions. They serve little purpose other than provide mostly coesmetic changes to your code.

1. The em function takes a pixel value and converts it to em.
1. The rem function takes a pixel value and converts it to rem.
1. The px function takes a pixel value, rounds it to the nearest whole number, and appends a 'px' to the end.
1. The pct function takes a percentage value formatted as a decimal and converts it to a percentage with a percent sign.


##Notes
The function 'convert' might conflict with other Sass stuff you're using. Convert is a common name for things, but I couldn't think of anything better.
