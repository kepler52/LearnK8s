## Configmap
A ConfigMap is an API object used to store non-confidential data in key-value pairs. Pods can consume ConfigMaps as environment variables, command-line arguments, or as configuration files in a volume.

### USING THE KUBECTL CREATE CONFIGMAP COMMAND


 in each container, Kubernetes also automatically
exposes environment variables for each service in the same namespace. These
environment variables are basically auto-injected configuration.