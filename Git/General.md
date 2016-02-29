# Ignore only from root folder

If the pattern does not contain a slash /, git treats it as a shell glob pattern and checks for a match against the pathname relative to the location of the .gitignore file (relative to the toplevel of the work tree if not from a .gitignore file).

A leading slash matches the beginning of the pathname. For example, "/*.c" matches "cat-file.c" but not "mozilla-sha1/sha1.c".
So you should add the following line to your root .gitignore:

/config.php

(Source)[http://stackoverflow.com/a/3637678]
