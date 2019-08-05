## Lab 7 : Scala

In this lab we show how you can use the ‘Template’ mechanism to get started with a simple Scala example:

1. Navigate to the project space by selecting “project”:
2. Create a new project by hitting the ‘+’ button on the top right and selecting ‘create project’:
3. In the Create new Project window that comes up provide a name for your new project (‘Scala’, for
   example), and then choose the Scala template:
4. Create the project. You’ll see the File Browser view onto the project.
5. Hit ‘**Open Workbench**’ in the top right and let’s go run some Scala code:
6. Start a **Scala** session
7. The Scala example project includes its own data set that needs to be moved into HDFS, since that is where the scala code expects to find it. Open a Terminal by clicking on the **>_Terminal access** button and execute the following shell commands to do this. Note how you have ready access to your own project’s data (purely local to you) and the secure (and massive) HDFS cluster:
8. `$ hdfs dfs -put data      /tmp/datauserXX`   (replace XX with      your user number)
9. Execute one or more of the various scala files in the Workbench

​                        

**Question:** How will you use templates when demonstrating CDSW to your friends and colleagues?

 

STOP your Scala session now

### End of Lab 7

------

[Back to Main](https://github.com/rajatrakesh/cdswlabs)