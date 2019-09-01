# Checking DNS Domain Expiration

* Format domain file

<pre>
$ cat domains
spotch.com 60
yahoo.com 60
prefetch.net 2000
google.com 80
</pre>

* Untuk melihat secara langsung tanggal expire domain bisa dengan opsi --interactive

<pre>
$ dns-domain-expiration-checker.py --interactive --domainfile domains
Domain Name                Registrar                       Expiration Date       Days Left
prefetch.net               DNC HOLDINGS, INC.              2020-06-23 00:00:00   1064
spotch.com                 GANDI SAS                       2017-12-03 00:00:00   131 
google.com                 MARKMONITOR INC.                2020-09-14 00:00:00   1147
</pre>

* Untuk alert ke email jika sudah mendekati expire

<pre>
$ dns-domain-expiration-checker.py --domainname prefetch.net --email --smtpfrom "root@mail.com" --smtpto "admin@mail.com" --expiredays 90

$ dns-domain-expiration-checker.py --domainfile domains --email --smtpserver smtp.mydomain --smtpto "biff" --smtpfrom "Root"
</pre>

# Installation

* Ubuntu based OS:

<pre>
apt install virtualenv -y
cd /data/ && virtualenv python-domain
cd python-domain && source bin/activate
pip install python-dateutil
git clone https://github.com/widyamedia/domain-check
cd domain-check
</pre>

* Pasang di crontab untuk menjalankan setiap bulan

3 3 3 * * /data/python-domain/domain-check/domain-check.sh

# Thanks

Forked from: https://github.com/Matty9191/dns-domain-expiration-checker
