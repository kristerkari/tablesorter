tablesorter is a jQuery plugin for turning a standard HTML table with THEAD and TBODY tags into a sortable table without page refreshes.
tablesorter can successfully parse and sort many types of data including linked data in a cell.

### Documentation

* See the [full documentation](http://mottie.github.com/tablesorter/docs/).
* All of the [original document pages](http://tablesorter.com/docs/) have been included.
* Information from my blog post on [undocumented options](http://wowmotty.blogspot.com/2011/06/jquery-tablesorter-missing-docs.html) and lots of new demos have also been included.
* Change log moved from included text file into the [wiki documentation](https://github.com/Mottie/tablesorter/wiki/Change).

### Demos

* [Basic alpha-numeric sort Demo](http://mottie.github.com/tablesorter/).
* Links to demo pages can be found within the main [documentation](http://mottie.github.com/tablesorter/docs/).
* More demos & playgrounds - updated in the [wiki pages](https://github.com/Mottie/tablesorter/wiki).

### Features

* Multi-column sorting.
* Multi-tbody sorting - see the [options](http://mottie.github.com/tablesorter/docs/index.html#options) table on the main document page.
* Parsers for sorting text, alphanumeric text, URIs, integers, currency, floats, IP addresses, dates (ISO, long and short formats) &amp; time. [Add your own easily](http://mottie.github.com/tablesorter/docs/example-parsers.html).
* Support for ROWSPAN and COLSPAN on TH elements.
* Support secondary "hidden" sorting (e.g., maintain alphabetical sort when sorting on other criteria).
* Extensibility via [widget system](http://mottie.github.com/tablesorter/docs/example-widgets.html).
* Cross-browser: IE 6.0+, FF 2+, Safari 2.0+, Opera 9.0+.
* Small code size.
* Works with jQuery 1.2.6+.

### Licensing

* Copyright (c) 2007 Christian Bach.
* Original examples and docs at: [http://tablesorter.com](http://tablesorter.com).
* Dual licensed under the [MIT](http://www.opensource.org/licenses/mit-license.php) and [GPL](http://www.gnu.org/licenses/gpl.html) licenses.

### Change Log

View the [complete listing here](https://github.com/Mottie/tablesorter/wiki/Change).

#### Version 2.3.1 (5/8/2012)

* Fixed an issue where header & metadata settings would ignore `sorter:false` inappropriately.
* Fixed minified version:
  * Apparently Dean Edwards packer now breaks the minified version, so I switched to using Uglify.
  * I prefer Google Closure Complier but it completely removes the eval needed to get multi-column sorting to work unless the "Whitespace only" mode is used and results in a file 2k larger than the Uglify version.
* Modified header settings to now check for settings with the following priority: jQuery data > metadata > headers option > header class name > overall option. Added:
  * [`dateFormat`](http://mottie.github.com/tablesorter/docs/index.html#dateformat)
  * [`lockedOrder`](http://mottie.github.com/tablesorter/docs/index.html#headers) - no demo.
  * [`sortInitialOrder`](http://mottie.github.com/tablesorter/docs/index.html#sortinitialorder)
  * [`filter`](http://mottie.github.com/tablesorter/docs/index.html#headers) widget - no demo.
* Added the ability to set the `sortList` via jQuery data. See the updated [sortList](http://mottie.github.com/tablesorter/docs/index.html#sortlist) documents on how to use it 
* Fixed date parsers (isoDate, usLongDate, shortDate and time) which did not handle empty cell data properly.

#### Version 2.3 (5/8/2012)

* Added ability to sort all columns under a header cell that spans multiple columns.
  * Previously clicking on the header cell would only sort the left-most column.
  * Added a [demo](http://mottie.github.com/tablesorter/docs/example-header-column-span.html).
* Added support for "Content-type: application/xhtml+xml". Fix for [issue #62](https://github.com/Mottie/tablesorter/issues/62). Thanks to [MelTraX](https://github.com/MelTraX) for the fix!
* Added `delayInit` option:
  * This option delays parsing of all table cell data until the user initializes a sort.
  * This speeds up the initialization process of very large tables, but the data still needs to be parsed, so the delay is still present upon initial sort.
  * Enhancement suggested by [MelTraX](https://github.com/MelTraX) in [issue #66](https://github.com/Mottie/tablesorter/issues/66).
* Column parsers & settings can now be set using jQuery data.
  * This setting has a higher priority than metadata: jQuery data > metadata > headers option > header class name > overall setting.
  * This applies to the [parsers](http://mottie.github.com/tablesorter/docs/index.html#parsers), [stringTo](http://mottie.github.com/tablesorter/docs/index.html#stringto) and [emptyTo](http://mottie.github.com/tablesorter/docs/index.html#emptyto) options.
* Nested tables will no longer be targeted inappropriately. Fix for [issue #65](https://github.com/Mottie/tablesorter/issues/65). Thanks to [MelTraX](https://github.com/MelTraX) for sharing some code!
* Reordered parsers to detect other numeric parsers before the general one. Fix for [issue #64](https://github.com/Mottie/tablesorter/issues/64).
* Completed minor document corrections, general code cleanup, optimization and removal of a global variable.

#### Version 2.2.2 (5/4/2012)

* Sorting algorithm replaced with naturalSort.js. Suggestion by [alisonatwork](https://github.com/alisonatwork) in [issue #58](https://github.com/Mottie/tablesorter/issues/58).
* Non-sorting tbodies with "tablesorter-infoOnly" class name should no longer sort internal rows.
* Added a [multiple tbodies sorting demo](http://mottie.github.com/tablesorter/docs/example-multiple-tbodies.html).

#### Version 2.2.1 (5/4/2012)

* Widgets should now apply properly while the pager is active. Fix for [issue #60](https://github.com/Mottie/tablesorter/issues/60).

#### Version 2.2 (5/3/2012)

* Multiple tbody sorting:
  * Each tbody within a table will now sort separately.
  * To add in a non-sorting tbody, add the class "tablesorter-infoOnly", modifiable by the new `cssInfoBlock` option
  * See the main document's [options table](http://mottie.github.com/tablesorter/docs/index.html#options) for an example.
  * **NOTE** The pager plugin will only be applied to the first tbody as always. I may work on modifying this behavior in the future, if I can figure out the best implementation.
* Added `ignoreCase` option:
  * When `true` (default), text character case is ignored during sorting.
  * If `false`, upper case characters will sort before lower case characters.
* Added `textSorter` option:
  * This option allows using a custom text sorter (e.g. naturalSort.js).
  * Suggestion by [alisonatwork](https://github.com/alisonatwork) in [issue #58](https://github.com/Mottie/tablesorter/issues/58).
  * [New demo](http://mottie.github.com/tablesorter/docs/example-option-custom-sort.html) added.
* Modified `sortLocaleCompare` option:
  * This option no longer switches the sort to use the `String.localeCompare` method.
  * When this option is `true`, the text parsed from table cells will convert accented characters to their equivalent to allow the alphanumeric sort to properly sort.
  * If `false` (default), any accented characters are treated as their value in the standard unicode order.
  * The following characters are replaced for both upper and lower case (information obtained from [sugar.js sorting equivalents](http://sugarjs.com/sorting) table):
     * `áàâãä` replaced with `a`
     * `ç` replaced with `c`
     * `éèêë` replaced with `e`
     * `íìİîï` replaced with `i`
     * `óòôõö` replaced with `o`
     * `úùûü` replaced with `u`
     * `ß` replaced with `S`
  * If you would like to continuing using the `String.localeCompare` method, then set the `sortLocaleCompare` option to `false` and use the new `textSorter` option as follows:

     ```javascript
     $('table').tablesorter({
       textSorter: function(a,b) {
        return a.localeCompare(b);
       }
     });
     ```

#### Version 2.1.20 (4/28/2012)

* Optimized table rebuilding after sort by using a document fragment instead of appending cells directly to the table. This results in about a 20% increase in sort speed (very roughly determined).
* Optimized pager table rebuilding to also use document fragments, and by removing two extra calls that reapplied the current widgets.

#### Version 2.1.19 (4/23/2012)

* The filter widget will now ignore leading spaces so when the `filter_startsWith` is `true` it will match the text. Fix from [issue #55](https://github.com/Mottie/tablesorter/issues/55). Thanks to [aarkay18](https://github.com/aarkay18) for the code!
* Fixed a problem with empty table cells returning an empty string instead of parsing the cell - needed when there is HTML like an input tag to process. Reverted the change accidently added back in version 2.1.15.
* Added a resort flag that when set to false, it will prevent the resorting of the table when "update", "updateCell" or "addRows" is called. Use the appropriate format below:
  * *update*: `$('table').trigger('update', [false]);
  * *updateCell*: `$('table').trigger('updateCell', [ this, false ]);` - see the [updating a table cell](http://mottie.github.com/tablesorter/docs/example-update-cell.html) demo.
  * *addRows*: `$('table').trigger('addRows', [$row, false]);` - see the [adding table rows](http://mottie.github.com/tablesorter/docs/example-add-rows.html) demo.

#### Version 2.1.18 (4/23/2012)

* When the sticky headers widget is applied to a table with multiple header rows, adding the class name `sticky-false` to any header row will prevent it from becoming sticky. Thanks to [megatom](https://github.com/megatom) for the suggestion in [issue #52](https://github.com/Mottie/tablesorter/issues/52#issuecomment-5261303)!
* Updated filter widget css to better work with twitter's bootstrap. Fix per [issue #54](https://github.com/Mottie/tablesorter/issues/54). Thanks [thezoggy](https://github.com/thezoggy)!
* Modified the green theme arrows; see the [columns style widget](http://mottie.github.com/tablesorter/docs/example-widget-columns.html) demo and choose the green theme to see the change. I've included the PSD files as well.

#### Version 2.1.17 (4/21/2012)

* Fixed an error reported in [issue #52](https://github.com/Mottie/tablesorter/issues/52) which occurrs when using the metadata plugin after the last update.
* The sticky headers widget will now work properly if TD's are included in the header, but the following should be noted:
  * The `selectorHeaders` option needs to be changed to `thead th, thead td` to properly include the TD's.
  * CSS changes to the blue theme were needed and most likely any custom themes to add a background color to these cells.
  * To prevent the TD's from being sortable, add a `sorter-false` class name to it.
* Updated the blue theme:
  * TD's in the sticky header should now have a background color applied.
  * Replaced the black arrow background image gifs with data uri. Included comments with white arrow data uri.
* Updated filter widget to more accurately count the number of columns. There was an issue with multiple header rows.

#### Version 2.1.16 (4/20/2012)

* Removed `emptyToBottom` option. It has been replaced with the `emptyTo` option.
* Added `emptyTo` option:
  * Setting it to `top` will always sort all empty table cells to the top of the table.
  * `bottom` will always sort all empty cells to the bottom of the table.
  * `none` or `zero` will treat empty cells as if their value was zero.
  * Individual columns can be modified by adding the following, set in order of priority:
      * metadata `class="{ empty: 'top' }"`. This requires the metadata plugin.
      * headers option `headers : { 0 : { empty : 'top' } }`.
      * header class name `class="empty-top"`.
      * Overall `emptyTo` option.
  * Updated the [sorting empty cells](http://mottie.github.com/tablesorter/docs/example-option-sort-empty.html) demo.
  * Fix for [issue #48](https://github.com/Mottie/tablesorter/issues/48).

* Add `stringTo` option in version 2.1.16. This options sets the string value for all of the numerical columns.
* Modified the `string` option which is only applied to text within a numerical column; setting the value to:
  * `max` will treat any text in that column as a value greater than the max (more positive) value. Same as the `max+` value, which was retained for backwards compatibility.
  * `min` will treat any text in that column as a value greater than the min (more negative) value. Same as the `max-` value.
  * `top` will always sort the text to the top of the column.
  * `bottom` will always sort the text to the bottom of the column.
  * `none` or `zero` will treat the text as if it has a value of zero.
  * Individual columns can be modified by adding the following, set in order of priority:
      * metadata `class="{ string: 'top' }"`. This requires the metadata plugin.
      * headers option `headers : { 0 : { string : 'top' } }`.
      * header class name `class="string-top"`.
      * Overall `stringTo` option.
  * Updated the [text strings in numerical sort](http://mottie.github.com/tablesorter/docs/example-options-headers-digits-strings.html).
  * Fix for [issue #50](https://github.com/Mottie/tablesorter/issues/50).

* Fixed sticky header widget to now include multiple rows. Fix for [issue #52](https://github.com/Mottie/tablesorter/issues/52).

#### Version 2.1.15 (4/18/2012)

* Modified the `emptyToBottom` option:
  * Clarified that setting this option to `null` will treat empty cells as if they had a value of zero. Fix for [issue #48](https://github.com/Mottie/tablesorter/issues/48).
  * Modified the script so that empty cells do not call their respective parser to keep the `emptyAtBottom` functionality working properly. Fix for [issue #49](https://github.com/Mottie/tablesorter/issues/49).

#### Version 2.1.14 (4/17/2012)

* Updated "shortDate" parser to include the time, if provided. I've also updated the [Changing the date format](http://mottie.github.com/tablesorter/docs/example-option-date-format.html) demo with a few times.

#### Version 2.1.13 (4/17/2012)

* Modified "digit" parser to not remove alphabetical characters as it was breaking the [text strings in numerical sort](http://mottie.github.com/tablesorter/docs/example-options-headers-digits-strings.html) functionality.
