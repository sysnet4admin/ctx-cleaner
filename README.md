# `ctx-cleaner`: Easy to clean up garbage on contexts

[![version](https://img.shields.io/badge/version-0.9-yellow.svg)](https://semver.org)
![Proudly written in Bash](https://img.shields.io/badge/written%20in-bash-ff69b4.svg)
[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)

## **`ctx-cleaner`** DEMO 
![ctx-cleaner-demo GIF](img/ctx-cleaner-demo.gif)

-----

## Environment

kubectl >= 1.20.x
```bash
kubectl version --client
Client Version: version.Info{Major:"1", Minor:"23", GitVersion:"v1.23.1", GitCommit:"86ec240af8cbd1b60bcc4c03c20da9b98005b92e", GitTreeState:"clean", BuildDate:"2021-12-16T11:33:37Z", GoVersion:"go1.17.5", Compiler:"gc", Platform:"darwin/amd64"}
```

In versions of kubectl less than 1.20, an error occurs because the `kubectl config get-users` command cannot be found among the execution contents.


## Purpose 
When k8s Contexts are not matched to Clusters or Users like below: <br/>
(i.e. if you remove contexts, clusters & users cannot remove automatically)

#### k8s Contexts
```bash 
$ kubectl config get-contexts
CURRENT   NAME   CLUSTER                                          AUTHINFO                                         NAMESPACE
          aks    aks                                              clusterUser_res_aks                              default
          eks    arn:aws:eks:us-east-2:443308097684:cluster/eks   arn:aws:eks:us-east-2:443308097684:cluster/eks
          gke    gke_hj-int-20200908_us-central1-c_gke            gke_hj-int-20200908_us-central1-c_gke
          nks    kubernetes                                       kubernetes-admin
```

#### k8s Clusters 
```bash 
$ kubectl config get-clusters
NAME
aks
arn:aws:eks:us-east-2:443308097684:cluster/eks
gke_20200512_us-central1-c_beer
gke_20200512_us-central1-c_bread
gke_20200512_us-central1-c_coffee
gke_hj-int-20200908_us-central1-c_gke
kubernetes
```

-----

## Usage

```bash
$ ctx-cleaner 
deleted cluster gke_20200512_us-central1-c_beer from /Users/mz01-hj/.kube/config
deleted cluster gke_20200512_us-central1-c_bread from /Users/mz01-hj/.kube/config
deleted cluster gke_20200512_us-central1-c_coffee from /Users/mz01-hj/.kube/config
deleted user gke_20200512_us-central1-c_beer from /Users/mz01-hj/.kube/config
deleted user gke_20200512_us-central1-c_bread from /Users/mz01-hj/.kube/config
deleted user gke_20200512_us-central1-c_coffee from /Users/mz01-hj/.kube/config
```

-----

## Installation

### Add other method later 

### One time runner 
```bash 
$ curl https://raw.githubusercontent.com/sysnet4admin/ctx-cleaner/main/ctx-cleaner | bash
```

### Manual Installation (macOS and Linux)
Since ctx-cleaner is written in Bash, you should be able to install 
them to any POSIX environment that has Bash installed

- Download the `ctx-cleaner` scripts.
- Either:
  - save them all to somewhere in your `PATH`,
  - or save them to a directory, then create symlinks to `ctx-cleaner` from
    somewhere in your `PATH`, like `/usr/local/bin`
- Make `ctx-cleaner` executable (`chmod +x ...`)

Example installation steps:

```bash
$ sudo git clone https://github.com/sysnet4admin/ctx-cleaner.git /opt/ctx-cleaner
$ sudo ln -s /opt/ctx-cleaner /usr/local/bin/ctx-cleaner
```

**OR**

```bash
$ curl https://raw.githubusercontent.com/sysnet4admin/ctx-cleaner/main/ctx-cleaner -o /usr/local/bin/ctx-cleaner
$ chmod +x /usr/local/bin/ctx-cleaner
```

-----

## Uninstall ctx-cleaner

```bash
$ rm -rf /opt/ctx-cleaner 
$ rm -f /usr/local/bin/ctx-cleaner 
```
