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
If the Priviledge is false it wil through Error.

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



