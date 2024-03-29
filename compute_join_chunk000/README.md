## Problem 3: Compute a Join on chunk-000

In this problem we will consider the subgraph consisting of triples whose subject matches rdfabout.com: for that, filter on ```subject matches '.*rdfabout\\.com.*'```. Find all chains of lengths 2 in this subgraph. More precisely, return all sextuples (subject, predicate, object, subject2, predicate2, object2) where object=subject2.

Note: Newer versions of Pig will automatically drop the duplicate column in the join output.In that case, you do NOT need to return the sixth column.

Suggestions on how to proceed:

* First filter the data so you only have tuples whose subject matches 'rdfabout.com'.
* Make another copy of the filtered collection (it's best to re-label the subject, predicate, and objects, for example to subject2, predicate2, object2).
* Now join the two copies:
  * the first copy of the 'rdfabout.com' collection should match on object.
  * the second copy of the 'rdfabout.com' collection should match on subject2.
* Remove duplicate tuples from the result of the join
As above, first debug your script for this problem using the test file. Once your script is debugged, then run it on the bigger file 'btc-2010-chunk-000'. While debugging on the test file, make the following two changes:

1) Use the following filter
```
subject matches '.*business.*'
```
2) Change the join predicate to be ```subject=subject2```

Otherwise, you will not get any results.

Note: this script took about 18 minutes with 10 small nodes.

What you need to turn in:
How many records are generated by the join for the cse-344-test-file dataset? For the btc-2010-chunk-000 dataset? DON'T FORGET TO SHUTDOWN YOUR INSTANCES!
