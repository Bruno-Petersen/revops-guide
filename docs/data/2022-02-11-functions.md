---
layout: default
title: Useful Functions
date: 2021-02-12 20:46:17 +0100
nav_order: 7
parent: Data
permalink: /useful-functions.html
---

# Useful Functions

This page is a collection of functions I have found to be useful when working with Google sheets and Looker. 

## Google Sheets
### IFERROR
```
IFERROR(value, [value_if_error])
# A collapsible section with markdown

e.g. IFERROR(A1,"Error in cell A1")
IFERROR(A2)

•	value - The value to return if value itself is not an error.
•	value_if_error - [ OPTIONAL - blank by default ] - The value the function returns if value is an error.

```
<details>
  <summary>More Detail</summary>
  ```
  e.g. IFERROR(A1,"Error in cell A1")
IFERROR(A2)

•	value - The value to return if value itself is not an error.
•	value_if_error - [ OPTIONAL - blank by default ] - The value the function returns if value is an error.
  ```
</details>

### VLOOKUP
```
VLOOKUP(search_key, range, index, [is_sorted])

•	search_key - The value to search for. For example, 42, "Cats", or I24.
•	range - The range to consider for the search. The first column in the range is searched for the key specified in search_key.
•	index - The column index of the value to be returned, where the first column in range is numbered 1.
•	If index is not between 1 and the number of columns in range, #VALUE! is returned.
•	is_sorted - [TRUE by default] - Indicates whether the column to be searched (the first column of the specified range) is sorted. FALSE is recommended in most cases.
•	It’s recommended to set is_sorted to FALSE. If set to FALSE, an exact match is returned. If there are multiple matching values, the content of the cell corresponding to the first value found is returned, and #N/A is returned if no such value is found.
•	If is_sorted is TRUE or omitted, the nearest match (less than or equal to the search key) is returned. If all values in the search column are greater than the search key, #N/A is returned.

```

### SUBSTITUTE
```
SUBSTITUTE(text_to_search, search_for, replace_with, [occurrence_number])
e.g. SUBSTITUTE("search for it","search for","Google")
SUBSTITUTE(A2,"new york","New York")
SUBSTITUTE("January 2, 2012",2,3,1)

•	text_to_search - The text within which to search and replace.
•	search_for - The string to search for within text_to_search.
•	search_for will match parts of words as well as whole words; therefore a search for "vent" will also replace text within "eventual".
•	replace_with - The string that will replace search_for.
•	occurrence_number - [ OPTIONAL ] - The instance of search_for within text_to_search to replace with replace_with. By default, all occurrences of search_for are replaced; however, if occurrence_number is specified, only the indicated instance of search_for is replaced.

```

### REGEXMATCH
```
REGEXMATCH(text, regular_expression)

•	text - The text to be tested against the regular expression.
•	regular_expression - The regular expression to test the text against.

```


### SPLIT
```
SPLIT(text, delimiter, [split_by_each], [remove_empty_text])

•	text - The text to divide.
•	delimiter - The character or characters to use to split text.
•	By default, each character in delimiter is considered individually, e.g. if delimiter is "the", then text is divided around the characters "t", "h", and "e". Set split_by_each to FALSE to turn off this behavior.
•	split_by_each - [ OPTIONAL - TRUE by default ] - Whether or not to divide text around each character contained in delimiter.
•	remove_empty_text  - [ OPTIONAL - TRUE by default ] - Whether or not to remove empty text messages from the split results. The default behavior is to treat consecutive delimiters as one (if TRUE). If FALSE, empty cells values are added between consecutive delimiters.

```

### REPLACE
```
REPLACE(text, position, length, new_text)
e.g. REPLACE("Spreadsheets", 1, 6, "Bed")

•	text - The text, a part of which will be replaced.
•	position - The position where the replacement will begin (starting from 1).
•	length - The number of characters in the text to be replaced.
•	new_text - The text which will be inserted into the original text.

```

### INDIRECT
```
INDIRECT(cell_reference_as_string, [is_A1_notation])

•	cell_reference_as_string - A cell reference, written as a string with surrounding quotation marks.
•	is_A1_notation - [OPTIONAL - TRUE by default] - Indicates if the cell reference is in A1 notation or R1C1 notation.
Returns the contents of the reference which can be a cell or an area.
```


### IMPORTRANGE
```
=IMPORTRANGE("https://docs.google.com/spreadsheets/d/abcd123abcd123", "sheet1!A1:C10")

If you keep data in separate Google Sheets, copy a range of data from one spreadsheet to another with the IMPORTRANGE function.
For example, you may track quarterly sales data for a product in a different spreadsheet for each region. To combine all that quarterly sales data, copy the data from each region's spreadsheet into a single spreadsheet using IMPORTRANGE.

```


### TRANSPOSE
```
TRANSPOSE(array_or_range)
e.g. TRANSPOSE({1,2;3,4;5,6})
TRANSPOSE(A2:F9)

•	array_or_range - The array or range whose rows and columns will be swapped.

```

### DATE
```
DATE(year, month, day)
e.g. DATE(1969,7,20)
DATE(A2,B2,C2)

•	year - The year component of the date.
•	month - The month component of the date.
•	day - The day component of the date.

TO_DATE(value)
e.g. TO_DATE(25405)
TO_DATE(A2)
TO_DATE(40826.4375)

•	value - The argument or reference to a cell to be converted to a date.
•	If value is a number or a reference to a cell containing a numeric value, TO_DATE returns value converted to a date, interpreting value as number of days since December 30, 1899.
• Negative values are interpreted as days before this date, and fractional values indicate time of day past midnight.
•	If value is not a number or a reference to a cell containing a numeric value, TO_DATE returns value without modification.


YEAR(date)
e.g. YEAR(DATE(1969,7,20))
YEAR(A2)
YEAR(40909)

•	date - The date from which to calculate the year. Must be a cell reference to a cell containing a date, a function returning a date type, or a number.


MONTH(date)
e.g. MONTH(DATE(1969, 7, 20))
MONTH(A2)
MONTH(40909)
MONTH("7/20/1969")

•	date - The date from which to extract the month. Must be a reference to a cell containing a date, a function returning a date type, or a number.

DAY(date)
e.g. DAY(DATE(1969,7,20))
DAY(A2)
DAY(40909)
DAY("7/20/1969")

•	date - The date from which to extract the day. Must be a reference to a cell containing a date, a function returning a date type, or a number.

```

### DATEDIFF
```
DATEDIF(start_date, end_date, unit)
e.g. DATEDIF(DATE(1969, 7, 16), DATE(1969, 7, 24), "D")
DATEDIF(A1, A2, "YM")
DATEDIF("7/16/1969", "7/24/1969", "Y")


•	start_date - The start date to consider in the calculation. Must be a reference to a cell containing a DATE, a function returning a DATE type, or a number.
•	end_date - The end date to consider in the calculation. Must be a reference to a cell containing a DATE, a function returning a DATE type, or a number.
•	unit - A text abbreviation for unit of time. For example,"M" for month. Accepted values are "Y","M","D" ,"MD","YM","YD".
•	"Y": the number of whole years between start_date and end_date.
•	"M": the number of whole months between start_date and end_date.
•	"D": the number of days between start_date and end_date.
•	"MD": the number of days between start_date and end_date after subtracting whole months.
•	"YM": the number of whole months between start_date and end_date after subtracting whole years.
•	"YD": the number of days between start_date and end_date, assuming start_date and end_date were no more than one year apart.
```

### FILTER
```
FILTER(range, condition1, [condition2, ...])
e.g. FILTER(A2:B26, A2:A26 > 5, D2:D26 < 10)
FILTER(A2:C5, {TRUE; TRUE; FALSE; TRUE})
FILTER(A2:B10, NOT(ISBLANK(A2:A10)))

•	range - The data to be filtered.
•	condition1 - A column or row containing true or false values corresponding to the first column or row of range, or an array formula evaluating to true or false.
•	condition2 ... - [ OPTIONAL ] - Additional rows or columns containing boolean values TRUE or FALSE indicating whether the corresponding row or column in range should pass through FILTER. Can also contain array formula expressions which evaluate to such rows or columns. All conditions must be of the same type (row or column). Mixing row conditions and column conditions is not permitted.
•	condition arguments must have exactly the same length as range.

Returns a filtered version of the source range, returning only rows or columns that meet the specified conditions.
```

### UNIQUE
```
UNIQUE(range)
e.g. UNIQUE(A2:B26)
UNIQUE({1, 2; 3, 4; 5, 6})

	•	range - The data to filter by unique entries.

Returns unique rows in the provided source range, discarding duplicates. Rows are returned in the order in which they first appear in the source range.
```

### SPARKLINE
```
SPARKLINE(data, [options])
e.g. SPARKLINE(A1:F1)
SPARKLINE(A2:E2,{"charttype","bar";"max",40})
SPARKLINE(A2:E2,A4:B5)
SPARKLINE(A1:A5, {"charttype","column"; "axis", true; "axiscolor", "red"})


•	data - The range or array containing the data to plot.
•	options - [ OPTIONAL ] - A range or array of optional settings and associated values used to customize the chart.
•	If referencing a range, options should be two cells wide where the first cell is the option and the second cell is the value that option is set to.
•	The "charttype" option defines the type of chart to plot, which includes:
•	"line" for a line graph (the default)
•	"bar" for a stacked bar chart
•	"column" for a column chart
•	"winloss" for a special type of column chart that plots 2 possible outcomes: positive and negative (like a coin toss, heads or tails).
•	For line graphs:
•	"xmin" sets the minimum value along the horizontal axis.
•	"xmax" sets the maximum value along the horizontal axis.
•	"ymin" sets the minimum value along the vertical axis.
•	"ymax" sets the maximum value along the vertical axis.
•	"color" sets the color of the line.
•	"empty" sets how to treat empty cells. Possible corresponding values include: "zero" or "ignore".
•	"nan" sets how to treat cells with non-numeric data. Options are: "convert" and "ignore".
•	"rtl" determines whether or not the chart is rendered right to left. Options are true or false.
•	"linewidth" determines how thick the line will be in the chart. A higher number means a thicker line.
•	For column and winloss sparklines:
•	"color" sets the color of chart columns.
•	"lowcolor" sets the color for the lowest value in the chart
•	"highcolor" sets the color for the higest value in the chart
•	"firstcolor" sets the color of the first column
•	"lastcolor" sets the color of the last column
•	"negcolor" sets the color of all negative columns
•	"empty" sets how to treat empty cells. Possible corresponding values include: "zero" or "ignore".
•	"nan" sets how to treat cells with non-numeric data. Options are: "convert" and "ignore".
•	"axis" decides if an axis needs to be drawn (true/false)
•	"axiscolor" sets the color of the axis (if applicable)
•	"ymin" sets the custom minimum data value that should be used for scaling the height of columns (not applicable for win/loss)
•	"ymax" sets the custom maximum data value that should be used for scaling the height of columns (not applicable for win/loss)
•	"rtl" determines whether or not the chart is rendered right to left. Options are true or false.
•	For bar charts:
•	"max" sets the maximum value along the horizontal axis.
•	"color1" sets the first color used for bars in the chart.
•	"color2" sets the second color used for bars in the chart.
•	"empty" sets how to treat empty cells. Possible corresponding values include: "zero" or "ignore".
•	"nan" sets how to treat cells with non-numeric data. Options are: "convert" and "ignore".
•	"rtl" determines whether or not the chart is rendered right to left. Options are true or false.

•	Colors can be written using their names (e.g., "green") or as a hex code (e.g., "#3D3D3D").
•	To modify the color of a line chart, change the font color of the cell.


```

## Looker
### Adding an Image to Looker
`<img src="https://your.website.com/your-image.jpg" width="100" height="100"/>`

### Forcing Table Calculations onto an Axis
```sql
-- A calculation is typically plotted as a dimension if no measures are involved in the formula. We can make a table calculation behave as a measure by including a measure in the calculation's expression. The key is making sure the measure won't affect the value of the original dimension.

-- For a numerical field, the calculation will be:
${mydimension} + (0 * ${mymeasure})

-- For a string field, the calculation will involve
if(is_null(${mymeasure}),${string_dimension},${string_dimension})
```

### Summing across a pivoted value
```sql
sum(pivot_row(${metric}))
```

### Last day of the month
```sql
-- Determine whether a date is on the last day of the month: - Dimension

extract_days(add_days(1,${date})) = 1

-- The logic is “tomorrow’s day of month is 1”. That is, the day after the last day of the month will always be the 1st of a month.

extract_days(
        add_days(-1, 
            date(
                extract_years(add_months(1, ${date})), extract_months(add_months(1, ${date})), 
                1)
                )
            )

-- 1	First, assume ${date} is January 10, 2020.
-- 2	Then extract_years(add_months(1, ${date})) is the year of the next month, which is 2020. Let's call this year.
-- 3	Similarly, extract_months(add_months(1, ${date})) returns the month number of the next month, which is 2. Call this month.
-- 4	Now date([year],[month],1) returns 2/1/2020, the first day of next month. We'll call this next_month.
-- 5	Next, add_days(-1, [next_month]) travels one day backwards, to reach the last day of this month, which in our example returns January 31, 2020. Call this last_day.
-- 6	Finally, extract_days([last_day]) returns the day number of last_day. In this example, this returns 31, the number of days in January!


```
### Last day of the Week
```sql
--  useful when working with snapshots grouped by week
--  Returns the day of the week (0-indexed) e.g. 6 for Sunday.

mod(
    diff_days(date(2008,01,01), 
    ${date}) + 1, 7
    )

```
### Rolling Average
```sql
mean(offset_list(${field_being_averaged},0,7))

-- offset_list takes three arguments: the column from which you want to grab the offset values, how far from the current row you want to start the offset, and how long you want the offset list to be. You can change the number of rows (the last argument of the function, or 7 in this case) to increase your window, and you can change where the window will start (the second to last argument of the function, or 0). Positive numbers will move down, and negative numbers will move up. So to get the average of the ten values above the current row, you can use:
mean(offset_list(${value},-10,10))

-- We can adjust our table calc to set nulls to 0s, using something like 
mean(offset_list(coalesce(${field_being_averaged}, 0),0,3)) 
-- to replace nulls with 0s. The average would then be 6/3 = 2.



-- ignoring null values
if(
    is_null(${total_amount}),
    null, 
    mean(offset_list(${total_amount}, 1, 13))
   )
```


### Defining Cases
```sql
if(is_null(${some_field}),
    case(
      when(
        diff_days(
          to_date("2022-01"),
          ${date_x}) = 0, 113,
      when(
        diff_days(
          to_date("2022-02"),
          ${date_x}) = 0, 215),

      when(
        diff_days(
          to_date("2022-03"),
          ${date_x}) = 0, 123),
      null),
    null)
)
```