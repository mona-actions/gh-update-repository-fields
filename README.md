# Update repository fields

**GitHub CLI** extensions are repositories that provide additional `gh` commands, and this **GitHub CLI** extension helps to automatically update all repositories in an organization.

## GHES Compatibility
The **gh-update-repository-fields** extension supports the following versions of GitHub Enterpise Server (GHES):

- Supported: >= 2.20
- Not Supported: <= v2.19

*It should be noted that support for versions < 3.1 is limited.*

## Prerequisites

- Operating system that can run shell scripts (*bash/sh*)
- **GitHub CLI** installed by following this documentation: <https://github.com/cli/cli#installation>
- **jq** command-line JSON parser: <https://stedolan.github.io/jq/>
- You have ownership/admin permissions in the organization where you want to migrate to
- You have ownership/admin permission in the source GitHub GHEC/EMU where you can migrate from
- You need to create a GitHub **Personal Access Token** with all `repo` permission `admin:org` permission your organization. Alternatively, you can use GitHub App token or GitHub OAuth token

| Environment Variable name | Value                                                                                       |
| ------------------------- | ------------------------------------------------------------------------------------------- |
| GHE_URL | GitHub URL or GHES URL where you want to migrate. Defaults to `https://github.com` |
| GH_TOKEN | GitHub Personal Access Token (PAT) for your organization with all `repo` permission `admin:org` permission  |
| ORGANIZATION | Organization that you wants to perform operation  |

Or the script will prompt you to put in the relevant information.

## CLI options

```text
Usage: gh update-repository-fields [options]
Options:
    -h, --help                    : Show script help
    -desc, --description          : Set description field for GitHub repositories. Looks for DESCRPTION environment
                                    variable if omitted
    -u, --url                     : Set destination GitHub URL (e.g. https://github.example.com) Looks for GHE_URL environment
                                    variable if omitted or defaults to https://github.com                                 
    -o, --organization            : Set organization to update information from -- Looks for ORGANIZATION environment
                                    variable if omitted
    -t, --token                   : Set token used to perform actions - Look for GH_TOKEN
                                    variable if omitted
Description:
gh-update-repository-fields updates all the repositories under an organization -- currently only support description
Example:
  gh update-repository-fields -u https://ghes-url.com -o my-org -t ABCDEFG1234567
```

## How to run

Make sure you followed prerequisites and then follow these instructions.

### Step 1: Install GitHub extension

```sh
gh extension install mona-actions/gh-update-repository-fields
```

### Step 2: Run gh migrate-team-permission

```sh
gh update-repository-fields -o my-org -t ABCDEFG1234567
```