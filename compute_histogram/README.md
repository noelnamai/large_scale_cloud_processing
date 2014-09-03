## Problem 4 : Compute a Histogram on the Entire Dataset

Compute the histogram in Problem 2 on the entire 0.5TB dataset. Use as many nodes as you like up to 19 small nodes.

You need to modify the load instruction to:
```
raw = LOAD 's3n://uw-cse-344-oregon.aws.amazon.com/btc-2010-chunk-*' USING TextLoader as (line:chararray);
```
Note: this query will take more than 4 hours to run. Plan accordingly, and monitor carefully: if anything looks wrong, abort, fix, restart.

When you are done, appreciate how relatively quick and easy it was to analyze a 0.5TB graph!

What you need to turn in:
How many (x, y) points are generated in the histogram? DON'T FORGET TO SHUTDOWN YOUR INSTANCES!
