# Coder/vscode OpenShift Template
An OpenShift Template to run a distribution of Coder's [Visual Studio Code in browser](https://github.com/codercom/code-server) on your OpenShift Cluster

## Running
```bash
oc new-app -f https://raw.githubusercontent.com/jefferyb/code-server-openshift/master/code-server-openshift-template.yaml -p URL=vscode.example.com -p CODER_PASSWORD=welcome2vscode

# OR

oc process -f https://raw.githubusercontent.com/jefferyb/code-server-openshift/master/code-server-openshift-template.yaml -p URL=vscode.example.com -p CODER_PASSWORD=welcome2vscode | oc create -f -
```

## Default Parameters

   * NAME=code-server
   * URL=
   * CODER_ENABLE_AUTH=true
   * CODER_PASSWORD=coder
   * PVC_STORAGE=10Gi
   * DOCKER_IMAGE=jefferyb/code-server:latest
