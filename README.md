# Coder/vscode OpenShift Template
An OpenShift Template to run a distribution of Coder's [Visual Studio Code in browser](https://github.com/codercom/code-server) on your OpenShift Cluster

Based on [https://github.com/sr229/code-server-openshift](https://github.com/sr229/code-server-openshift) and [https://github.com/codercom/code-server/releases](https://github.com/codercom/code-server/releases)

## Running
### Using Openshift CLI
```bash
oc new-app -f https://raw.githubusercontent.com/jefferyb/code-server-openshift/master/code-server-openshift-template.yaml -p URL=vscode.example.com -p CODER_PASSWORD=welcome2vscode

# OR

oc process -f https://raw.githubusercontent.com/jefferyb/code-server-openshift/master/code-server-openshift-template.yaml -p URL=vscode.example.com -p CODER_PASSWORD=welcome2vscode | oc create -f -

# OR

oc new-app --name=code-server --image=jefferyb/code-server -e CODER_PASSWORD=welcome2vscode
oc create route edge code-server --insecure-policy=Redirect --service=code-server --hostname=vscode.example.com
```

### Using Kubernetes CLI
```bash
# Deploy
kubectl run code-server --image=jefferyb/code-server -e CODER_PASSWORD=welcome2vscode
```

### Using Docker
```bash
# Deploy
docker run -itd --name code-server -e CODER_PASSWORD=welcome2vscode -p 9000:9000 -v "${PWD}:/home/coder/project" jefferyb/code-server
```

If we find `/home/coder/projects/.setup/setup-vscode` file in the container, we'll run/execute it to setup VS Code on startup. Useful when a container restarts and want to run a script to it setup automatically

## Default Parameters for the OpenShift Template ( code-server-openshift-template.yaml )

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
