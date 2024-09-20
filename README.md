# build-and-push-with-kaniko

This is a simple example of building and pushing a container with Kaniko.

Pushing to DockerHub requires a credential. I created a PAT in my Docker account and stored it in a kubernetes secret. The `kubectl` command had this form:

```
$ kubectl create secret docker-registry docker-credentials -n cloudbees-ci \
	--docker-username=DOCKER_ACCT \
	--docker-password=DOCKER_PAT \
	--docker-email=DOCKER_EMAIL
```

Note, the secret is of type `docker-registry` and is named `docker-credentials`. In the pod spec in `Jenkinsfile` I reference the secret by that name to get the credential.
