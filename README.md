# helm-chart-resource

This resource allows you to monitor a [Helm](https://helm.sh) repository for
new versions to a chart.

## Source Configuration
* `repository_url`: *Required*. The Base URL of the Helm Repository (The URL you would use in `helm repo add`).
* `chart`: *Required*. The name of the helm chart.
* `username`: *Optional*. If HTTP Basic Authorization is required, the username to authenticate.
* `password`: *Optional*. If HTTP Basic Authorization is required, the password to authenticate.
* `skip_tls_validation`: *Optional*. Please don't (defaults to `false`)
* `sort_by`: *Optional*. Defaults to `semver`. If versions are not semantically versioned, use `created` instead.

## Behavior

### `check`: Discover new chart versions
Reports the latest version for the specified chart in the repository.

### `in`: Fetches the chart files from the repository
Fetches all files specified.

#### Parameters
* `skip_download`: Default `false`. If `true`, no files will be downloaded.
* `globs`: A list of linux-style globs to match agains the specified files in the chart. 
  If no globs are set, all files will be downloaded.

If `skip_download` is `true`, the `globs` field is ignored.