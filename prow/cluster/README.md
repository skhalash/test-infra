# Cluster

## Overview

This folder contains configuration files of the Prow production cluster that are used during the cluster provisioning.

### Project structure

<!-- Update the folder structure each time you modify it. -->

The structure of the folder looks as follows:

```
  ├── components                # Directory with yaml definitions of prow production cluster components
  ├── resources                 # Directory with configuration files additional services running on prow cluster
  └── required-secrets.yaml             # A default list of required Secrets that must be stored in a storage bucket
```

### Required secrets structure
The `required-secrets.yaml` file is read by `secretspopulator` and consists of required Secrets stored in a Google Cloud Storage (GCS) bucket.
You can define two kinds of Secrets:
- Service accounts
- Generic Secrets

`Secretspopulator` looks for a `{prefix}.encrypted` object in a bucket and creates a Kubernetes Secret with a `{prefix}` name.
For service accounts, the Secret key is `service-account.json`. For generic Secrets, you must provide a key.
For more details about the syntax of this file, see the `RequiredSecretsData` type in `development/tools/cmd/secretspopulator/secretspopulator`.
