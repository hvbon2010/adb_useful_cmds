# Repo installation
You can install it manually:

`mkdir -p ~/.bin`

`PATH="${HOME}/.bin:${PATH}"`

`curl https://storage.googleapis.com/git-repo-downloads/repo > ~/.bin/repo`

`chmod a+rx ~/.bin/repo`

# Help

`repo help [command]`

Example: `repo help sync`

Usage: repo sync [<project>...]

Options:

  `-h, --help`            show this help message and exit

  `-j JOBS, --jobs=JOBS`  number of jobs to run in parallel (default: 6; based
                          on number of CPU cores)

  `--jobs-network=JOBS`   number of network jobs to run in parallel (defaults to
                          --jobs)

  `--jobs-checkout=JOBS`  number of local checkout jobs to run in parallel
                          (defaults to --jobs)

  `-f, --force-broken`    obsolete option (to be deleted in the future)

  `--fail-fast`           stop syncing after first error is hit

  `--force-sync`          overwrite an existing git directory if it needs to
                          point to a different object directory. WARNING: this
                          may cause loss of data

  `--force-remove-dirty`  force remove projects with uncommitted modifications
                          if projects no longer exist in the manifest. WARNING:
                          this may cause loss of data

  `-l, --local-only`      only update working tree, don't fetch

  `--no-manifest-update, --nmu`
                          use the existing manifest checkout as-is. (do not
                          update to the latest revision)

  `-n, --network-only`    fetch only, don't update working tree

  `-d, --detach`          detach projects back to manifest revision

  `-c, --current-branch`  fetch only current branch from server

  `--no-current-branch`   fetch all branches from server

  `-m NAME.xml, --manifest-name=NAME.xml`
                          temporary manifest to use for this sync

  `--clone-bundle`        enable use of /clone.bundle on HTTP/HTTPS

  `--no-clone-bundle`     disable use of /clone.bundle on HTTP/HTTPS

  `-u MANIFEST_SERVER_USERNAME, --manifest-server-username=MANIFEST_SERVER_USERNAME`
                          username to authenticate with the manifest server

  `-p MANIFEST_SERVER_PASSWORD, --manifest-server-password=MANIFEST_SERVER_PASSWORD`
                          password to authenticate with the manifest server

  `--fetch-submodules`    fetch submodules from server

  `--use-superproject`    use the manifest superproject to sync projects;
                          implies -c

  `--no-use-superproject`
                          disable use of manifest superprojects

  `--tags`                fetch tags

  `--no-tags`             don't fetch tags (default)

  `--optimized-fetch`     only fetch projects fixed to sha1 if revision does not
                          exist locally

  `--retry-fetches=RETRY_FETCHES`
                          number of times to retry fetches on transient errors

  `--prune`               delete refs that no longer exist on the remote
                          (default)

  `--no-prune`            do not delete refs that no longer exist on the remote

  `-s, --smart-sync`      smart sync using manifest from the latest known good
                          build

  `-t SMART_TAG, --smart-tag=SMART_TAG`
                          smart sync using manifest from a known tag

Logging options:

  `-v, --verbose`       show all output

  `-q, --quiet`         only show errors

repo Version options:

  `--no-repo-verify`    do not verify repo source code

# Repo init

`repo init -u [url] -m [manifest-file] -b [manifest-branch]`

`-u`: Specify a URL from which to retrieve a manifest repository. The common manifest is found at https://android.googlesource.com/platform/manifest.

`-m`: Select a manifest file within the repository. If no manifest name is selected, the default is default.xml.

`-b`: Specify a revision, that is, a particular manifest-branch.

# Repo sync

Normal sync:

`repo sync -j$(num_of_process)`

Quick sync (1):

`repo sync -d -c -q --force-sync --jobs=$(num_of_process) --no-tags`

Quick sync (2):

`repo sync --no-clone-bundle --no-tags -j6`

# Repo diff

Show git diff of all projects all the manifest file:

`repo diff`

# Repo status

Show git status of all projects all the manifest file:

`repo status`

# Repo forall

Loop for excute a command.

`repo forall [options] [command]`

`-c`: Command and arguments to execute. The command is evaluated through /bin/sh and any arguments after it are passed through as shell positional parameters.

`-p`: Show project headers before output of the specified command. This is achieved by binding pipes to the command's stdin, stdout, and sterr streams, and piping all output into a continuous stream that is displayed in a single pager session.

`-v`: Show messages the command writes to stderr.


Example: clean and reset all projects in repo

`repo forall -vc "git reset --hard HEAD ; git clean -fd"`

