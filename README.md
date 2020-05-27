# Tekton with KIND Example

This repository contains a work in progress project for using [KIND](https://kind.sigs.k8s.io/) as part of a Tekton continuous 
integration process. This was inspired by the article [`Running KIND inside A Kubernetes Cluster for Continuous Integration`](https://d2iq.com/blog/running-kind-inside-a-kubernetes-cluster-for-continuous-integration). The end goal of this is to have a more concrete example 
of using KIND with Tekton for integration testing.

# Prerequesites 

* A Kubernetes cluster - As of now, this has only been tested on Minikube
* Tekton Pipelines [installed on your cluster](https://github.com/tektoncd/pipeline/blob/master/docs/install.md#installing-tekton-pipelines-on-kubernetes)
* kubectl CLI
* [tkn CLI](https://github.com/tektoncd/cli#installing-tkn)

# Running

Create the Task to create a KIND cluster:

```
kubectl apply -f https://raw.githubusercontent.com/danielhelfand/tekton-kind-example/master/tekton/kind.yaml
```

Create the TaskRun to execute the Task:

```
kubectl create -f https://raw.githubusercontent.com/danielhelfand/tekton-kind-example/master/tekton/kind-taskrun.yaml
```

View TaskRun logs:

```
tkn tr logs --last -f
```

The cluster has been successfully created when using the following output is shown:

```
[create-cluster] Set kubectl context to "kind-kind"
[create-cluster] You can now use your cluster with:
[create-cluster] 
[create-cluster] kubectl cluster-info --context kind-kind
[create-cluster] 
[create-cluster] Not sure what to do next? 😅 Check out https://kind.sigs.k8s.io/docs/user/quick-start/
```
