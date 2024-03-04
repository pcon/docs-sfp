# Pool

## `@flxblio/sfp pool`

Build and manage scratch org or sandbox pools

* `@flxblio/sfp pool delete`
* `@flxblio/sfp pool fetch`
* `@flxblio/sfp pool list`
* `@flxblio/sfp pool metrics publish`
* `@flxblio/sfp pool org delete`
* `@flxblio/sfp pool prepare`

### `@flxblio/sfp pool delete`

Deletes the pooled scratch orgs from the Scratch Org Pool

```
USAGE
  $ @flxblio/sfp pool delete -v <value> [-t <value>] [-i | -a] [-o] [--apiversion <value>] [--loglevel
    trace|debug|info|warn|error|fatal|TRACE|DEBUG|INFO|WARN|ERROR|FATAL]

FLAGS
  -a, --allscratchorgs                Deletes all used and unused Scratch orgs from pool by the tag
  -i, --inprogressonly                Deletes all In Progress Scratch orgs from pool by the tag
  -o, --orphans                       Recovers scratch orgs that were created by salesforce but were not tagged to sfp
                                      due to timeouts etc.
  -t, --tag=<value>                   tag used to identify the scratch org pool
  -v, --targetdevhubusername=<value>  (required) Username or alias of the Dev Hub org.
      --apiversion=<value>            Override the api version used for api requests made by this command
      --loglevel=<option>             [default: info] logging level for this command invocation
                                      <options: trace|debug|info|warn|error|fatal|TRACE|DEBUG|INFO|WARN|ERROR|FATAL>

DESCRIPTION
  Deletes the pooled scratch orgs from the Scratch Org Pool

EXAMPLES
  $ sfp pool:delete -t core 

  $ sfp pool:delete -t core -v devhub

  $ sfp pool:delete --orphans -v devhub
```

_See code:_ [_src/commands/pool/delete.ts_](https://github.com/flxbl-io/sfp)

### `@flxblio/sfp pool fetch`

Gets an active/unused scratch org from the scratch org pool

```
USAGE
  $ @flxblio/sfp pool fetch -v <value> -t <value> [--json] [-a <value>] [-s <value>] [-d] [--nosourcetracking]
    [--apiversion <value>] [--loglevel trace|debug|info|warn|error|fatal|TRACE|DEBUG|INFO|WARN|ERROR|FATAL]

FLAGS
  -a, --alias=<value>                 Fetch and set an alias for the org
  -d, --setdefaultusername            set the authenticated org as the default username that all commands run against
  -s, --sendtouser=<value>            Send the credentials of the fetched scratchorg to another DevHub user, Useful for
                                      situations when pool is only limited to certain users
  -t, --tag=<value>                   (required) (required) tag used to identify the scratch org pool
  -v, --targetdevhubusername=<value>  (required) Username or alias of the Dev Hub org.
      --apiversion=<value>            Override the api version used for api requests made by this command
      --loglevel=<option>             [default: info] logging level for this command invocation
                                      <options: trace|debug|info|warn|error|fatal|TRACE|DEBUG|INFO|WARN|ERROR|FATAL>
      --nosourcetracking              Do not set source tracking while fetching the scratch org

GLOBAL FLAGS
  --json  Format output as json.

DESCRIPTION
  Gets an active/unused scratch org from the scratch org pool

EXAMPLES
  $ sfp pool:fetch  -t core 

  $ sfp pool:fetch  -t core -v devhub

  $ sfp pool:fetch  -t core -v devhub -m

  $ sfp pool:fetch  -t core -v devhub -s testuser@test.com
```

_See code:_ [_src/commands/pool/fetch.ts_](https://github.com/flxbl-io/sfp)

### `@flxblio/sfp pool list`

Retrieves a list of active scratch org and details from any pool. If this command is run with -m|--mypool, the command will retrieve the passwords for the pool created by the user who is executing the command.

```
USAGE
  $ @flxblio/sfp pool list -v <value> [--json] [--apiversion <value>] [-t <value>] [-m] [-a] [--loglevel
    trace|debug|info|warn|error|fatal|TRACE|DEBUG|INFO|WARN|ERROR|FATAL]

FLAGS
  -a, --allscratchorgs                Gets all used and unused Scratch orgs from pool
  -m, --mypool                        Filter the tag for any additions created  by the executor of the command
  -t, --tag=<value>                   tag used to identify the scratch org pool
  -v, --targetdevhubusername=<value>  (required) Username or alias of the Dev Hub org.
      --apiversion=<value>            Override the api version used for api requests made by this command
      --loglevel=<option>             [default: info] logging level for this command invocation
                                      <options: trace|debug|info|warn|error|fatal|TRACE|DEBUG|INFO|WARN|ERROR|FATAL>

GLOBAL FLAGS
  --json  Format output as json.

DESCRIPTION
  Retrieves a list of active scratch org and details from any pool. If this command is run with -m|--mypool, the command
  will retrieve the passwords for the pool created by the user who is executing the command.

EXAMPLES
  $ sfp pool:list -t core 

  $ sfp pool:list -t core -v devhub

  $ sfp pool:list -t core -v devhub -m

  $ sfp pool:list -t core -v devhub -m -a
```

_See code:_ [_src/commands/pool/list.ts_](https://github.com/flxbl-io/sfp)

### `@flxblio/sfp pool metrics publish`

Publish metrics about scratch org pools to your observability platform, via StatsD or direct APIs for supported platforms

```
USAGE
  $ @flxblio/sfp pool metrics publish -v <value> [--loglevel
    trace|debug|info|warn|error|fatal|TRACE|DEBUG|INFO|WARN|ERROR|FATAL]

FLAGS
  -v, --targetdevhubusername=<value>  (required) Username or alias of the Dev Hub org.
      --loglevel=<option>             [default: info] logging level for this command invocation
                                      <options: trace|debug|info|warn|error|fatal|TRACE|DEBUG|INFO|WARN|ERROR|FATAL>

DESCRIPTION
  Publish metrics about scratch org pools to your observability platform, via StatsD or direct APIs for supported
  platforms

EXAMPLES
  $ sfp pool:metrics:publish -v <myDevHub>
```

_See code:_ [_src/commands/pool/metrics/publish.ts_](https://github.com/flxbl-io/sfp)

### `@flxblio/sfp pool org delete`

Deletes a particular scratch org in the pool, This command is to be used in a pipeline with correct permissions to delete any active scratch org record or to be used by an adminsitrator

```
USAGE
  $ @flxblio/sfp pool org delete -u <value> -v <value> [--apiversion <value>] [--loglevel
    trace|debug|info|warn|error|fatal|TRACE|DEBUG|INFO|WARN|ERROR|FATAL]

FLAGS
  -u, --targetusername=<value>        (required) Username or alias of the target org.
  -v, --targetdevhubusername=<value>  (required) Username or alias of the Dev Hub org.
      --apiversion=<value>            Override the api version used for api requests made by this command
      --loglevel=<option>             [default: info] logging level for this command invocation
                                      <options: trace|debug|info|warn|error|fatal|TRACE|DEBUG|INFO|WARN|ERROR|FATAL>

DESCRIPTION
  Deletes a particular scratch org in the pool, This command is to be used in a pipeline with correct permissions to
  delete any active scratch org record or to be used by an adminsitrator

EXAMPLES
  $ sfp pool:org:delete -u test-xasdasd@example.com -v devhub
```

_See code:_ [_src/commands/pool/org/delete.ts_](https://github.com/flxbl-io/sfp)

### `@flxblio/sfp pool prepare`

Prepare a pool of scratchorgs with all the packages upfront, so that any incoming change can be validated in an optimized manner

```
USAGE
  $ @flxblio/sfp pool prepare -v <value> [-f <value>] [--npmrcpath <value>] [--keys <value>] [-g <value>]
    [--loglevel trace|debug|info|warn|error|fatal|TRACE|DEBUG|INFO|WARN|ERROR|FATAL]

FLAGS
  -f, --poolconfig=<value>            [default: config/poolconfig.json] The path to the configuration file for creating
                                      a pool of scratch orgs
  -g, --logsgroupsymbol=<value>...    Symbol used by CICD platform to group/collapse logs in the console. Provide an
                                      opening group, and an optional closing group symbol.
  -v, --targetdevhubusername=<value>  (required) Username or alias of the Dev Hub org.
      --keys=<value>                  Keys to be used while installing any managed package dependencies. Required format
                                      is a string of key-value pairs separated by spaces e.g. packageA:pw123
                                      packageB:pw123 packageC:pw123
      --loglevel=<option>             [default: info] logging level for this command invocation
                                      <options: trace|debug|info|warn|error|fatal|TRACE|DEBUG|INFO|WARN|ERROR|FATAL>
      --npmrcpath=<value>             Path to .npmrc file used for authentication to a npm registry when using npm based
                                      artifacts. If left blank, defaults to home directory

DESCRIPTION
  Prepare a pool of scratchorgs with all the packages upfront, so that any incoming change can be validated in an
  optimized manner

ALIASES
  $ @flxblio/sfp orchestrator prepare
  $ @flxblio/sfp prepare

EXAMPLES
  $ sfp prepare -f config/mypoolconfig.json  -v <devhub>
```

_See code:_ [_src/commands/pool/prepare.ts_](https://github.com/flxbl-io/sfp)