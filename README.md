# gitlab-pipeline
Hi

CI (Continuous Integration):- 
In this repository I have provided the Complete CI Pipeline for Java based application Build.

Gitlab Runner:-
In this Pipeline we have used Docker Executor Gitlab Runner with base Image as Ubuntu:latest.
Gitlab Runner is running on Ubuntu 22.04 with Docker Installed on it and it is a Group Runner.

Docker Executor:-
As we are using Docker Executor with Docker in Docker (DIND)
As per the Documentation of Gitlab we have to use few variable to work the CI Pipeline.
DOCKER_HOST: tcp://docker:2375
DOCKER_TLS_CERTDIR: ""
So need to add This two Variables So the Docker Daemon Starts properly without any Error.

Also Note Change the Priviledge in Config.toml file from false to true.
    privileged = true
If the Priviledge is false it wil throw Error.

Executor Tags:-
As we have Multiple Runners So we defined Tag for Each Runner and Used it in our Pipeline.
So it helps to Execute the Stages in Required Runner.

Group & Project Variables:-
The Pipeline is Configured to use some Group Variables and Project variables.
In the Group Variable We have defined the Container Registry URL and on Project Variable we have defined the Image Name.

Image Tag:-
We are Using Constant tag or Our Image with an Env Name.
We have collected the in Built Variables to collect the Branch Name. 
$CI_COMMIT_BRANCH with this Command it will provide the Branch Name.
So will the help of Ubuntu Commands we will filter it out the Required Name from it and will store it in $ENV and will use $ENV as Image tag.

Nexus Repository:-
We are also Copying the Settings.xml file from the code base to the stage for build process to get all its dependency from the Nexus Repository.

Workflow Rules:-
This CI Pipeline is Triggered manually using Gitlab UI. So we have defined workflow rules.
Where is defines that the pipeline should be triggered from Web UI with the branch.

Sonarqube:-
We also have tried Implementing Sonarqube on this project. We have Installed Sonarqube on Gitlab Runner Server. Sonarqube version is 9.9 LTS.

Sonarqube is installed using Docker and soanrqube Image with 9.9 version.

So the sonarqube URL is used in Gitlab Pipeline and it is used as a Group variable in Gitlab SonarToken is generated for Authentication Purpose and its also used in Group variable in gitlab.

Sonarqube analysis command is Implemented on the Build Stage only.
Once the Build is completed it will run the sonar Gaols and it will generate the Report which will be available to analyse in Sonarqube.


Thanks.