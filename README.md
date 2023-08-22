# Where for Dinner

Where For Dinner with ACS integration.

## Assumptions

The ACS package should already be installed into your TAP cluster.  If you do not already have TAP installed, install ACS with the following command:

```
tanzu package install acs --package application-configuration-service.tanzu.vmware.com --version <version> -n tap-install
```

## Deployment Guides

To demonstrate ACS integration, this can be done by simply deploying the Crawler service along with ACS `ConfigurationSource` and `ConfigurationSlice` resources.

### Create Configuration Source And Slices

Create the configuration source by running the following command from the `./config/app-operator` directory replacing the workload namespace with the appropriate namespace.

```
kubectl apply -f configurationSource.yaml -n <workload namespace>
```

Create the ConfigurationSlice for the Where For Dinner applications by running the following command from the `./config/app-operator` directory replacing the workload 
namespace with the appropriate namespace.


```
kubectl apply -f configurationSlice.yaml -n <workload namespace>
```

### Deploy the Crawler Service


Deploy the crawler service by running the following command from the `./where-for-dinner-crawler`

```
tanzu apps workload apply -f config/workload.yaml -n workloads
```
