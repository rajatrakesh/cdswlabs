

## Lab 10 : Scheduling Jobs

It’s often the case that you need to execute tasks on a periodic basis, and to execute one or more tasks once some other task has succeeded. Obviously there are sophisticated workflow engines many customers are already using. For simple workflows CDSW has a handy jobs system built in.  Jobs can also be exposed for for use from other scheduling systems.

 

This lab goes through the mechanics of creating a simple multi-step job process. 

1. Open up your      ‘**cdsw demo**’ project to get to      this screen:
2. Select the      ‘new job’ link in the middle of the page, and you’ll get to the following      screen (there are other ways of getting to this next screen - its an      exercise for the student to figure out what they might be):
3. Create  a job that will be triggered manually      and will execute the 1_python.py. Here are the parameters to do that:
4.  

| Name            | My New Job  |
| --------------- | ----------- |
| Script          | 1_python.py |
| Engine   Kernel | Python 3    |

1.  
2. Leave      everything else as default. Scroll down and hit ‘Create Job’. You should      get to this screen:
3. Here you can      see that you have a job (‘My New Job’). It’s never been run, and it has no      dependencies.
4. Let’s make      other jobs depend on this one: Click the ‘+ Add Job Dependency’ grayed out      button and add a new job that has a dependency on ‘My New Job’. The      parameters are:
5.  

| Name          | Job 2        |
| ------------- | ------------ |
| Script        | 2_pyspark.py |
| Engine Kernel | Python 2     |

1. Scroll down and ‘Create Job’.      You’ll now see a page like this:
2. So here we      can see that ‘Job 2’ depends upon ‘My New Job’ (although you can run each      manually, if you so choose). 
3. Lets add      another job that will run in parallel with Job2:
4. Click ‘New      Job’ in the top right corner and create another job that depends upon ‘My      New Job’. The parameters you’ll need are:
5.  

| Name          | R Job                    |
| ------------- | ------------------------ |
| Script        | 4_sparklyr.R             |
| Engine Kernel | R                        |
| Schedule      | Dependent / My   New Job |

1. Create the job and you’ll see      this:

2. Lets run it      all - hit the ‘Run’ button next to ‘My New Job’ (bottom of the list of      jobs). You should see the job get scheduled, run, complete, and then the      next two jobs should likewise get scheduled, run and complete:

3. **Question**: How will a job scheduler reduce the effort required for you to build simple pipelines?

    

   **Question**: What other facilities surrounding a job did we not explain? What do you think those other parameters might do?  

### End of Lab 10

------

[Back to Main](https://github.com/rajatrakesh/cdswlabs)