# Using `vi` to transform an HTML table to (mostly) Markdown

1. Copy HTML table into .md text file.
1. Combine all of the table lines into one line. - [Number of lines] J (J is for Join)
1. Put all tags on their own line. (Sub '<' char with '<[return]' - `:%s/</<ctrl-v[return]/g`
1. Delete all <table> tags, <thead> tags, <tbody> tags. (You now have only rows, cells, formatting tags and cell data.) - `:%s/<*.table.*>//`
1. Substitute all <th> and <td> tags with the '|' char. - `:%s/<t[dh].*>/|`
1. Substitute all </tr> tags with the '|' char. (You now have your MD cell separators in place.)
    Note: If your table uses row spans and column spans, you'll have to improvise here. How will depend on your implementation. Either add '|' chars to balance, or...
1. Delete all <tr> tags. - :%s/<tr.*>//
1. Delete all </th> and </td> tags - `:%s/<\/t[dh]>//`
1. Delete all "spanny" kinds of tags that you can't or don't want to turn into MD formatting, e.g. <div> tags, <p> tags, ...
    You're now left with (mostly) font formatting tags and list tags.
1. If you're using single asterisks for anything, say, footnotes, escape them. - `:%s/\*/\\\*/`
1. Turn your "simple" font formatting tags into their MD counterparts.
    a. First, get rid of any empty code font or bold font tag pairs, e.g. <strong class="bleh"/>. - `:%s/<strong.*\/>//`
    a. Clean up spacing around formatting tags and their enclosed content. (Good: "Content <code>code text</code>"; Bad: "Content<code> code text</code>")
    b. Turn <samp> or <code> tags into '`' chars.
    b. Turn </samp> or </code> tags into '`' chars.
    c. Do the same with <strong>/<bold>, <em>/<i>, etc., using their respective MD chars.

**Lists:** I think your best bet is to stick with  HTML tags within table cells. 
