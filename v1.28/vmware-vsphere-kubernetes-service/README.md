# Conformance testing vSphere Kubernetes Service



## Setup Cluster

Setup cluster according to the [documentation](https://docs.vmware.com/en/VMware-vSphere/8.0/vsphere-with-tanzu-tkg/GUID-918803BD-123E-43A5-9843-250F3E20E6F2.html).
 Please mention TKR version to v1.28.7---vmware.1-fips.1-tkg.1 while deploying cluster .Refer [here](https://docs.vmware.com/en/VMware-Tanzu-Kubernetes-releases/services/rn/vmware-tanzu-kubernetes-releases-release-notes/index.html) for vSphere 8.x 


## Deploy Sonobuoy Conformance test

[Download](https://github.com/vmware-tanzu/sonobuoy)  Sonobuoy binary release and follow the conformance suite instructions to run sonobuoy test. 


### Run Sonobuoy e2e
```
./sonobuoy run --mode=certified-conformance
results=$(./sonobuoy retrieve)
mkdir ./results
tar xzf $results -C ./results
./sonobuoy e2e ${results}
mv results/plugins/e2e/results/global/* .
```
