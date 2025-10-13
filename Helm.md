---
date: 2025-03-11
tags:
  - kubernetes
  - docker
---
Bundles kubernetes resources like [[Kubernetes Service|Services]], ConfigMaps, Deployments etc into a single chart. It allows to parameterize configurations to customize deployments. It has versioning and can be reused. Supports rollbacks, upgrades, installs etc. 
In essence it abstracts away a lot of fluff and we can deploy entire clusters with just one yaml file.  

## Terminology 

- Chart: Packaged collection of kubernetes resources.
- Release: Deployed instance of a helm chart. When a chart is installed, helm creates a release. Each release has a name and version, which helps manage rollbacks, updates and tracking of multiple installations of the same chart. 
- Repository: Place where charts can be collected and shared. 

## Common commands

Add a new chart repository under a given name so that we can search and install charts from that repo.
```
helm repo add <reponame> <repo_url>
```

Update all the local chart repo cache by downloading the latest index files.
```
helm repo update
```

Search for charts in the added repo that match given name or keyword.
```
helm search repo <chart_name>
```

Install a chart into the cluster as a new release. Custom config values can be supplied to tailor the deployment. 
```
helm install <release_name> <chart>
```

Upgrade an existing release to a new version of the chart or applies new config values. This allows to update the deployment without downtime. 
```
helm upgrade <release_name> <chart>
```

Roll back installed release to its previous revision. 
```
helm rollback <release_name> <revision>
```

Uninstall (delete) the release from the cluster.
```
helm unistall <release_name>
```

List all releases installed on the cluster. 
```
helm list
```

Displays detailed information about specific release.
```
helm status <release_name>
```

Check common issues and best practice violations.
```
helm lint <chart_directory>
```


### References

