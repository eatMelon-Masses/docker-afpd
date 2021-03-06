![Logo](http://svg.wiersma.co.za/github/project?lang=docker&title=afpd)

A lightweight Docker container serving AppleTalk Filing Protocol.

## Configure users

Users are setup using two files: ```names``` and ```users```.

The names file should mounted to ```/names``` and have the following format:

```
username:full name
username:full name
```

The users file should mounted to ```/users``` and have the following format (as expected by ```chpasswd```):

```
username:<password hash>
username:<password hash>
```

Password hashes can be created with ```mkpasswd```.

## Configuring Shares

Shares can be configured by mounting an afpd.conf file into ```/usr/local/etc/afp.conf```.

Documentation for the afpd.conf can be found in [Netatalk's documentation](http://netatalk.sourceforge.net/3.0/htmldocs/afp.conf.5.html).

## Ports

Ports 548 is exposed and should be mounted to the host ports

## Example

```
    docker run --detach
               -v /path/to/local/afpd.conf:/usr/local/etc/afp.conf
               -p 548:548
               nrwiersma/docker-afpd:latest
```
