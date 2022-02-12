# Postgres book notes

**Some terminology**

* Cluster - PostgresSQL instance that servers/ handles multiple databases
* Schema - namespaces; mneomonic name that the user can assign to organize database objects such as tables, into a more structured collection
* Database objects - anything user can create or manage within the database (tables, functions, triggers and data types)
  * Every db object belongs to one and only schema; by default its the public schema
* Users - defined at cluster-wide level
  * normal users
  * superusers: admin
* Catalogs - special tables that present meta data/ internal data in a SQL interactive way
  * where Postgres keeps track of table structures, indexes, functions, etc
  * information schema
* `PGDATA` - directory on the host computer where all content (user data and internal status) is stored
  * Represents  what the cluster is serving as databases
  * Switching PGDATA directories means to deliver different content
  * Needs to be initalized before used
  * Contains config data and WALs (write-ahead logs)
* WALs - write ahead logs used to save operations for transactions data consistency
* postmaster - waits for incoming lcient connections and forks "backend processes" which serves client connections

```
PostgreSQL provides you with executables that can be installed wherever you want on your system and can serve a single cluster. The cluster, in turn, serves data out of a single PGDATA directory that contains, among other stuff, the user data, the cluster internal status, and the WALs. Every time a client connects to the server, the postmaster process forks a new backend process that is the minion in charge of serving the connection.
```

## Cluster management ##

* `pg_ctl`
  * CLI tool for doing actions on cluster
  * `start, stop, restart, status, init, reloaded, etc`
  * Postgres does not allow root user to run pg_ctl
    * user `postgres` is the normal user who runs it
      * so login in as `postgres` to use pg_ctl stuff
  * `pg_ctl` requires `PGDATA` directory which can be provided as a env vraible with `-D` or by setting `PGDATA` env variable
    * `PGDATA` can only be used by one version of postgres...so name it after postgres version to make it clear who owns it

* processes
  * postmaster is the root of all Posgres processes
  * backend process
    * responsible for serving client requests (queires and returning results)

* Connecting
  * You connect to a specific database, not entire cluster
  * clusters are init. with one database (and one backup copy...tempalte1 and template0)
  * psql CLI that allows you to interact with, connect, or administer databases and the cluster itself

* Template dAtabses
  * `template1` first db created when cluster is init.
    * cloned into `template0` which is the safe copy for rebuilding in case `template1` gets messed up
      * you can't connect to it
  * template1 serves as a template for all dbs created that use it as a base tempalte
    * you can customize it

* `psql`
  * Uses `-d` database name, `-U` username, and `-h` host (ipv4, ipv6, or hostname) to connect to DB
    * if these arent provided ^ then current user is asssumed connecting on a local connection
