---
title: Multi-Directional Tables
status: draft
technologies: HTML5
order: 3
wcag_techniques: 
  - H51
---

A multi directional table usually has one header row and a header column. Most of the times, they are in the first row and column of the table. They don’t span columns/rows.

In addition to mark table headers up using `<th>` elements it is necessary to use the `scope` attribute on these tables. It’s used to declare the direction of the header cell. A `scope` value of `row` or `col` denotes that the header cell applies to the entire row or column, respectively. The direction of a table heading is especially important when the content in the table isn’t easy to distinguish.

Additionally, you can use add a [caption](caption-summary.html) to identify the table in a document, which is particularly useful for screen-reader users browsing the web page in “tables mode” where they can navigate from table to table. The caption is a way to meet WCAG 2.0 requirements in specific situations.

## Table with ambiguous data
{:.ex}

In this example the first and last names and cities are impossible to tell apart from one another. By using the `scope` element the header cells are clearly associated with their respective column.

{::nomarkdown}
<%= sample_start %>

<p><strong>Teddy bear collectors:</strong></p>
<table>
  <tr>
    <th scope="col">Last Name</th>
    <th scope="col">First Name</th>
    <th scope="col">City</th>
  </tr>
  <tr>
    <td>John</td>
    <td>Martin</td>
    <td>Henry</td>
  </tr>
  <tr>
    <td>Shawn</td>
    <td>Oliver</td>
    <td>George</td>
  </tr>
  <tr>
    <td>Wilson</td>
    <td>Kelly</td>
    <td>Hope</td>
  </tr>
</table>

<%= sample_end %>
{:/nomarkdown}

{::nomarkdown}
<%= code_start %>
{:/nomarkdown}

~~~ html
<table>
  <tr>
    <th scope="col">Last Name</th>
    <th scope="col">First Name</th>
    <th scope="col">City</th>
  </tr>
  <tr>
    <td>John</td>
    <td>Martin</td>
    <td>Henry</td>
  </tr>
  <tr>
    <td>Shawn</td>
    <td>Oliver</td>
    <td>George</td>
  </tr>
  <tr>
    <td>Wilson</td>
    <td>Kelly</td>
    <td>Hope</td>
  </tr>
</table>
~~~

{::nomarkdown}
<%= code_end %>
{:/nomarkdown}

## Table with header cells in one column only
{:.ex}

This example has `<th>` elements for all cells in the left column of a table. As the heading cells are read in every line, the `scope` attribute with a value of `row` should be used on each `<th>` cell to ensure that it cannot be mistaken as a header for other cells in the same column. In the table below, Belgium should not be mistaken as the heading for France, Holland, etc.

{::nomarkdown}
<%= sample_start %>

<table>
  <caption>
    Capital cities
  </caption>
  <tr>
    <th scope="row">Belgium</th>
    <td>Brussels</td>
  </tr>
  <tr>
    <th scope="row">France</th>
    <td>Paris</td>
  </tr>
  <tr>
    <th scope="row">Holland</th>
    <td>Amsterdam</td>
  </tr>
  <tr>
    <th scope="row">Luxembourg</th>
    <td>Luxembourg</td>
  </tr>
  <tr>
    <th scope="row">Spain</th>
    <td>Madrid</td>
  </tr>
  <tr>
    <th scope="row">UK</th>
    <td>London</td>
  </tr>
</table>

<%= sample_end %>
{:/nomarkdown}

A header row can be used to clarify the table even further:

{::nomarkdown}
<%= sample_start %>

<table>
  <caption>
    Capital cities
  </caption>
  <tr>
    <th scope="col">Country</th>
    <th scope="col">Capital city</th>
  </tr>
  <tr>
    <th scope="row">Belgium</th>
    <td>Brussels</td>
  </tr>
  <tr>
    <th scope="row">France</th>
    <td>Paris</td>
  </tr>
  <tr>
    <th scope="row">Holland</th>
    <td>Amsterdam</td>
  </tr>
  <tr>
    <th scope="row">Luxembourg</th>
    <td>Luxembourg</td>
  </tr>
  <tr>
    <th scope="row">Spain</th>
    <td>Madrid</td>
  </tr>
  <tr>
    <th scope="row">UK</th>
    <td>London</td>
  </tr>
</table>

<%= sample_end %>
{:/nomarkdown}

{::nomarkdown}
<%= code_start %>
{:/nomarkdown}

~~~ html
<table>
  <caption>Capital cities</caption>
  <tr>
    <th scope="col">Country</th>
    <th scope="col">Capital city</th>
  </tr>
  <tr>
    <th scope="row">Belgium</th>
    <td>Brussels</td>
  </tr>
  <tr>
    <th scope="row">France</th>
    <td>Paris</td>
  </tr>
  <tr>
    <th scope="row">Holland</th>
    <td>Amsterdam</td>
  </tr>
  […]
</table>
~~~

{::nomarkdown}
<%= code_end %>
{:/nomarkdown}

[Full code Example “Table with header cells in one column only”](examples/scope-simple.html)

## Table with header cells in the top row and first column
{:.ex}

This table of opening times has header information contained in both the top row and the first column. All header cells are marked up as `<th>` cells, additionally we add `scope` attributes with the values `col` (to the top row header cells) and `row` (to the first column header cells).

{::nomarkdown}
<%= sample_start %>

<p><strong>Delivery slots:</strong></p>

<table>
	<tr>
		<td></td>
		<th scope="col">Monday</th>
		<th scope="col">Tuesday</th>
		<th scope="col">Wednesday</th>
		<th scope="col">Thursday</th>
		<th scope="col">Friday</th>
	</tr>
	<tr>
		<th scope="row">09:00 - 11:00</th>
		<td>Closed</td>
		<td>Open</td>
		<td>Open</td>
		<td>Closed</td>
		<td>Closed</td>
	</tr>
	<tr>
		<th scope="row">11:00 - 13:00</th>
		<td>Open</td>
		<td>Open</td>
		<td>Closed</td>
		<td>Closed</td>
		<td>Closed</td>
	</tr>
	<tr>
		<th scope="row">13:00 - 15:00</th>
		<td>Open</td>
		<td>Open</td>
		<td>Open</td>
		<td>Closed</td>
		<td>Closed</td>
	</tr>
	<tr>
		<th scope="row">15:00 - 17:00</th>
		<td>Closed</td>
		<td>Closed</td>
		<td>Closed</td>
		<td>Open</td>
		<td>Open</td>
	</tr>
</table>

<%= sample_end %>
{:/nomarkdown}

{::nomarkdown}
<%= code_start %>
{:/nomarkdown}

~~~ html
<table>
	<tr>
		<td></td>
		<th scope="col">Monday</th>
		<th scope="col">Tuesday</th>
		<th scope="col">Wednesday</th>
		<th scope="col">Thursday</th>
		<th scope="col">Friday</th>
	</tr>
	<tr>
		<th scope="row">09:00 - 11:00</th>
		<td>Closed</td>
		<td>Open</td>
		<td>Open</td>
		<td>Closed</td>
		<td>Closed</td>
	</tr>
	<tr>
		<th scope="row">11:00 - 13:00</th>
		<td>Open</td>
		<td>Open</td>
		<td>Closed</td>
		<td>Closed</td>
		<td>Closed</td>
	</tr>
	[…]
</table>
~~~

{::nomarkdown}
<%= code_end %>
{:/nomarkdown}

[Full code for “Table with header cells in the top row and first column”](examples/headertoprowfirstcol.html)

## Table with an offset column of header cells
{:.ex}

In this table, the row header cells are in the second column rather than the first. The `<th>` cells in the second column have `scope="row"`  to ensure that data cells on both sides are correctly associated.

{::nomarkdown}
<%= sample_start %>

<table class="numbers">
  <caption>
    Holidays taken in the last six months
  </caption >
  <thead>
    <tr>
      <th scope="col">ID</th>
      <th scope="col">Name</th>
      <th scope="col">July</th>
      <th scope="col">August</th>
      <th scope="col">September</th>
      <th scope="col">October</th>
      <th scope="col">November</th>
      <th scope="col">December</th>
    </tr>
  </thead>

  <tbody>
    <tr>
      <td>215</td>
      <th scope="row">Abel</th>
      <td>5</td>
      <td>2</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>3</td>
    </tr>

    <tr>
      <td>231</td>
      <th scope="row">Annette </th>
      <td>0</td>
      <td>5</td>
      <td>3</td>
      <td>0</td>
      <td>0</td>
      <td>6</td>
    </tr>

    <tr>
      <td>173</td>
      <th scope="row">Bernard</th>
      <td>2</td>
      <td>0</td>
      <td>0</td>
      <td>5</td>
      <td>0</td>
      <td>0</td>
    </tr>

    <tr>
      <td>141</td>
      <th scope="row">Gerald</th>
      <td>0</td>
      <td>10</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>8</td>
    </tr>

    <tr>
      <td>99</td>
      <th scope="row">Michael</th>
      <td>8</td>
      <td>8</td>
      <td>8</td>
      <td>8</td>
      <td>0</td>
      <td>4</td>
    </tr>
  </tbody>
</table>

<%= sample_end %>
{:/nomarkdown}

{::nomarkdown}
<%= code_start %>
{:/nomarkdown}

~~~ html
[…]
<tr>
  <td>215</td>
  <th scope="row">Abel</th>
  <td>5</td>
  <td>2</td>
  <td>0</td>
  <td>0</td>
  <td>0</td>
  <td>3</td>
</tr>
[…]
~~~

{::nomarkdown}
<%= code_end %>
{:/nomarkdown}

[Full code for “Table with an offset column of header cells”](examples/scope-offset.html)