LifeSaver
=========

A Sass mixin that allows for quicker changes to unit values.


<h1>The Rundown</h1>
<h2>Mixin</h2>
	@include ls( property, values, units, important );

	// Input
	@include ls( margin, 2 4 x 16, px rem );

	// Output
	margin-top: 2px;
	margin-right: 4px;
	margin-left: 16px;
	margin-top: 0.125rem;
	margin-right: 0.25rem;
	margin-left: 1rem;

+ Each paremter creates an array.
	+ This means you can pass multiple properties in this mixin to generate two properties with the same values. You could also pass multiple unit types for fallback purposes.
+ You can skip values.
	+ You can skip values while keeping the shorthand syntax. Any value you don't want to re-define, just place an x.
+ You can make things important.
	+ Just like you normally would. No '!' required.
+ You can still pass text values.
	+ Basic functionality is still there. Auto and inherit still work perfect, along with any other text string you throw in there.

<h2>Functions</h2>
	margin: em( 1 );
	margin: rem( 1 );
	margin: px( 1 );
	margin: pct( 1 );

There are 4 functions. They serve little purpose other than provide small coesmetic changes to your code that may make it more readable.

+ The em and rem functions take pixel values and convert them to em or rems.
+ The px function takes a pixel value and appends a 'px' to the end.
+ The pct function takes a percentage value formatted as a decimal and converts it to a percentage.

<h2>Notes</h2>
There are 2 other functions, convert and join that I used for LifeSaver things, not for usage. These are common names and may (most likely will) conflict with other Sass scripts or libraries. Luckily, LifeSaver is just a single small file, and you could do a find / replace on these 2 functions if you have any problems.

## Changelog
+ July 20, 2014
	+ Commited Project
