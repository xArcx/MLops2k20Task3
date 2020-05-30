# MLops2k20Task3

## Problem Overview :
 - Create docker container image that has python installed in it along with all the essential libraries required for training Machine   learning model.
 - Create number of jobs in jenkins to test , notify , rebuild , tweak the machine learning model in order to get desired accuracy.
 
 We are going to build chain of jobs here in order to get desired accuracy for given dataset but before going ahead we have to create a Dockerfile which will create image with required configurations.

 - Job 1 : Job 1 will keep an eye on github repository for changes. This job will automatically copy everything in           the folder of my base os as soon as new commits are done..( RHEL8 as my base os ). 
 
   [![Screenshot-25.png](https://i.postimg.cc/J49g1zBB/Screenshot-25.png)](https://postimg.cc/ykynjBjV)
   
   [![Screenshot-26.png](https://i.postimg.cc/T1BkYthX/Screenshot-26.png)](https://postimg.cc/1Vc0vcpW)
   
   [![Screenshot-27.png](https://i.postimg.cc/Hs7ZP1PW/Screenshot-27.png)](https://postimg.cc/7fwnfdkj)
   
 - Job 2 : Success of Job 1 will trigger job 2. This job will launch docker container which is workspace for Jenkins.
 - Job 3 : After successfully launching the OS Jenkins will trigger this job. This job will search for file which is pushed by developer and has a main code to train model. (in my case)
 - Job 4 : If main code runs successfully but give less accuracy than what developer desire then jenkins should automatically tweak   something and by various hit and trials will try to increase the accuracy. In order to achive this thing developer will push one more file along with main.py that is rebuild.py. This will help jenkins to take tests and build model again and again till      desired accuracy is achived.
 - Job 5 : This job is success notifier as soon as jenkins succeed in achieving desired accuracy it will notify developer about success of the model and accuracy achieved.
 - Job 6 : This job is again failure notifier but now it will notify on failure of rebuild.py file.
 - there was supposed to be a job 7, that would monitor the containers.Instead as i am using kubernetes deployment,they take care of it automatically.

## solution
 - First create docker image using docker file. One of my dockerfile looks like this.Its for the DL files.
   [![Screenshot-24.png](https://i.postimg.cc/VN1gdQNg/Screenshot-24.png)](https://postimg.cc/PC3YR7Yv)
  - After successful build, it will show like this.
   [![Screenshot-21.png](https://i.postimg.cc/25wYgDJB/Screenshot-21.png)](https://postimg.cc/jWLBJGRs)
   

   
