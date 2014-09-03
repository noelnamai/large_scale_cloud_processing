## Large-scale processing in the cloud Help

### Terminating an AWS cluster

When you are done running Pig scripts, make sure to ALSO terminate your job flow. This is a step that you need to do in addition to stopping pig and Hadoop (if necessary).

1. Go to the [Management Console](https://console.aws.amazon.com/elasticmapreduce/home).
2. Select the job in the list.
3. Click the Terminate button (you may also need to turn off Termination protection).
4. Wait for a while (may take minutes) and recheck until the job state becomes TERMINATED.

If you fail to terminate your job and only close the browser, or log off AWS, your AWS will continue to run, and AWS will continue to charge your credit card: for hours, days, and weeks. Make sure you don't leave the console until you have confirmation that the job is terminated.

### Notes

This will be very difficult from Windows and the instructions assume you have access to a Linux command line.

This should cost no more than 5-10 dollars if you only use small aws instances
