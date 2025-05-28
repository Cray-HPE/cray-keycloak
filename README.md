# Project Name

Cray-Keycloak

## Description

Deploys Keycloak

Uses the community-supported Keycloak helm chart, see
https://github.com/codecentric/helm-charts/tree/keycloakx-2.1.0/charts/keycloakx

Check the requirements.yaml/requirements.lock files for the current version.

Need to:

```
helm repo add codecentric https://codecentric.github.io/helm-charts
```

Our previous chart created a service called `keycloak` while the codecentric
chart creates a Service called `cray-keycloak-http`. For backwards compatibility
a `keycloak` service is created. The `keycloak` service is deprecated and
`cray-keycloak-http` must be used instead.

An istio virtual service is created for ingress. Keycloak is on `/keycloak`.

Keycloak is configured to use the Postgres operator set up by
cray-postgres-operator. The postgres.yaml file is essentially copied from the
cray-service chart.

When upgrading

* Update the tag in the github link above.
* check for NOTEs in the values.yaml

### Updating the Docker Image

Please update and create the change in the keycloak-installer repo. Once that is released then
change the chart version, and the app version in the Chart.yaml file. Also update the image
tag in the Values file.

## Contributing

See the [CONTRIBUTING.md](CONTRIBUTING.md) file for how to contribute to this project.

## Changelog

See the [CHANGELOG.md](CHANGELOG.md) for the changes and release history of this project.

## License

This project is copyrighted by Hewlett Packard Enterprise Development LP and is distributed under the MIT license. See the [LICENSE.txt](LICENSE.txt) file for details.
