# Coder/vscode OpenShift Template
An OpenShift Template to run a distribution of Coder's [Visual Studio Code in browser](https://github.com/codercom/code-server) on your OpenShift Cluster

Based on [https://github.com/sr229/code-server-openshift](https://github.com/sr229/code-server-openshift) and [https://github.com/codercom/code-server/releases](https://github.com/codercom/code-server/releases)

## Running
```bash
oc new-app -f https://raw.githubusercontent.com/jefferyb/code-server-openshift/master/code-server-openshift-template.yaml -p URL=vscode.example.com -p CODER_PASSWORD=welcome2vscode

# OR

oc process -f https://raw.githubusercontent.com/jefferyb/code-server-openshift/master/code-server-openshift-template.yaml -p URL=vscode.example.com -p CODER_PASSWORD=welcome2vscode | oc create -f -
```

If we find `/home/coder/projects/.setup/setup-vscode` file in the container, we'll run/execute it to setup VS Code on startup. Useful when a container restarts and want to run a script to it setup automatically

## Default Parameters

   * NAME=code-server
   * URL=
   * CONTAINER_HOSTNAME=coder
   * CODER_PASSWORD=coder
   * CODER_ENABLE_AUTH=true
   * PVC_STORAGE=10Gi
   * DOCKER_IMAGE=jefferyb/code-server:latest

## Added Packages

Added a few packages that can be used in vs code terminal

   * git
   * java
   * httpie
   * nodejs
   * python
   * ansible
   * openssh-client
   * oc (OpenShift client)
   * kubectl (Kubernetes client)
