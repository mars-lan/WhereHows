# WhereHows [![Build Status](https://travis-ci.org/linkedin/WhereHows.svg?branch=master)](https://travis-ci.org/linkedin/WhereHows)

WhereHows is a data discovery and lineage tool built at LinkedIn. It integrates with all the major data processing systems and collects both catalog and operational metadata from them.

Within the central metadata repository, WhereHows curates, associates, and surfaces the metadata information through two interfaces:
* a web application that enables data & linage discovery, and community collaboration
* an API endpoint that empowers automation of data processes/applications

WhereHows serves as the single platform that:
* links data objects with people and processes
* enables crowdsourcing for data knowledge
* provides data governance and provenance based on ownership and lineage

## Documentation

The detailed information can be found in the [Wiki][wiki]


## Examples in VM

There is a pre-built vmware image (about 11GB) to quickly demonstrate the functionality of WhereHows. Check out the [VM Guide][VM]


## Getting Started

New to Wherehows? Check out the [Getting Started Guide][GS]

### Preparation

First, please [setup the metadata repository][DB] in MySQL.
```
CREATE DATABASE wherehows
  DEFAULT CHARACTER SET utf8
  DEFAULT COLLATE utf8_general_ci;

CREATE USER 'wherehows';
SET PASSWORD FOR 'wherehows' = PASSWORD('wherehows');
GRANT ALL ON wherehows.* TO 'wherehows'
```

Execute the [DDL files][DDL] to create the required repository tables in **wherehows** database.


### Build

1. Get the source code: ```git clone https://github.com/linkedin/WhereHows.git```
2. Put a few 3rd-party jar files to **metadata-etl/extralibs** directory. Some of these jar files may not be available in Maven Central or Artifactory. See [the download instrucitons][EXJAR] for more detail. ```cd WhereHows/metadata-etl/extralibs```
3. From the **WhereHows** root directory and build all the modules: ```./gradlew build```
4. Start the metadata ETL and API service: ```./gradlew backend-service:runPlayBinary```
5. In a new terminal, start the web front-end: ```./gradlew web:runPlayBinary```. The WhereHows UI is available at http://localhost:9000 by default. You can change the port number by editing the value of ```project.ext.httpPort``` in ```web/build.gradle```.

## Contribute

Want to contribute? Check out the [Contributors Guide][CON]

## Community

Want help? Check out the [Google Groups][LIST]


[wiki]: https://github.com/LinkedIn/Wherehows/wiki
[GS]: https://github.com/LinkedIn/Wherehows/wiki/Getting-Started
[CON]: https://github.com/LinkedIn/Wherehows/wiki/Contributing
[VM]: https://github.com/LinkedIn/Wherehows/wiki/Quick-Start-With-VM
[EXJAR]: https://github.com/LinkedIn/Wherehows/wiki/Getting-Started#download-third-party-jar-files
[DDL]: https://github.com/linkedin/WhereHows/tree/master/data-model/DDL
[DB]: https://github.com/LinkedIn/Wherehows/wiki/Getting-Started#set-up-your-database
[LIST]: https://groups.google.com/forum/#!forum/wherehows
