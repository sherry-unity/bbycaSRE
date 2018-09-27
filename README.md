A pipeline design for a simple Nodejs app using Heroku.

Workflow description:

1.	Install and update GIT, Heruko and required dependencies for app deployment (node, npm)
2.	Fork the bbycaSRE github repository to my own github account (sparkshfx)
3.	Create 4 branches for the sake of simplicity and possible assumption of different changes aimed to different environment 
(DEV, TEST, DR, master)
4.	Create/design a new pipeline and app in Heroku (Using terminal or UI) and connect github account to it.
5.	Configure and set the ENV and PORT variables for each environment.
6.	Final check to see the apps run locally and on the web.

How the process works:
The pipeline is triggered with the committed changes to github, which could be considered development stage, then in review apps it can be reviewed/code reviewed or also automatically triggered for build using Jenkins or similar build specific technology. On heroku on development environment the app can be developed/modified, and then pushed to staging environment where it can also be sent back to development or promoted to production upon satisfying the requirements. I did not work on Tests/CI section.

•	Pipeline name : bbcasreppln
https://dashboard.heroku.com/pipelines/802c4aeb-d8cd-49dd-8989-e9f719160995 

•	Environment specifics:
  Apps and config variables
  bbcasre-dev                  ENV DEV, PORT 8000   
  https://bbcasre-dev.herokuapp.com/ 
  bbcasre-staging            ENV DR, PORT 8001
  https://bbcasre-staging.herokuapp.com/ 
  bbcasre-prod                 ENV PROD, PORT 8002
  https://bbcasre-prod.herokuapp.com/ 

•	Challenges and problems

o	Build failure of Nodejs app due to the missing a dependency. Investigating in the Heruko log I found out package.json file is missing and need to create a default one. Using “npm init” I was able to create the package.json but I had to manually edit it to cover for missing dependencies: express and ejs.

o	The problem definition looked so broad, I could design a pipeline to Develop at the first stage, Build in the second, Test in the third and stage, then push to the production. I took the best guess in design choice as I assumed the build stage is not automated and triggered manually.





