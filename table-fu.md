1. Copy HTML table into .md file.
1. Figure out how many lines in the table.
1. Combine all of the table lines into one line.
1. Put all tags on their own line. (Sub '>' char with '>[return]' - `:%s/>/>ctrl-v[return]/g`
1. Shove everything in the table to the left. (No beginning blanks) - `:%<<<<<`
1. Get rid of table tags, thead tags, tbody tags. (You now have only rows, cells, formatting tags and cell data.) - e.g., `:%s/<thead.*>//`
1. Substitute all <th> and <td> tags with '|' char. - `:%s/<t[hd].*>/|`
1. Substitute all </tr> tags with '|' char. (You now have your MD cell separators in place.)
1. Get rid of <tr> tags. - :%s/<tr.*>//
1. Get rid of </th> and </td> tags - `:%s/<\/t[dh]>//`
1. Get rid of any spanny kind of tags that you can't or don't want to turn into MD formatting, e.g. <div> tags, <p> tags, ...
    At this point, you're left with font formatting, and lists, and ?
1. If you're using asterisks for anything, say, footnotes, escape them. - `:%s/\*/\\\*/`
1. Turn your "simple" font formatting tags into their MD counterparts.
    a. First, get rid of any empty code font or bold font tag pairs, e.g. <strong class="bleh"/>. - `:%s/<strong.*\/>//`
    a. Clean out class and id parameters, etc., from tags. - `:%s/<ul.*>/<ul>/g`
    b. <samp> or <code> into '`' chars (don't forget closing chars for <\/samp>, etc.))
    c. <bold> or <strong> into '**' chars, and their </bold> or </strong> closers.
    d. Do line joins to pull the text being bolded or "coded" onto the same line as the formatting. You can do the first line join automagically, but for multi-lines, you have to do it manually (at this point anyway, I haven't figured out a trickier way). - I'm going to figure out how many there are by doing `grep "\*\*" [filename] | wc -l`, and then record `/ ^\*\*;J` and run it as many times as there are instances. `44@q` if there are 44 and I recorded the operation in buffer 'q'.
    e. Get rid of spaces before and after your formatting characters. - `:%s/\*\* /\*\*/` with some recording as well to do repeat line-join space-removal as necessary.
    f. Manual formatting cleanup if necessary.
1. That should be it for formatting. On to lists...
