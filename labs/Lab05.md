## Lab 5: Hadoop Integration

In this lesson we’ll see two mechanisms for integrating with Hadoop:

- Filesystem - storing data in Hadoop itself using HDFS
- Computation - executing code on the Hadoop cluster via Spark

Stop all sessions you have currently running. Start a new **Python3 session.**

Select the **2_pyspark.py** file.

Look at line 34:

`!hdfs dfs -put -f $HOME/data/kmeans_data.txt /user/$HADOOP_USER_NAME`

**Question**: What is this line doing? Where is the data coming from? Where is it going to?

You can see that the original data (stored under the data directory of our project) is copied into HDFS. The data is tiny (go look at it with the file browser!), but the principle is what applies - simple integration with HDFS.

Execute the 2_pyspark.py file in your already running Python session

**Question**: What did it do?

**Question**: What kind of thing is the variable ‘data’? (try typing ‘data’ into the console and seeing what gets printed out.Open a terminal using the ‘terminal’ icon in the top right: 

Execute `hdfs dfs -ls` to see the data file in the hadoop file system (or, to show off, execute `! hdfs dfs -ls`in the python console to do the same thing!)

If everything went correctly you’ll see that we demonstrate:

- Natural integration with HDFS - it’s just a path to a file!
- Natural parallel computation across the cluster using Spark

**Question**: If you had 20TB and 50 nodes with 32 processors per node how much faster do you think a KMeans algorithm would take compared to running it on your laptop? 10X? 100X?

**Question:** What shell is running in that terminal? What else can you do in the terminal? Does it remind you of a terminal access to your Linux laptop?

### End of Lab 5

----

[Back to Main](https://github.com/rajatrakesh/cdswlabs)







In this lesson we’ll see two mechanisms for integrating with Hadoop:

1. Filesystem - storing data in Hadoop itself using HDFS
2. Computation - executing code on the Hadoop cluster via Spark

Execute the following instructions.
1. Clean up your Python session by hitting the ‘clear’ button and the ‘expand’ link (if available)

2. Select the 2_pyspark.py file
3. If you don’t have a Python 3 workbench session open yet, Launch a Python 3 session 1 vCPU / 4 GB
RAM
4. Run line 32:
5. !hdfs dfs -put -f $HOME/data/kmeans_data.txt /user/cdsw
6. Execute the 2_pyspark.py file in your already running Python session
7. Question: What did it do?
8. Question: What kind of thing is the variable ‘data’? (try typing ‘data’ into the console and seeing
what gets printed out.
9. Open a terminal using the ‘terminal’ icon in the top right:

10. Execute ‘hdfs dfs -ls’ to see the data file in the hadoop file system (or, to show off, execute ‘! hdfs dfs -ls’ in the python console to do the same thing!)

If everything went correctly you’ll see that we demonstrate:
● Natural integration with HDFS - it’s just a path to a file!
● Natural parallel computation across the cluster using Spark