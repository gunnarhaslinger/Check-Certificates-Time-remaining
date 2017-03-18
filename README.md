# check_certificates_time-remaining
Check WebServer Certificates, remind you of remaining time left to renew

I supervise all my (Let's Encrypt) certificates I'm using on my Apache-Webserver with a little Perl-Scripts I wrote.

three Variables to configure:
$limit = 30;
$LetsEncrytpCertDir="/etc/letsencrypt/live";
$ApacheConfigs="/etc/apache2/sites-enabled/*";

It enumerates all Certificates used in the Apache-Config-Files found in the $ApacheConfigs Directory and all certificate-files found in the $LetsEncrytpCertDir subdirectories.

It outputs details for all certificates with a less remaining time than $limit days.

Just link this script into your crontab.
If no certificate is within the 30-day period no output occurs (silent cronjob run).

Interactive usage with Verbose-Output: just use parameter "-v"
Help-Output: "-?"
