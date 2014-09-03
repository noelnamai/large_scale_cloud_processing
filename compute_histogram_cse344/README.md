## Problem 2A: Compute a Histogram on cse344-test-file

Using the 'cse344-test-file' file, write a Pig script that groups tuples by the subject column, and creates/stores histogram data showing the distribution of counts per subject, then generate a scatter-plot of this histogram. The histogram consists of:

* The x-axis is the counts associated with the subjects, and
* The y-axis is the total number of subjects associated with each particular count.

So, for each point (x,y) that we generate, we mean to say that y subjects each had x tuples associated with them after we group by subject.

A few comments to help you get started:

* We expect that your script will (1) group the input data by subject and count the tuples associated with each subject then (2) group the results by these intermediate counts (x-axis values) and compute the final counts (y-axis values).
* To get more familiar with the Pig Latin commands, we suggest that you also take a look at the [Pig Latin Reference](http://pig.apache.org/docs/r0.7.0/piglatin_ref2.html).

DEBUGGING:

* Since you are using the small test file in this question, you can run a small, 1-node cluster.
* In this question, we are debugging the script. The output of this question is thus not going to be terribly interesting. In fact, your scatterplot should only have two points: (1,1) and (3,333).
* To debug a Pig Latin script, try to run Pig as follows:
```
 pig -x local  
 ```
Run all commands as you normally would, except for store. You need to store your results locally:
```
store my_final_output into '/tmp/finaloutput' using PigStorag()
```
Once you are done debugging in local mode, try to run your script by issuing real MapReduce jobs. That is run with "pig" instead of "pig -x local" (remember to change the store command).

#### What you need to turn in: 

How many (x, y) points are generated in the histogram? DON'T FORGET TO SHUTDOWN YOUR INSTANCES!

## Problem 2B: Compute a Histogram on chunk-000

Now run your script from Problem 2A on 'btc-2010-chunk-000' file. Please use a 5-node cluster of small instances.

Note: this script took about 21 minutes with 5 nodes.

What you need to turn in:
How many (x, y) points are generated in the histogram? DON'T FORGET TO SHUTDOWN YOUR INSTANCES!
