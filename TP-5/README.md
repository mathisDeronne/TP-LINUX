# Partie 1 : Mise en place et maîtrise du serveur Web

## 1. Installation
| Machine         | IP            | Service     |
|-----------------|---------------|-------------|
| `web.tp5.linux` | `10.105.1.11` | Serveur Web |

🌞 **Installer le serveur Apache**

- paquet `httpd`
 ```
 [user@localhost ~]$ sudo dnf install httpd
[sudo] password for user:
Rocky Linux 9 - BaseOS                      7.2 kB/s | 3.6 kB     00:00
Rocky Linux 9 - BaseOS                      2.2 MB/s | 1.7 MB     00:00
Rocky Linux 9 - AppStream                    13 kB/s | 4.1 kB     00:00
Rocky Linux 9 - AppStream                   3.3 MB/s | 6.4 MB     00:01
Rocky Linux 9 - Extras                       11 kB/s | 2.9 kB     00:00
Rocky Linux 9 - Extras                       16 kB/s | 7.7 kB     00:00
Dependencies resolved.
============================================================================ Package                Arch        Version            Repository      Size
============================================================================Installing:
 httpd                  x86_64      2.4.53-7.el9       appstream       48 k
Installing dependencies:
 apr                    x86_64      1.7.0-11.el9       appstream      123 k
 apr-util               x86_64      1.6.1-20.el9       appstream       94 k
 apr-util-bdb           x86_64      1.6.1-20.el9       appstream       13 k
 httpd-core             x86_64      2.4.53-7.el9       appstream      1.4 M
 httpd-filesystem       noarch      2.4.53-7.el9       appstream       15 k
 httpd-tools            x86_64      2.4.53-7.el9       appstream       82 k
 mailcap                noarch      2.1.49-5.el9       baseos          32 k
 rocky-logos-httpd      noarch      90.13-1.el9        appstream       24 k
Installing weak dependencies:
 apr-util-openssl       x86_64      1.6.1-20.el9       appstream       15 k
 mod_http2              x86_64      1.15.19-2.el9      appstream      149 k
 mod_lua                x86_64      2.4.53-7.el9       appstream       62 k

Transaction Summary
============================================================================Install  12 Packages

Total download size: 2.0 M
Installed size: 6.0 M
Is this ok [y/N]: y
Downloading Packages:
(1/12): mailcap-2.1.49-5.el9.noarch.rpm                                                                                     384 kB/s |  32 kB     00:00
(2/12): rocky-logos-httpd-90.13-1.el9.noarch.rpm                                                                            271 kB/s |  24 kB     00:00
(3/12): mod_lua-2.4.53-7.el9.x86_64.rpm                                                                                     605 kB/s |  62 kB     00:00
(4/12): httpd-filesystem-2.4.53-7.el9.noarch.rpm                                                                            421 kB/s |  15 kB     00:00
(5/12): httpd-tools-2.4.53-7.el9.x86_64.rpm                                                                                 1.3 MB/s |  82 kB     00:00
(6/12): apr-util-openssl-1.6.1-20.el9.x86_64.rpm                                                                            551 kB/s |  15 kB     00:00
(7/12): apr-util-bdb-1.6.1-20.el9.x86_64.rpm                                                                                445 kB/s |  13 kB     00:00
(8/12): httpd-2.4.53-7.el9.x86_64.rpm                                                                                       514 kB/s |  48 kB     00:00
(9/12): apr-util-1.6.1-20.el9.x86_64.rpm                                                                                    1.1 MB/s |  94 kB     00:00
(10/12): mod_http2-1.15.19-2.el9.x86_64.rpm                                                                                 1.8 MB/s | 149 kB     00:00
(11/12): apr-1.7.0-11.el9.x86_64.rpm                                                                                        820 kB/s | 123 kB     00:00
(12/12): httpd-core-2.4.53-7.el9.x86_64.rpm                                                                                 2.5 MB/s | 1.4 MB     00:00
------------------------------------------------------------------------------------------------------------------------------------------------------------
Total                                                                                                                       1.6 MB/s | 2.0 MB     00:01
Running transaction check
Transaction check succeeded.
Running transaction test
Transaction test succeeded.
Running transaction
  Preparing        :                                                                                                                                    1/1
  Installing       : apr-1.7.0-11.el9.x86_64                                                                                                           1/12
  Installing       : apr-util-bdb-1.6.1-20.el9.x86_64                                                                                                  2/12
  Installing       : apr-util-1.6.1-20.el9.x86_64                                                                                                      3/12
  Installing       : apr-util-openssl-1.6.1-20.el9.x86_64                                                                                              4/12
  Installing       : httpd-tools-2.4.53-7.el9.x86_64                                                                                                   5/12
  Running scriptlet: httpd-filesystem-2.4.53-7.el9.noarch                                                                                              6/12
useradd warning: apache's uid 48 outside of the SYS_UID_MIN 201 and SYS_UID_MAX 999 range.

  Installing       : httpd-filesystem-2.4.53-7.el9.noarch                                                                                              6/12
  Installing       : rocky-logos-httpd-90.13-1.el9.noarch                                                                                              7/12
  Installing       : mailcap-2.1.49-5.el9.noarch                                                                                                       8/12
  Installing       : httpd-core-2.4.53-7.el9.x86_64                                                                                                    9/12
  Installing       : mod_lua-2.4.53-7.el9.x86_64                                                                                                      10/12
  Installing       : mod_http2-1.15.19-2.el9.x86_64                                                                                                   11/12
  Installing       : httpd-2.4.53-7.el9.x86_64                                                                                                        12/12
  Running scriptlet: httpd-2.4.53-7.el9.x86_64                                                                                                        12/12
  Verifying        : mailcap-2.1.49-5.el9.noarch                                                                                                       1/12
  Verifying        : rocky-logos-httpd-90.13-1.el9.noarch                                                                                              2/12
  Verifying        : mod_lua-2.4.53-7.el9.x86_64                                                                                                       3/12
  Verifying        : httpd-tools-2.4.53-7.el9.x86_64                                                                                                   4/12
  Verifying        : httpd-2.4.53-7.el9.x86_64                                                                                                         5/12
  Verifying        : httpd-filesystem-2.4.53-7.el9.noarch                                                                                              6/12
  Verifying        : apr-util-openssl-1.6.1-20.el9.x86_64                                                                                              7/12
  Verifying        : apr-util-bdb-1.6.1-20.el9.x86_64                                                                                                  8/12
  Verifying        : apr-util-1.6.1-20.el9.x86_64                                                                                                      9/12
  Verifying        : mod_http2-1.15.19-2.el9.x86_64                                                                                                   10/12
  Verifying        : apr-1.7.0-11.el9.x86_64                                                                                                          11/12
  Verifying        : httpd-core-2.4.53-7.el9.x86_64                                                                                                   12/12

Installed:
  apr-1.7.0-11.el9.x86_64          apr-util-1.6.1-20.el9.x86_64        apr-util-bdb-1.6.1-20.el9.x86_64          apr-util-openssl-1.6.1-20.el9.x86_64
  httpd-2.4.53-7.el9.x86_64        httpd-core-2.4.53-7.el9.x86_64      httpd-filesystem-2.4.53-7.el9.noarch      httpd-tools-2.4.53-7.el9.x86_64
  mailcap-2.1.49-5.el9.noarch      mod_http2-1.15.19-2.el9.x86_64      mod_lua-2.4.53-7.el9.x86_64               rocky-logos-httpd-90.13-1.el9.noarch

Complete!
 ```

🌞 **Démarrer le service Apache**

```
[user@localhost ~]$ sudo systemctl status httpd
● httpd.service - The Apache HTTP Server
     Loaded: loaded (/usr/lib/systemd/system/httpd.service; disabled; vendor preset: disabled)
     Active: active (running) since Tue 2023-01-03 16:51:06 CET; 6min ago
       Docs: man:httpd.service(8)
   Main PID: 11206 (httpd)
     Status: "Total requests: 0; Idle/Busy workers 100/0;Requests/sec: 0; Bytes served/sec:   0 B/sec"
      Tasks: 213 (limit: 11116)
     Memory: 29.2M
        CPU: 964ms
     CGroup: /system.slice/httpd.service
             ├─11206 /usr/sbin/httpd -DFOREGROUND
             ├─11207 /usr/sbin/httpd -DFOREGROUND
             ├─11208 /usr/sbin/httpd -DFOREGROUND
             ├─11209 /usr/sbin/httpd -DFOREGROUND
             └─11210 /usr/sbin/httpd -DFOREGROUND

Jan 03 16:51:06 localhost.localdomain systemd[1]: Starting The Apache HTTP Server...
Jan 03 16:51:06 localhost.localdomain httpd[11206]: AH00558: httpd: Could not reliably determine the server's fully qualified domain name, using localhost.>
Jan 03 16:51:06 localhost.localdomain httpd[11206]: Server configured, listening on: port 80
Jan 03 16:51:06 localhost.localdomain systemd[1]: Started The Apache HTTP Server.
```
  - faites en sorte qu'Apache démarre automatiquement au démarrage de la machine
  ```
  [user@localhost ~]$ sudo systemctl enable httpd
Created symlink /etc/systemd/system/multi-user.target.wants/httpd.service → /usr/lib/systemd/system/httpd.service.
  ```
  - ouvrez le port firewall nécessaire
  ```
  [user@localhost ~]$ sudo ss -laptn | grep httpd
LISTEN 0      511                *:80              *:*     users:(("httpd",pid=11210,fd=4),("httpd",pid=11209,fd=4),("httpd",pid=11208,fd=4),("httpd",pid=11206,fd=4))
  ```
🌞 **TEST**

- vérifier que le service est démarré
```
[user@localhost ~]$ sudo systemctl status httpd
● httpd.service - The Apache HTTP Server
     Loaded: loaded (/usr/lib/systemd/system/httpd.service; enabled; vendor preset: disabled)
     Active: active (running) since Tue 2023-01-03 16:51:06 CET; 31min ago
       Docs: man:httpd.service(8)
   Main PID: 11206 (httpd)
     Status: "Total requests: 0; Idle/Busy workers 100/0;Requests/sec: 0; Bytes served/sec:   0 B/sec"
      Tasks: 213 (limit: 11116)
     Memory: 29.2M
        CPU: 4.167s
     CGroup: /system.slice/httpd.service
             ├─11206 /usr/sbin/httpd -DFOREGROUND
             ├─11207 /usr/sbin/httpd -DFOREGROUND
             ├─11208 /usr/sbin/httpd -DFOREGROUND
             ├─11209 /usr/sbin/httpd -DFOREGROUND
             └─11210 /usr/sbin/httpd -DFOREGROUND

Jan 03 16:51:06 localhost.localdomain systemd[1]: Starting The Apache HTTP Server...
Jan 03 16:51:06 localhost.localdomain httpd[11206]: AH00558: httpd: Could not reliably determine the server's fully qualified domain name, using localhost.>
Jan 03 16:51:06 localhost.localdomain httpd[11206]: Server configured, listening on: port 80
Jan 03 16:51:06 localhost.localdomain systemd[1]: Started The Apache HTTP Server.
```
- vérifier qu'il est configuré pour démarrer automatiquement
```
[user@localhost ~]$ sudo systemctl is-enabled httpd
enabled
```
- vérifier avec une commande `curl localhost` que vous joignez votre serveur web localement
```
[user@localhost ~]$ curl localhost
<!doctype html>
<html>
  <head>
    <meta charset='utf-8'>
    <meta name='viewport' content='width=device-width, initial-scale=1'>
    <title>HTTP Server Test Page powered by: Rocky Linux</title>
    <style type="text/css">
      /*<![CDATA[*/

      html {
        height: 100%;
        width: 100%;
      }
        body {
  background: rgb(20,72,50);
  background: -moz-linear-gradient(180deg, rgba(23,43,70,1) 30%, rgba(0,0,0,1) 90%)  ;
  background: -webkit-linear-gradient(180deg, rgba(23,43,70,1) 30%, rgba(0,0,0,1) 90%) ;
  background: linear-gradient(180deg, rgba(23,43,70,1) 30%, rgba(0,0,0,1) 90%);
  background-repeat: no-repeat;
  background-attachment: fixed;
  filter: progid:DXImageTransform.Microsoft.gradient(startColorstr="#3c6eb4",endColorstr="#3c95b4",GradientType=1);
        color: white;
        font-size: 0.9em;
        font-weight: 400;
        font-family: 'Montserrat', sans-serif;
        margin: 0;
        padding: 10em 6em 10em 6em;
        box-sizing: border-box;

      }


  h1 {
    text-align: center;
    margin: 0;
    padding: 0.6em 2em 0.4em;
    color: #fff;
    font-weight: bold;
    font-family: 'Montserrat', sans-serif;
    font-size: 2em;
  }
  h1 strong {
    font-weight: bolder;
    font-family: 'Montserrat', sans-serif;
  }
  h2 {
    font-size: 1.5em;
    font-weight:bold;
  }

  .title {
    border: 1px solid black;
    font-weight: bold;
    position: relative;
    float: right;
    width: 150px;
    text-align: center;
    padding: 10px 0 10px 0;
    margin-top: 0;
  }

  .description {
    padding: 45px 10px 5px 10px;
    clear: right;
    padding: 15px;
  }

  .section {
    padding-left: 3%;
   margin-bottom: 10px;
  }

  img {

    padding: 2px;
    margin: 2px;
  }
  a:hover img {
    padding: 2px;
    margin: 2px;
  }

  :link {
    color: rgb(199, 252, 77);
    text-shadow:
  }
  :visited {
    color: rgb(122, 206, 255);
  }
  a:hover {
    color: rgb(16, 44, 122);
  }
  .row {
    width: 100%;
    padding: 0 10px 0 10px;
  }

  footer {
    padding-top: 6em;
    margin-bottom: 6em;
    text-align: center;
    font-size: xx-small;
    overflow:hidden;
    clear: both;
  }

  .summary {
    font-size: 140%;
    text-align: center;
  }

  #rocky-poweredby img {
    margin-left: -10px;
  }

  #logos img {
    vertical-align: top;
  }

  /* Desktop  View Options */

  @media (min-width: 768px)  {

    body {
      padding: 10em 20% !important;
    }

    .col-md-1, .col-md-2, .col-md-3, .col-md-4, .col-md-5, .col-md-6,
    .col-md-7, .col-md-8, .col-md-9, .col-md-10, .col-md-11, .col-md-12 {
      float: left;
    }

    .col-md-1 {
      width: 8.33%;
    }
    .col-md-2 {
      width: 16.66%;
    }
    .col-md-3 {
      width: 25%;
    }
    .col-md-4 {
      width: 33%;
    }
    .col-md-5 {
      width: 41.66%;
    }
    .col-md-6 {
      border-left:3px ;
      width: 50%;


    }
    .col-md-7 {
      width: 58.33%;
    }
    .col-md-8 {
      width: 66.66%;
    }
    .col-md-9 {
      width: 74.99%;
    }
    .col-md-10 {
      width: 83.33%;
    }
    .col-md-11 {
      width: 91.66%;
    }
    .col-md-12 {
      width: 100%;
    }
  }

  /* Mobile View Options */
  @media (max-width: 767px) {
    .col-sm-1, .col-sm-2, .col-sm-3, .col-sm-4, .col-sm-5, .col-sm-6,
    .col-sm-7, .col-sm-8, .col-sm-9, .col-sm-10, .col-sm-11, .col-sm-12 {
      float: left;
    }

    .col-sm-1 {
      width: 8.33%;
    }
    .col-sm-2 {
      width: 16.66%;
    }
    .col-sm-3 {
      width: 25%;
    }
    .col-sm-4 {
      width: 33%;
    }
    .col-sm-5 {
      width: 41.66%;
    }
    .col-sm-6 {
      width: 50%;
    }
    .col-sm-7 {
      width: 58.33%;
    }
    .col-sm-8 {
      width: 66.66%;
    }
    .col-sm-9 {
      width: 74.99%;
    }
    .col-sm-10 {
      width: 83.33%;
    }
    .col-sm-11 {
      width: 91.66%;
    }
    .col-sm-12 {
      width: 100%;
    }
    h1 {
      padding: 0 !important;
    }
  }


  </style>
  </head>
  <body>
    <h1>HTTP Server <strong>Test Page</strong></h1>

    <div class='row'>

      <div class='col-sm-12 col-md-6 col-md-6 '></div>
          <p class="summary">This page is used to test the proper operation of
            an HTTP server after it has been installed on a Rocky Linux system.
            If you can read this page, it means that the software is working
            correctly.</p>
      </div>

      <div class='col-sm-12 col-md-6 col-md-6 col-md-offset-12'>


        <div class='section'>
          <h2>Just visiting?</h2>

          <p>This website you are visiting is either experiencing problems or
          could be going through maintenance.</p>

          <p>If you would like the let the administrators of this website know
          that you've seen this page instead of the page you've expected, you
          should send them an email. In general, mail sent to the name
          "webmaster" and directed to the website's domain should reach the
          appropriate person.</p>

          <p>The most common email address to send to is:
          <strong>"webmaster@example.com"</strong></p>

          <h2>Note:</h2>
          <p>The Rocky Linux distribution is a stable and reproduceable platform
          based on the sources of Red Hat Enterprise Linux (RHEL). With this in
          mind, please understand that:

        <ul>
          <li>Neither the <strong>Rocky Linux Project</strong> nor the
          <strong>Rocky Enterprise Software Foundation</strong> have anything to
          do with this website or its content.</li>
          <li>The Rocky Linux Project nor the <strong>RESF</strong> have
          "hacked" this webserver: This test page is included with the
          distribution.</li>
        </ul>
        <p>For more information about Rocky Linux, please visit the
          <a href="https://rockylinux.org/"><strong>Rocky Linux
          website</strong></a>.
        </p>
        </div>
      </div>
      <div class='col-sm-12 col-md-6 col-md-6 col-md-offset-12'>
        <div class='section'>

          <h2>I am the admin, what do I do?</h2>

        <p>You may now add content to the webroot directory for your
        software.</p>

        <p><strong>For systems using the
        <a href="https://httpd.apache.org/">Apache Webserver</strong></a>:
        You can add content to the directory <code>/var/www/html/</code>.
        Until you do so, people visiting your website will see this page. If
        you would like this page to not be shown, follow the instructions in:
        <code>/etc/httpd/conf.d/welcome.conf</code>.</p>

        <p><strong>For systems using
        <a href="https://nginx.org">Nginx</strong></a>:
        You can add your content in a location of your
        choice and edit the <code>root</code> configuration directive
        in <code>/etc/nginx/nginx.conf</code>.</p>

        <div id="logos">
          <a href="https://rockylinux.org/" id="rocky-poweredby"><img src="icons/poweredby.png" alt="[ Powered by Rocky Linux ]" /></a> <!-- Rocky -->
          <img src="poweredby.png" /> <!-- webserver -->
        </div>
      </div>
      </div>

      <footer class="col-sm-12">
      <a href="https://apache.org">Apache&trade;</a> is a registered trademark of <a href="https://apache.org">the Apache Software Foundation</a> in the United States and/or other countries.<br />
      <a href="https://nginx.org">NGINX&trade;</a> is a registered trademark of <a href="https://">F5 Networks, Inc.</a>.
      </footer>

  </body>
</html>
```
## 2. Avancer vers la maîtrise du service

🌞 **Le service Apache...**

- affichez le contenu du fichier `httpd.service` qui contient la définition du service Apache
```
[user@localhost conf]$ cat httpd.conf

ServerRoot "/etc/httpd"

Listen 80

Include conf.modules.d/*.conf

User apache
Group apache


ServerAdmin root@localhost


<Directory />
    AllowOverride none
    Require all denied
</Directory>


DocumentRoot "/var/www/html"

<Directory "/var/www">
    AllowOverride None
    Require all granted
</Directory>

<Directory "/var/www/html">
    Options Indexes FollowSymLinks

    AllowOverride None

    Require all granted
</Directory>

<IfModule dir_module>
    DirectoryIndex index.html
</IfModule>

<Files ".ht*">
    Require all denied
</Files>

ErrorLog "logs/error_log"

LogLevel warn

<IfModule log_config_module>
    LogFormat "%h %l %u %t \"%r\" %>s %b \"%{Referer}i\" \"%{User-Agent}i\"" combined
    LogFormat "%h %l %u %t \"%r\" %>s %b" common

    <IfModule logio_module>
      LogFormat "%h %l %u %t \"%r\" %>s %b \"%{Referer}i\" \"%{User-Agent}i\" %I %O" combinedio
    </IfModule>


    CustomLog "logs/access_log" combined
</IfModule>

<IfModule alias_module>


    ScriptAlias /cgi-bin/ "/var/www/cgi-bin/"

</IfModule>

<Directory "/var/www/cgi-bin">
    AllowOverride None
    Options None
    Require all granted
</Directory>

<IfModule mime_module>
    TypesConfig /etc/mime.types

    AddType application/x-compress .Z
    AddType application/x-gzip .gz .tgz



    AddType text/html .shtml
    AddOutputFilter INCLUDES .shtml
</IfModule>

AddDefaultCharset UTF-8

<IfModule mime_magic_module>
    MIMEMagicFile conf/magic
</IfModule>


EnableSendfile on

IncludeOptional conf.d/*.conf
```

🌞 **Déterminer sous quel utilisateur tourne le processus Apache**

- mettez en évidence la ligne dans le fichier de conf principal d'Apache (`httpd.conf`) qui définit quel user est utilisé
```
[user@localhost conf]$ cat httpd.conf | grep -i "user" | head -n 1
User apache
```
- utilisez la commande `ps -ef` pour visualiser les processus en cours d'exécution et confirmer que apache tourne bien sous l'utilisateur mentionné dans le fichier de conf
```
[user@localhost conf]$ ps -ef | grep apache
apache       761     728  0 09:33 ?        00:00:00 /usr/sbin/httpd -DFOREGROUND
apache       763     728  0 09:33 ?        00:00:07 /usr/sbin/httpd -DFOREGROUND
apache       764     728  0 09:33 ?        00:00:07 /usr/sbin/httpd -DFOREGROUND
apache       765     728  0 09:33 ?        00:00:07 /usr/sbin/httpd -DFOREGROUND
user        1562    1412  0 11:25 pts/0    00:00:00 grep --color=auto apache
```
- la page d'accueil d'Apache se trouve dans `/usr/share/testpage/`
  - vérifiez avec un `ls -al` que tout son contenu est **accessible en lecture** à l'utilisateur mentionné dans le fichier de conf
```
 [user@localhost testpage]$ ls -al
 total 12
drwxr-xr-x.  2 root root   24 Jan  3 16:17 .
drwxr-xr-x. 82 root root 4096 Jan  3 16:17 ..
-rw-r--r--.  1 root root 7620 Jul 27 20:05 index.html
```

🌞 **Changer l'utilisateur utilisé par Apache**

- créez un nouvel utilisateur

```
[user@localhost ~]$ sudo adduser user2 -d /usr/share/httpd -s /sbin/nologin
[sudo] password for user:
adduser: warning: the home directory /usr/share/httpd already exists.
adduser: Not copying any file from skel directory into it.
[user@localhost ~]$ cat /etc/passwd | grep user2
user2:x:1001:1001::/home/user2:/bin/bash
```
```
[user@localhost conf]$ cat httpd.conf | grep user1
User user1
[user@localhost ~]$ ps -ef | grep httpd
root         729       1  0 09:55 ?        00:00:00 /usr/sbin/httpd -DFOREGROUND
user1        758     729  0 09:55 ?        00:00:00 /usr/sbin/httpd -DFOREGROUND
user1        759     729  0 09:55 ?        00:00:00 /usr/sbin/httpd -DFOREGROUND
user1        760     729  0 09:55 ?        00:00:00 /usr/sbin/httpd -DFOREGROUND
user1        761     729  0 09:55 ?        00:00:00 /usr/sbin/httpd -DFOREGROUND
user        1465    1447  0 09:57 pts/0    00:00:00 grep --color=auto httpd
```
🌞 **Faites en sorte que Apache tourne sur un autre port**

- modifiez la configuration d'Apache pour lui demander d'écouter sur un autre port de votre choix
  - montrez la ligne de conf dans le compte rendu, avec un `grep` pour ne montrer que la ligne importante
```
[user@localhost conf]$ cat httpd.conf | grep -i listen
Listen 222
```
- ouvrez ce nouveau port dans le firewall, et fermez l'ancien
```
[user@localhost conf]$ sudo firewall-cmd --add-port=222/tcp --permanent
success
[user@localhost conf]$ sudo firewall-cmd --remove-port=80/tcp --permanent
success
```
- redémarrez Apache
- prouvez avec une commande `ss` que Apache tourne bien sur le nouveau port choisi
```
[user@localhost ~]$ sudo ss -alntp | grep httpd
[sudo] password for user:
LISTEN 0      511                *:222             *:*    users:(("httpd",pid=749,fd=4),("httpd",pid=748,fd=4),("httpd",pid=746,fd=4),("httpd",pid=729,fd=4))
```
- vérifiez avec `curl` en local que vous pouvez joindre Apache sur le nouveau port
```
[user@localhost ~]$ curl localhost:222 | head -5
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
  0     0    0     0    0     0      0      0 --:--:-- --:--:-- --:--:--     0<!doctype html>
<html>
  <head>
    <meta charset='utf-8'>
    <meta name='viewport' content='width=device-width, initial-scale=1'>
100  7620  100  7620    0     0  3720k      0 --:--:-- --:--:-- --:--:-- 7441k
curl: (23) Failed writing body
```
# Partie 2 : Mise en place et maîtrise du serveur de base de données
| Machines        | IP            | Service                 |
|-----------------|---------------|-------------------------|
| `web.tp5.linux` | `10.105.1.11` | Serveur Web             |
| `db.tp5.linux`  | `10.105.1.12` | Serveur Base de Données |

🌞 **Install de MariaDB sur `db.tp5.linux`**
```
[user@localhost ~]$ sudo dnf install mariadb-server
[sudo] password for user:
[...]
Complete!
```

🌞 **Port utilisé par MariaDB**

```
[user@localhost ~]$ sudo systemctl enable mariadb
Created symlink /etc/systemd/system/mysql.service → /usr/lib/systemd/system/mariadb.service.
Created symlink /etc/systemd/system/mysqld.service → /usr/lib/systemd/system/mariadb.service.
Created symlink /etc/systemd/system/multi-user.target.wants/mariadb.service → /usr/lib/systemd/system/mariadb.service.
```
```
[user@localhost ~]$ sudo mysql_secure_installation
```
```
[user@localhost ~]$ sudo ss -alptn |grep mariadb
LISTEN 0      80                 *:3306            *:*    users:(("mariadbd",pid=4483,fd=19))
```
🌞 **Processus liés à MariaDB**

```
[user@localhost ~]$ ps -ef | grep mariadb
mysql       4483       1  7 10:51 ?        00:00:16 /usr/libexec/mariadbd --basedir=/usr
user        4582    1228  0 10:55 pts/0    00:00:00 grep --color=auto mariadb
```
# Partie 3 : Configuration et mise en place de NextCloud
## 1. Base de données
🌞 **Préparation de la base pour NextCloud**

- une fois en place, il va falloir préparer une base de données pour NextCloud :
  - connectez-vous à la base de données à l'aide de la commande `sudo mysql -u root -p`
  - exécutez les commandes SQL suivantes :
```
MariaDB [(none)]> CREATE USER 'nextcloud'@'10.105.1.11' IDENTIFIED BY 'pewpewpew';
Query OK, 0 rows affected (0.003 sec)

MariaDB [(none)]> CREATE DATABASE IF NOT EXISTS nextcloud CHARACTER SET utf8mb4 COLLATE utf8mb4_general_ci;
Query OK, 1 row affected (0.000 sec)

MariaDB [(none)]> GRANT ALL PRIVILEGES ON nextcloud.* TO 'nextcloud'@'10.105.1.11';
Query OK, 0 rows affected (0.002 sec)

MariaDB [(none)]> FLUSH PRIVILEGES;
Query OK, 0 rows affected (0.000 sec)
```

🌞 Exploration de la base de données
```
[user@localhost~]$ mysql -u nextcloud -h 10.105.1.12 -p
Enter password:
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 23
```
```
[user@localhost ~]$ sudo dnf install mysql-8.0.30-3.el9_0.x86_64
```
```
mysql> SHOW DATABASES;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| nextcloud          |
+--------------------+
2 rows in set (0.00 sec)
```
🌞 Trouver une commande SQL qui permet de lister tous les utilisateurs de la base de données
```
mysql> SHOW DATABASES;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| nextcloud          |
+--------------------+
2 rows in set (0.00 sec)


2. Serveur Web et NextCloud

🌞 Install de PHP

```
[user@localhost conf]$ sudo dnf config-manager --set-enabled crb

```
[user@localhost conf]$ sudo dnf install dnf-utils http://rpms.remirepo.net/enterprise/remi-release-9.rpm -y`

```
```
[user@localhost conf]$ dnf module list php
```
```
[user@localhost conf]$ sudo dnf module enable php:remi-8.1 -y
```
```
[user@localhost conf]$ sudo dnf install -y php81-php
```




🌞 Install de tous les modules PHP nécessaires pour NextCloud
```
[user@localhsot conf]$ sudo dnf install -y libxml2 openssl php81-php php81-php-ctype php81-php-curl php81-php-gd php81-php-iconv php81-php-json php81-php-libxml php81-php-mbstring php81-php-openssl php81-php-posix php81-php-session php81-php-xml php81-php-zip php81-php-zlib php81-php-pdo php81-php-mysqlnd php81-php-intl php81-php-bcmath php81-php-gmp
```



🌞 Récupérer NextCloud
```
[user@localhost ~]$ sudo curl https://download.nextcloud.com/server/prereleases/nextcloud-25.0.0rc3.zip -O
[sudo] password for user:
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
  7  168M    7 13.2M    0     0   708k      0  0:04:03  0:00:19  0:03:44  455k`
```
```
[user@localhost ~]$ ls /var/www/tp5_nextcloud/
3rdparty  config       core      index.html  occ           ocs-provider  resources   themes
apps      console.php  cron.php  index.php   ocm-provider  public.php    robots.txt  updater
AUTHORS   COPYING      dist      lib         ocs           remote.php    status.php  version.php
```
```
[user@localhost ~]$ sudo chown apache:apache /var/www/tp5_nextcloud/ -R
```
🌞 Adapter la configuration d'Apache
```
[user@localhost conf]$ sudo cat httpd.conf | tail -n 18
IncludeOptional conf.d/*.conf

<VirtualHost *:80>
  # on indique le chemin de notre webroot
  DocumentRoot /var/www/tp5_nextcloud/
  # on précise le nom que saisissent les clients pour accéder au service
  ServerName  web.tp5.linux

  # on définit des règles d'accès sur notre webroot
  <Directory /var/www/tp5_nextcloud/>
    Require all granted
    AllowOverride All
    Options FollowSymLinks MultiViews
    <IfModule mod_dav.c>
      Dav off
    </IfModule>
  </Directory>
</VirtualHost>
```

🌞 Redémarrer le service Apache pour qu'il prenne en compte le nouveau fichier de conf
```
[user@localhost conf]$ sudo systemctl restart httpd
```
3. Finaliser l'installation de NextCloud

🌞 Exploration de la base de données`
```
mysql> SELECT Count(*) FROM INFORMATION_SCHEMA.TABLES WHERE TABLE_TYPE = 'BASE TABLE';
+----------+
| Count(*) |
+----------+
|       95 |
+----------+
1 row in set (0.00 sec)
```
