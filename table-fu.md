1. Copy HTML table into .md file.
1. Figure out how many talbe lines you're dealing with and remember that.
1. Combine all of the table lines into one line.
1. Put all tags on their own line. (Sub '<' char with '<[return]' - `:%s/</<ctrl-v[return]/g`
1. Shove everything in the table to the left. (No beginning blanks) - `:%<<<<<`
1. Delete all table tags, thead tags, tbody tags. (You now have only rows, cells, formatting tags and cell data.) - e.g., `:%s/<thead.*>//`
1. Substitute all <th> and <td> tags with '|' char. - `:%s/<t[dh].*>/|`
1. Substitute all </tr> tags with the '|' char. (You now have your MD cell separators in place.)
    Note: If your table uses row spans and column spans, you'll have to improvise.
1. Delete all <tr> tags. - :%s/<tr.*>//
1. Delete all </th> and </td> tags - `:%s/<\/t[dh]>//`
1. Delete all spanny kinds of tags that you can't or don't want to turn into MD formatting, e.g. <div> tags, <p> tags, ...
    At this point, you're left with font formatting and lists.
1. If you're using single asterisks for anything, say, footnotes, escape them. - `:%s/\*/\\\*/`
1. Turn your "simple" font formatting tags into their MD counterparts.
    a. First, get rid of any empty code font or bold font tag pairs, e.g. <strong class="bleh"/>. - `:%s/<strong.*\/>//`
    a. Clean out parameters from tags you are keeping. - `:%s/<ul.*>/<ul>/g`
    a. Clean up spacing around formatting tags and their enclosed content. (Good: <code>code text</code>; Bad:<code> code text</code>;)
    b. Turn <samp> or <code> tags into '`' chars.
    b. Turn </samp> or </code> tags into '`' chars.
    c. Do the same with <strong>/<bold>, <em>/<i>, using their respective MD chars.

Lists: Use HTML tags within tables.
