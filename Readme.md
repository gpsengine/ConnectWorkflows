# Shared Workflows for Connect application

The workflows contained here are for usage in Connect application repos.


## production-release.yaml

### Function

Build the component and push to production artifact registry, then update ConnectProduction to use
the new tagged version. Runs in `production` environment.

### Usage

```yaml
name: Release to production
on:
  release:
    types: [published]

jobs:
  production-release:
    uses: gpsengine/ConnectWorkflows/.github/workflows/production-release.yaml@v1
    with:
      app: backend
    secrets: inherit
```


## staging-push.yaml

### Function

Build the component and push to staging artifact registry, then update ConnectStaging to use
the newly build product (tagged with SHA). Runs in `staging` environment.

### Usage

```yaml
name: Build and push to staging
on:
  workflow_dispatch:
  push:
    branches:
      - master

jobs:
	staging-push:
    uses: gpsengine/ConnectWorkflows/.github/workflows/staging-push.yaml@v1
    with:
      app: backend
    secrets: inherit
```

