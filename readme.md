# HAML-Py

HAML-Py (pronounced "haml pie") is a tool for Django developers who want to use a HAML like syntax for their templates.
HAML-Py is not a template engine in itself but simply a compiler which will convert HamlPy files into templates that Django can understand.


But wait, what is HAML?  HAML is an incredible template engine written in Ruby used a lot in the Rails community.  You can read more about it [here](http://www.haml-lang.com "HAML Home")

## Syntax

Almost all of the XHTML syntax of HAML is preserved.  

	#profile
		.left.column
			#date 2010/02/18
			#address Toronto, ON
		.right.column
			#bio Jesse Miller
			
turns into..

	<div id='profile'>
		<div class='left column'>
			<div id='date'>2010/02/18</div>
			<div id='address'>Toronto, ON</div>
		</div>
		<div class='right column'>
			<div id='bio'>Jesse Miller</div>
		</div>
	</div>
	

The main difference is instead of interpretting Ruby, or even Python we instead can create Django Tags and Variables

	%ul#atheletes
		- for athelete in athelete_list
		%li.athelete= athelete.name
		- endfor

turns into..

	<ul id='atheletes'>
		{% for athelete in athelete_list %}
		<li class='athelete'>{{ athelete.name }}</li>
		{% endfor %}
	</ul>
	
## Reference

Check out the wiki for a complete reference and more examples.

## Status

HAML-Py currently cannot:

- Auto close Django tags.  This can make indentation a little confusing sometimes.
- Actually output nicely indented templates.  They will actually be stripped of white space.

