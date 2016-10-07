# Ansible Role: SonarQube on Postgres

[![Build Status](https://travis-ci.org/carlosfunk/ansible-role-sonar.svg?branch=master)](https://travis-ci.org/carlosfunk/ansible-role-sonar)

An Ansible Role that installs [SonarQube](http://www.sonarqube.org/) on RedHat/CentOS and Debian/Ubuntu Linux servers.

## Requirements

Requires the `unzip` utility to be installed on the server. Also, different SonarQube versions require different minimum versions of Java:

  - SonarQube 5.0-5.5 requires Java 1.7+
  - SonarQube 5.6+ requires Java 1.8+

## Role Variables

Available variables are listed below, along with default values:

    workspace: /root

Directory where downloaded files will be temporarily stored.

    sonar_download_url: http://dist.sonar.codehaus.org/sonarqube-4.5.4.zip
    sonar_version_directory: sonarqube-4.5.4

The URL from which SonarQube will be downloaded, and the resulting directory name (should match the download archive, without the archive extension).

    sonar_database_username: sonar
    sonar_database_password: sonar
    
    sonar_database_host: localhost
    sonar_database_port: "3306"
    sonar_database: sonar
    
    sonar_database_allowed_hosts:
      - 127.0.0.1
      - ::1
      - localhost

JDBC settings for the database. Defaults presume the database resides on localhost and is only accessible on the SonarQube server itself.

## Dependencies

  - geerlingguy.java
  - ANXS.postgresql

## Example Playbook

    - hosts: all
      roles:
        - geerlingguy.sonar

Using the defaults, you can view the SonarQube home at `http://localhost:9000/` (default System administrator credentials are `admin`/`admin`).

## License

MIT / BSD

## Author Information

This role was created by [Jeff Geerling](http://jeffgeerling.com/) and subsequently changed from MySQL to Postgres by [Carl](https://github.com/carlosfunk)