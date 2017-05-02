# Render your job

```
export PROJECT_NAME="ubuntu-16.04-drupal"
export JENKINS_JOBNAME="emergya_$PROJECT_NAME"

cp -a emergya-floss-docker-image-example.xml ${JENKINS_JOBNAME}.xml

export GIT_HTTP_REPOSITORY_URI="https://github.com/Emergya/${PROJECT_NAME}.git"

export DOCKER_PRIVATE_REGISTRY_HOST="CHANGEME:443"
export DOCKER_PRIVATE_REGISTRY_REPO="emergya"

export DOCKER_IMAGE="$DOCKER_PRIVATE_REGISTRY_REPO/$PROJECT_NAME"
# hashes as generated via UI by https://wiki.jenkins-ci.org/display/JENKINS/Mask+Passwords+Plugin
export DOCKER_USERNAME_HASH='CHANGEME'
export DOCKER_PASSWORD_HASH='CHANGEME'

sed -i "s|_GIT_HTTP_REPOSITORY_URI_|$GIT_HTTP_REPOSITORY_URI|g" ${JENKINS_JOBNAME}.xml
sed -i "s|_DOCKER_PRIVATE_REGISTRY_HOST_|$DOCKER_PRIVATE_REGISTRY_HOST|g" $JENKINS_JOBNAME_FILENAME
sed -i "s|_DOCKER_PRIVATE_REGISTRY_REPO_|$DOCKER_PRIVATE_REGISTRY_REPO|g" $JENKINS_JOBNAME_FILENAME
sed -i "s|_DOCKER_IMAGE_|$DOCKER_IMAGE|g" ${JENKINS_JOBNAME}.xml
sed -i "s|_DOCKER_USERNAME_HASH_|$DOCKER_USERNAME_HASH|g" ${JENKINS_JOBNAME}.xml
sed -i "s|_DOCKER_PASSWORD_HASH_|$DOCKER_PASSWORD_HASH|g" ${JENKINS_JOBNAME}.xml

```