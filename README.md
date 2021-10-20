<p align="center">
  <img alt="CYBERTEC Migrator" width="300px" src="https://www.cybertec-postgresql.com/wp-content/uploads/2018/03/Migrator_neu-300x79.png"/>
  <br/><br/>
  <i>Streamlined Oracle to PostgreSQL migration</i>
</p>

---

<p align="center">
  <a href="#getting-started">Getting Started</a> •
  <a href="#running-the-migrator">Running the Migrator</a> •
  <a href="#contact">Contact</a>
</p>

[_CYBERTEC Migrator_](https://www.cybertec-postgresql.com/en/products/cybertec-migrator/) is a streamlined and user-friendly tool that helps you to organize and efficiently migrate multiple Oracle databases to PostgreSQL.
In addition to migrating your data professionally and securely with minimum effort, _CYBERTEC Migrator_ allows you to visually monitor and track the whole process at any time.

<br/>

<p align="center">
  <a href="http://www.youtube.com/watch?v=8hSrFVOw3Rc"><img alt="CYBERTEC Migrator v3 Demonstration" width="384px" src="http://img.youtube.com/vi/8hSrFVOw3Rc/0.jpg"/></a><br/>
  <b>Product Demo</b>
</p>

---

For detailed information see the list of [supported migration features for Oracle](docs/oracle-migration-support.md).

## Table of Contents

1. [What's New](#whats-new)
2. [Getting Started](#getting-started)
3. [Running the Migrator](#running-the-migrator)
4. [Contact](#contact)

## What's New

- `v3.1.0`

  **Features**

  - Search and Replace  
    Perform bulk changes on column data types / default values, functions, views, and triggers (with support for even more object properties coming soon)

  - Significant Speed Improvements  
    **Feel** the difference

  - Resume Failed Stages  
    Spend less time fixing those last few migration errors

  - Realtime Syntax Checking  
    Get immediate feedback about the syntactical correctness of code

  - Partition Renaming  
    Rename partitions as part of a migration instead of altering the source database

  - Code Export  
    Export code of function / views / triggers (with code import coming soon)

  - Migration Deletion  
    Delete of completed migrations
    
  - Migration Cloning  
    Prepare migrations against your staging environment and then execute them against production

  **Resolved Bugs**

  - Keys for excluded columns are not excluded automatically
  - Column aliases in view code are not migrated
  - Migration status is sometimes displayed incorrectly
  - Excluding partition columns via the sidebar prevents the Structure stage from succeeding

- `v3.0.0`

  With _CYBERTEC Migrator_ v3 we've rebuilt the GUI from the ground up to simplify database migrations even further

  - Get a brief look at the structure of your source database by using the migration _Overview_
  - Quickly drill down into your data model with the help of the new _Sidebar_
  - Stages (natural synchronization points of a migration process) now guide you through the migration process
    - **Structure** stage: create database objects necessary to migrate the table data
    - **Data** stage: migrate table data in parallel
    - **Logic** stage: create functions, triggers, views
    - **Integrity** stage: parallel creation of primary keys, indices, foreign keys, and constraint checks
  - Enjoy quick round trips and gain confidence in the correctness of your migration thanks to the reworked _Migration Controls_
    - **Start** migration from the beginning
    - **Rerun stage** in case of an error
    - **Continue** to next stage
    - **Abort** migration and restart at any time
  - Explore the inner workings of your migration with the new, and easily accessible _Log View_
    - Log entries are inter-linked to the database objects configuration
    - Filter on log level (`ERROR`, `WARNING`, `INFO`, `VERBOSE`)
  - Extensive configuration
    - Exclude database objects (schemas, tables, columns, indexes, ...) from migration
    - Table editor to configure columns, constraints, indices, triggers, and partitions
    - Bulk change of data types (for example change all `NUMBER(4)` to `int`, instead of `smallint`)
    - Integrated code editor for functions, stored procedures, and views with diff feature

## Getting Started

### Requirements

_CYBERTEC Migrator_ is distributed as a set of [Docker](https://www.docker.com/) images that are brought up by [Docker Compose](https://docs.docker.com/compose/).

- [`docker`](https://docs.docker.com/get-docker/)
- [`docker-compose`](https://docs.docker.com/compose/install/) (`>= 1.27.0`)
- `git` (`>= 2.20.1`)
- `bash` (`>= 4.0`)

### Obtaining Images

_CYBERTEC Migrator_ images can be obtained through Docker Hub.  
An offline installation package is also available for environments in which networking restrictions are imposed.

- Docker Hub  
  Please [get in touch with us](#contact) if your account has not been granted access to the respective images.

  ```sh
  cat ~/password.txt | docker login --username <username> --password-stdin
  ```

- Offline installation package  
  Please [get in touch with us](#contact) to request download credentials.

### Setup

- Online installation

  1. Clone the repository
  2. Change directory into cloned repository
  3. Generate default configuration
  4. Download images

  <br/>

  ```sh
  git clone https://github.com/cybertec-postgresql/cybertec_migrator
  cd cybertec_migrator
  ./migrator configure
  ./migrator install
  ```

- Offline installation

  | 💡  | Installation archives also serve as upgrade archives |
    | --- | ---------------------------------------------------- |

  1. Extract the provided archive file
  2. Change directory to the directory created in the previous step
  3. Generate default configuration
  4. Import images from archive

  <br/>

  ```sh
  tar xf cybertec_migrator-vX.Y.Z.tar.gz
  cd cybertec_migrator
  ./migrator configure
  ./migrator install --archive ../cybertec_migrator-vX.Y.Z.tar.gz
  ```

## Running the Migrator

```sh
./migrator up
```

CYBERTEC Migrator only supports connections via HTTP.

The `EXTERNAL_HTTP_PORT` variable in the `.env` file (generated by `./migrator configure`) controls on which port the Migrator is served.

### Upgrades

| ⚠️  | Running migrations _will_ be interrupted by applying upgrades |
| --- | ------------------------------------------------------------- |

- Online upgrade

  1. Update release information
  2. Upgrade to newest version
  3. Apply upgrade

  <br/>

  ```sh
  ./migrator update
  ./migrator upgrade
  ./migrator up
  ```

- Offline upgrade

  1. Update release information
  2. Upgrade to version bundled in archive
  3. Apply upgrade

  <br/>

  ```sh
  ./migrator update --archive cybertec_migrator-vX.Y.Z.tar.gz
  ./migrator upgrade --archive cybertec_migrator-vX.Y.Z.tar.gz
  ./migrator up
  ```

## Contact

- [Sales](https://www.cybertec-postgresql.com/en/contact/)
- [Report Bug](https://cybertec.atlassian.net/servicedesk/customer/portal/3/group/4/create/23)
