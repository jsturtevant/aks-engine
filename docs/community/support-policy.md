# aks-engine Support Policy
This document is to outline our support policy for the aks-engine binaries that are produced in our releases. It also outlines the support for kubernetes versions in relation to the AKS-engine version.  By support we mean we will help with issue on github and produce patch release for critical issues.  Please review our [release process documentation](release-checklist.md) for details on how we produce patches. 

aks-engine is approaching a stable 1.0 release.  We will have a difference between the support policy prior to the release and the stable 1.0 version.

## aks-engine pre 1.0 

### aks-engine binary support policy
As we did not have a clear support policy prior to 1.0, for any issues opened we will do our do diligence, with in reason, to identify the root cause. 

For all minor versions <1.0 we will patch back to `n-4` where `n` is the latest minor version. For example if we find an issue that in `0.54.0`, we patch back to the `0.50.0` release where required. 

We highly recommend upgrading as soon as possible to the latest minor versions as we will only patch critical issues and you will will benefit from many other improvements by adopting the latest minor version.

After 1.0 is released we will support `n-1` patch release for 6 months after the release of the patch release.  After 6 months of 1.0 we will ask teams to adopt the latest 1.0 release. 

### Kubernetes version support

Kubernetes supports `n-3` versions.  In aks-engine prior to 1.0, any version that is is shipped inside a supported an aks-engine version will be considered for support if the changes are directly related to ask-engine.  If the issue is related to changes required in kubenetes binaries/images them selves then we will support them in relation to the kubernetes support policy of `n-3`.  Any changes to the kubernetes support policy will supercede this document in relation to the kubernetes binaries. 

We highly recommend upgrading as soon as possible to the latest minor versions of Kubernetes as patch fixed for kubernetes will not be released for anything prior to `n-3`.

## aks-engine 1.0+
For 1.0, we are evolving our support policy as following.

### aks-engine binary support policy
We will support issues for `n-3` versions where `n` is the latest minor version in the major release.

For all minor versions <1.0 we will patch back to `n - 3` where `n` is the latest minor version in the major release. For example if we find an issue that in `1.3.0`, we patch back to the `1.0.0` release where required. 

### Kubernetes version support

After 1.0, with in the aks-engine binary we will support `n-3` versions of kubernetes.  As we add additional kubernetes versions (non pre-release) we will drop off the prior kubernetes.  

An **example** of our support model after 1.0 (should updated once we move to 1.0 and we have releases)


| aks-engine version  | kubernetes versions | supported |
| ------------------- |:-------------------:|:---------:|
| 1.4.0               | 1.19, 1.18, 1.17    | yes       |
| 1.3.0               | 1.18, 1.17, 1.16    | yes       |
| 1.2.0               | 1.17, 1.16, 1.15    | yes       |
| 1.1.0               | 1.16, 1.15, 1.14    | no        |

> :warning: please note at this time this table is an example of the versioning we wish to support.  As we are not at 1.0 currently this is not accurate.

## Alpha/beta/Release Candidate K8s
One of our missions is to adopt and validate Kubernetes versions running on Azure as early as possible. For any pre-release (alpha/beta/rc) versions of Kubernetes any clusters built via aks-engine are considered experimental and may not be fully reliable.  There is no support and its use is for development/validation purposes only.



## Inspired by 
https://istio.io/latest/about/release-cadence/

https://helm.sh/docs/topics/version_skew/