# Leak report

_Use this document to describe whatever memory leaks you find in `clean_whitespace.c` and how you might fix them. You should also probably remove this explanatory text._
46 bytes of unfreed memory, which is traced through different function calls.
We can follow the leak step-by-step in the extended report.
It looks like it will be fixed by freeing memory in main, so I'll try there first.

So, I wrote the above without looking through the program at all.
After viewing the program, I can say that the memory leak happens because of the strip function.
The strip function allocates memory for the string without freeing it, then passes the result on.
That result is used in is_clean, and then not again. The memory leak would be fixed by:
Freeing the result of strip after the comparison in is_clean should fix the problem.
