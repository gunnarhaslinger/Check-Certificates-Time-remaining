# check_certificates_time-remaining.pl
Check WebServer Certificates, remind you of remaining time left to renew

I supervise all my (Let's Encrypt) certificates I'm using on my Apache-Webserver with a little Perl-Scripts I wrote.

## Configuration
three Variables to configure:
$limit = 30;
$LetsEncrytpCertDir="/etc/letsencrypt/live";
$ApacheConfigs="/etc/apache2/sites-enabled/*";

It enumerates all Certificates used in the Apache-Config-Files found in the $ApacheConfigs Directory and all certificate-files found in the $LetsEncrytpCertDir subdirectories.

It outputs details for all certificates with a less remaining time than $limit days.

## Crontab Usage
Just link this script into your crontab.
If no certificate is within the 30-day period no output occurs (silent cronjob run).

## Interactive Usage
```
# ./check_certificates_time-remaining.pl -?
Commandline arguments:
Without Arguments: Only shows Certificates valid for less than 30 days.
-limit=20 ... show only certificates valid for less than n (20) days
-v ... Verbose Output
-vv ... Debug Output
```

## Prerequisites
Uses two perl-modules you maybe have to install first, on Debian/Ubuntu it's:
```
apt install libcrypt-openssl-x509-perl
apt install libdatetime-format-strptime-perl
```

## Sample-Output 
```
./check_certificates_time-remaining.pl -v
...
it-security.eu.org         88 Days difference now to 14.06.2017 18:15:00 UTC
                              File: /etc/letsencrypt/live/it-security.eu.org/fullchain.pem
                              AltName: 0r
                                       demo.it-sec.ovh
                                       demo.it-security.eu.org
                                       it-sec.ovh
                                       it-security.eu.org
                                       www.it-sec.ovh
                                       www.it-security.eu.org
...
```
