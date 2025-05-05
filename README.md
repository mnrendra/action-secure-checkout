# mnrendra/action-secure-checkout

A [**GitHub Action**](https://github.com/features/actions) for securely checking out a repository with safe credential handling.

Uses [`actions/checkout`](https://github.com/actions/checkout) with `persist-credentials: false` by **default** for secure access,  
and automatically sets `persist-credentials: true` if a custom `token:` is provided that differs from `${{ github.token }}`.

*The purpose of this action is to minimize the number of defined inputs in reusable secure workflows.*

## Usage

```yml
- uses: mnrendra/action-secure-checkout@v1 # Pin to a commit SHA for improved security.
  with:
    # Repository name with owner. For example, actions/checkout
    # Default: ${{ github.repository }}
    repository: ''

    # The branch, tag or SHA to checkout. When checking out the repository that
    # triggered a workflow, this defaults to the reference or SHA for that event.
    # Otherwise, uses the default branch.
    ref: ''

    # Personal access token (PAT) used to fetch the repository. The PAT is configured
    # with the local git config, which enables your scripts to run authenticated git
    # commands. The post-job step removes the PAT.
    #
    # We recommend using a service account with the least permissions necessary. Also
    # when generating a new PAT, select the least scopes necessary.
    #
    # [Learn more about creating and using encrypted secrets](https://help.github.com/en/actions/automating-your-workflow-with-github-actions/creating-and-using-encrypted-secrets)
    #
    # Default: ${{ github.token }}
    token: ''

    # SSH key used to fetch the repository. The SSH key is configured with the local
    # git config, which enables your scripts to run authenticated git commands. The
    # post-job step removes the SSH key.
    #
    # We recommend using a service account with the least permissions necessary.
    #
    # [Learn more about creating and using encrypted secrets](https://help.github.com/en/actions/automating-your-workflow-with-github-actions/creating-and-using-encrypted-secrets)
    ssh-key: ''

    # Known hosts in addition to the user and global host key database. The public SSH
    # keys for a host may be obtained using the utility `ssh-keyscan`. For example,
    # `ssh-keyscan github.com`. The public key for github.com is always implicitly
    # added.
    ssh-known-hosts: ''

    # Whether to perform strict host key checking. When true, adds the options
    # `StrictHostKeyChecking=yes` and `CheckHostIP=no` to the SSH command line. Use
    # the input `ssh-known-hosts` to configure additional hosts.
    # Default: true
    ssh-strict: ''

    # The user to use when connecting to the remote SSH host. By default 'git' is
    # used.
    # Default: git
    ssh-user: ''

    # Whether to configure the token or SSH key with the local git config
    # Default: false
    persist-credentials: ''

    # Relative path under $GITHUB_WORKSPACE to place the repository
    path: ''

    # Whether to execute `git clean -ffdx && git reset --hard HEAD` before fetching
    # Default: true
    clean: ''

    # Partially clone against a given filter. Overrides sparse-checkout if set.
    # Default: null
    filter: ''

    # Do a sparse checkout on given patterns. Each pattern should be separated with
    # new lines.
    # Default: null
    sparse-checkout: ''

    # Specifies whether to use cone-mode when doing a sparse checkout.
    # Default: true
    sparse-checkout-cone-mode: ''

    # Number of commits to fetch. 0 indicates all history for all branches and tags.
    # Default: 1
    fetch-depth: ''

    # Whether to fetch tags, even if fetch-depth > 0.
    # Default: false
    fetch-tags: ''

    # Whether to show progress status output when fetching.
    # Default: true
    show-progress: ''

    # Whether to download Git-LFS files
    # Default: false
    lfs: ''

    # Whether to checkout submodules: `true` to checkout submodules or `recursive` to
    # recursively checkout submodules.
    #
    # When the `ssh-key` input is not provided, SSH URLs beginning with
    # `git@github.com:` are converted to HTTPS.
    #
    # Default: false
    submodules: ''

    # Add repository path as safe.directory for Git global config by running `git
    # config --global --add safe.directory <path>`
    # Default: true
    set-safe-directory: ''

    # The base URL for the GitHub instance that you are trying to clone from, will use
    # environment defaults to fetch from the same instance that the workflow is
    # running from unless specified. Example URLs are https://github.com or
    # https://my-ghes-server.example.com
    github-server-url: ''
```

## Example

### Checkout without custom token:
```yml
- uses: mnrendra/action-secure-checkout@v1 # Pin to a commit SHA for improved security.
```
This checks out the repository using `actions/checkout` with `persist-credentials: false`.

### Checkout with custom token:
```yml
- uses: mnrendra/action-secure-checkout@v1 # Pin to a commit SHA for improved security.
  with:
    token: ${{ secrets.TOKEN }}
```
This checks out the repository using `actions/checkout` with `persist-credentials: true` due to the custom token.

### Checkout with `token: ${{ github.token }}`:
```yml
- uses: mnrendra/action-secure-checkout@v1 # Pin to a commit SHA for improved security.
  with:
    token: ${{ github.token }}
```
This checks out the repository using `actions/checkout` with `persist-credentials: false` since the provided token is identical to `${{ github.token }}`.

### Checkout with `token: ${{ github.token }}` and `persist-credentials: true`:
```yml
- uses: mnrendra/action-secure-checkout@v1 # Pin to a commit SHA for improved security.
  with:
    token: ${{ github.token }}
    persist-credentials: true
```
This checks out the repository using `actions/checkout` with `persist-credentials: true` since the `persist-credentials` is explicitly set to `true`.

## Security

We take security seriously in this project. If you discover a **vulnerability**, we strongly encourage you to report it in a responsible manner.

Please open a [Security Advisory](/security/advisories/new) to report any vulnerabilities.

For more information, please refer to our [Security Policy](/blob/HEAD/SECURITY.md).

## Contributing

We appreciate your help in making this project better. Please follow the [guidelines](/blob/HEAD/CONTRIBUTING.md) to ensure that your contributions are smoothly integrated.

## License
[MIT](/blob/HEAD/LICENSE)

## Author
[@mnrendra](https://github.com/mnrendra)
