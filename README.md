# DEPLOYMENT 3.1 – 9.20.23
# POST INCIDENT REPORT


## What was the reason for the incident?

The version of code that the URL was connected to was not ready for deployment. This is why it failed in Jenkins the first time. The incorrect version (V2) was used for the url shortener. 

## How long was the site down or malfunctioning?

The site was down for more than an hour which was way over the time limit that was set in the SLA. 

## What steps were taken to resolve the incident?

Rolled the application back  to the previous version until the new version was fixed.

My first issue was with my AWS EB. I was unable to create a url shortner. I reran and installed a few commands from the AWS EB CLI instructions and was able to obtain my url shortener from there. The url shortener did not work though because it was on the wrong version (I forgot to take a screenshot of this).

![image](https://github.com/DomIvey/Dep3_9.20/assets/140740841/f57fa1cf-9f28-4d0c-a1ba-0f9db23b132c)

Next, I went to Jenkins to deploy the application and it did not work. After reading the logs I found that it was the code in the test_app.py file. The line should have read “hi Jeff” (no space after “Jeff), but instead it read “hi Jeff “ (with a space after “Jeff”). Once I took out the space, Jenkins was able to successfully build, test, and deploy the application. 

![image](https://github.com/DomIvey/Dep3_9.20/assets/140740841/a9e930af-d2a8-4b96-ad50-28a015398f3d)

![image](https://github.com/DomIvey/Dep3_9.20/assets/140740841/c75a38a6-2e2e-43db-b9cb-af9212e5e2e1)

![image](https://github.com/DomIvey/Dep3_9.20/assets/140740841/b262ce82-c4a4-4f82-8cbb-da1754663676)

When it came to the successful url shortener I had to do this in Git Hub. To do this, I used the git checkout command, along with the hash from V1. Once this was committed, I then pushed the changes from my local terminal in VS Code to my GitHub repository. Once the changes were rolled back to the previous version, the url shortener worked: http://dep-3-91923-main-dev.us-east-1.elasticbeanstalk.com/  

![image](https://github.com/DomIvey/Dep3_9.20/assets/140740841/b3fabad0-e81c-48d1-aa09-2889cccced15)

## Was the incident fully resolved?

Yes, although it was well beyond 20 minutes, once the app was rolled back and redeployed in Jenkins it was resolved. 

## What steps would you take to prevent this from happening again?

Going forward I would make sure that someone with more experience reviews the application before it was deployed. Also, for any issues that arise in the future I would notify Nike to let them know what is going on and reassure them that we are working on fixing the issue as soon as possible to stay within the time limit set in our contract. 
