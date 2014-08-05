LifeSaver
=========

A Sass mixin that allows for quicker changes to units and values.


<h1>The Rundown</h1>
<h2>Mixin</h2>
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

	// Output Indented and Commented for Demonstration
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

<ol>
  <li>Each property is stored in a list.</li>
    <ul>
      <li>Pass multiple properties to output them with same values.</li>
      <li>Properties are output in the order you list them in.</li>
    </ul>
    <br>

  <li>Each unit is stored in a list.<li>
    <ul>
      <li>Pass multiple unit types for fallback purposes.</li>
      <li>Units are output in the order you list them in.</li>
    </ul>
    <br>

  <li>Skip values.</li>
    <ul>
      <li>Skip values while keeping the shorthand syntax. Any value you don't want to re-define, place an x.</li>
    </ul>
    <br>

  <li>Functionality has not been lost.</li>
    <ul>
      <li>You can make things important just like you normally would. No '!' required.</li>
      <li>You can still pass text values like auto and inherit, along with any other text string you throw in there.</li>
    </ul>
    <br>

  <li>Added support for the position property.</li>
    <ul>
      <li>Add 'position' to the properties and enter in values for top, right, bottom, and left as you would expect.</li>
    </ul>
</ol>

<h2>Functions</h2>
	margin: em( 1 );
	margin: rem( 1 );
	margin: px( 1 );
	margin: pct( 1 );

There are 4 functions. They serve little purpose other than provide small coesmetic changes to your code that may make it more readable.

1. The em function takes a pixel value and convert it to em.
1. The rem function takes a pixel value and convert it to rem.
1. The px function takes a pixel value and appends a 'px' to the end.
1. The pct function takes a percentage value formatted as a decimal and converts it to a percentage.


<h2>Notes</h2>
There are 2 other functions, convert and join that I used for LifeSaver things, not for usage. These are common names and may (most likely will) conflict with other Sass scripts or libraries. Luckily, LifeSaver is just a single small file, and you could do a find / replace on these 2 functions if you have any problems.

<h2>Changelog</h2>
<ul>
  <li>July 27, 2014</li>
    <ul><li>Changed $properties to $property-list</li></ul>
    <br>

  <li>July 21, 2014</li>
    <ul><li>Multiple Properties</li></ul>
    <br>
  
  <li>July 20, 2014</li>
    <ul><li>Commited Project</li></ul>
    <br>
</ul>
