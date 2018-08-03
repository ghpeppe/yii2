Installare Yii
==============

Puoi installare Yii in due modi, usando [Composer](https://getcomposer.org/) o scaricando un archivio.
Il metodo preferito è il primo, perché ti consente di installare [estensioni](structure-extensions.md) o aggiornare il core di Yii 
semplicemente eseguendo un comando.

Le installazioni standard di Yii comportano il download e l'installazione sia del framework che di un modello di progetto. Un modello di progetto è un progetto Yii funzionante che implementa alcune funzionalità di base, come login, modulo di contatto, ecc. Il suo codice è organizzato come raccomandato. Pertanto, può essere un buon punto di partenza per i tuoi progetti.

In questa e nelle prossime sezioni, descriveremo come installare Yii con il cosiddetto modello di progetto di base e come implementare nuove funzionalità sopra a questo modello. Yii fornisce anche un altro modello chiamato [modello di progetto avanzato](https://www.yiiframework.com/extension/yiisoft/yii2-app-advanced/doc/guide) da utilizzare preferibilmente in un ambiente di sviluppodi squadra per realizzare applicazioni a più livelli.

> Info: il modello di progetto di base è adatto per lo sviluppo del 90 percento delle applicazioni Web. Si differenzia dal modello di progetto avanzato principalmente per come è organizzato il codice. Se sei nuovo di Yii, ti consigliamo vivamente di attenersi al modello di progetto di base per le sue funzionalità semplici ma sufficienti.


Installazione tramite Composer <span id="installing-via-composer"></span>
--------------------------

### Installazione di Composer

Se non hai già installato Composer puoi farlo seguendo le istruzioni al sito [getcomposer.org](https://getcomposer.org/download/). Su Linux e Mac OS X puoi installare Composer con questo comando:

    curl -sS https://getcomposer.org/installer | php
    mv composer.phar /usr/local/bin/composer

Su Windows devi scaricare ed eseguire [Composer-Setup.exe](https://getcomposer.org/Composer-Setup.exe).

Fai riferimento alla [documentazione di Composer](https://getcomposer.org/doc/articles/troubleshooting.md) per qualsiasi problema. Se sei un nuovo utente di Composer, ti consigliamo inoltre di leggere almeno la [Guida di base](https://getcomposer.org/doc/01-basic-usage.md) della documentazione.

In questa guida tutti i comandi presuppongono che composer sia stato installato [a livello globale](https://getcomposer.org/doc/00-intro.md#globally) in modo che sia disponibile come comando `composer`. Se invece stai utilizzando `composer.phar` nella directory locale, è necessario aggiustare i comandi di esempio di conseguenza.

Se hai già Composer installato assicurati di avere una versione aggiornata. Puoi aggiornare Composer con il comando
`composer self-update`.

> Nota: durante l'installazione di Yii, Composer dovrà richiedere molte informazioni dall'API Github. Il numero di richieste dipende dal numero di dipendenze della tua applicazione e potrebbe essere maggiore del limite stabilito dell'API Github. Se raggiungi questo limite, Composer potrebbe chiedere le tue credenziali di accesso a Github per ottenere un token di accesso. Nelle connessioni veloci è possibile che questo limite venga superato prima che Composer sia in grado di gestirlo quindi è consigliabile configurare il token di accesso prima di installare Yii. Si prega di fare riferimento alla [documentazione di Composer sui token Github API](https://getcomposer.org/doc/articles/troubleshooting.md#api-rate-limit-and-oauth-tokens) per le istruzioni su come farlo.

### Installazione di Yii <span id="installing-from-composer"></span>

Una volta installato Composer, puoi installare Yii eseguendo questo comando in una directory accessbile via web:

    composer global require "fxp/composer-asset-plugin:^1.4.1"
    composer create-project --prefer-dist yiisoft/yii2-app-basic basic

Il primo comando installa il [plugin composer asset](https://github.com/francoispluchino/composer-asset-plugin/)
che consente di gestire le dipendenze di bower e npm tramite Composer. Devi eseguire questo comando solo una volta. Il secondo 
installa Yii in una directory di nome `basic`. Puoi scegliere un nome diverso, se preferisci.

> Nota: durante l'installazione potrebbe essere che Composer ti chieda le credenziali di Github, per superato limite di utilizzo
> delle API di Github. Questa situazione è normale perché Composer deve scaricare molte informazioni per tutti i pacchetti da Github.
> Accedendo a Github aumenterà il limite di utilizzo delle API, consentendo a Composer di completare il suo lavoro. Per maggiori 
> dettagli fai riferimento alla 
> [documentazione di Composer](https://getcomposer.org/doc/articles/troubleshooting.md#api-rate-limit-and-oauth-tokens).

> Suggerimento: se vuoi installare l'ultima versione di sviluppo di Yii, puoi usare questo comando che aggiunge una 
> [opzione di stabilità](https://getcomposer.org/doc/04-schema.md#minimum-stability):
>
>     composer create-project --prefer-dist --stability=dev yiisoft/yii2-app-basic basic
>
> Considera che la versione di sviluppo di Yii non dovrebbe essere utilizzata per siti di produzione perché potrebbe rendere instabile
> il tuo codice.


Installazione da un archivio <span id="installing-from-archive-file"></span>
----------------------------

L'installazione da un archivio compresso comporta tre passaggi:

1. Scaricare l'archivio da [yiiframework.com](http://www.yiiframework.com/download/).
2. Scompattare l'archivio in una directory accessible via web.
3. Modificare il file `config/web.php` inserendo una chiave segreta per il parametro di configurazione `cookieValidationKey` 
   (questa operazione viene fatta automaticamente se installi tramite Composer):

   ```php
   // !!! insert a secret key in the following (if it is empty) - this is required by cookie validation
   'cookieValidationKey' => 'enter your secret key here',
   ```


Altre modalità di installazione <span id="other-installation-options"></span>
-------------------------------

Le istruzioni sopra elencate mostrano come installare Yii, e creano inoltre un'applicazione web base funzionante.
Questo approccio è un ottimo punto di partenza per progetti minori, o se stai imparando Yii.

Ma ci sono altre opzioni disponibili per l'installazione:

* se vuoi installare solo il core e costruire l'applocazione da zero puoi seguire le istruzioni della sezione
  [costruire un'applicazione da zero](tutorial-start-from-scratch.md).
* se vuoi avviare un'applicazione più sofisticata, che meglio si sposa per uno sviluppo di gruppo, puoi considerare l'insallazione del
  [template di applicazione avanzata](tutorial-advanced-app.md).


Verifica dell'installazione <span id="verifying-installation"></span>
---------------------------

Dopo l'installazione puoi usare il tuo browser per accedere all'applicazione Yii installata con l'URL seguente:

```
http://localhost/basic/web/index.php
```

Questo indirizzo assume che hai installato Yii in una directory di nome `basic`, direttamente nella *root* del tuo webserver,
e che il webserver è in esecuzione sulla tua macchina locale (`localhost`). Potresti doverlo modificare a seconda del tuo ambiente
di installazione.

![Installazione di Yii completata con successo](images/start-app-installed.png)

Dovresti vedere la pagina sopra di congratulazioni. In caso contrario verifica se la tua installazione di PHP soddisfa i requisiti minimi
di Yii. Puoi verificare le richieste in due modi:

* accedere all'indirizzo `http://localhost/basic/requirements.php` tramite browser;
* lanciando questi comandi:

  ```
  cd basic
  php requirements.php
  ```

Devi configurare la tua installazione di PHP in modo che soddisfi le richieste minime di Yii. E' molto importante che tu stia usando 
PHP 5.4 o successivo. Devi inoltre installare le [estensioni PDO di PHP](http://www.php.net/manual/en/pdo.installation.php) e un driver
di database di PDO (come ad esempio `pdo_mysql` per i database MySQL), se la tua applicazione richiede un database.


Configurazione del webserver <span id="configuring-web-servers"></span>
----------------------------

> Informazione: puoi saltare questa parte per ora se stai solo provando Yii e non hai intenzione di installarlo su un server di produzione.

L'applicazione installata secondo le istruzioni sopra dovrebbe funzionare senza problemi su un server 
[Apache](http://httpd.apache.org/) o [Nginx](http://nginx.org/), su Windows, Mac OS X, or Linux equipaggiati con PHP 5.4 o successivo. 
Yii 2.0 è anche compatibile con le librerie [HHVM](http://hhvm.com/) di Facebook, tuttavia ci sono alcuni casi limite dove HHVM si
comporta diversamente dal PHP nativo, quindi devi avere maggiore cura se intendi usare HHVM.

Su un server di produzione vorrai probabilmente che la tua applicazione sia accessibile tramite l'url 
`http://www.example.com/index.php` invece di `http://www.example.com/basic/web/index.php`. Questo risultato richiede che punti la
*document root* del tuo webserver nella directory `basic/web`. Vorrai magari anche nascondere `index.php` dall'URL, come descritto
nella sezione [analizzare e generare URL](runtime-url-handling.md).
In questa parte vedrai configurare il tuo server Apache o Nginx per ottenere questo risultato.

> Informazione: impostando `basic/web` come *document root* impedisci agli utenti finali di accedere al codice e a file/informazioni
riservate memorizzate nelle directory superiori a `basic/web`. Negare l'accesso a queste altre cartelle è sicuramente un vantaggio
per la sicurezza.

> Informazione: se la tua applicazione andrà installata su un servizio di hosting condiviso non avrai il permesso di modificare la
configurazione del webserver, ma dovrai comunque correggere la struttura della tua applicazione per migliorare la sicurezza. Fai 
riferimento alla sezione [ambienti di hosting condiviso](tutorial-shared-hosting.md) per maggiori dettagli.


### Configurazione consigliata di Apache <span id="recommended-apache-configuration"></span>

Usa questa configurazione nel file `httpd.conf` di Apache o nella definizione del tuo *VirtualHost*. Tieni presente che dovrai
modificare `path/to/basic/web` con il percorso reale della tua `basic/web`.

```
# Imposta *DocumentRoot* per essere "basic/web"
DocumentRoot "path/to/basic/web"

<Directory "path/to/basic/web">
    # usa mod_rewrite per gli url SEF
    RewriteEngine on
    # If a directory or a file exists, use the request directly
    RewriteCond %{REQUEST_FILENAME} !-f
    RewriteCond %{REQUEST_FILENAME} !-d
    # Otherwise forward the request to index.php
    RewriteRule . index.php

    # ...altre impostazioni...
</Directory>
```


### Configurazione consigliata di Nginx <span id="recommended-nginx-configuration"></span>

Devi aver installato PHP con il demone [FPM](http://php.net/install.fpm) per usare [Nginx](http://wiki.nginx.org/).
Usa questa configurazione per Nginx, sostituendo `path/to/basic/web` con il percorso reale di `basic/web` e `mysite.test` con
il nome reale del server web.

```
server {
    charset utf-8;
    client_max_body_size 128M;

    listen 80; ## listen for ipv4
    #listen [::]:80 default_server ipv6only=on; ## listen for ipv6

    server_name mysite.test;
    root        /path/to/basic/web;
    index       index.php;

    access_log  /path/to/basic/log/access.log main;
    error_log   /path/to/basic/log/error.log;

    location / {
        # Redirect everything that isn't a real file to index.php
        try_files $uri $uri/ /index.php?$args;
    }

    # uncomment to avoid processing of calls to non-existing static files by Yii
    #location ~ \.(js|css|png|jpg|gif|swf|ico|pdf|mov|fla|zip|rar)$ {
    #    try_files $uri =404;
    #}
    #error_page 404 /404.html;

    location ~ \.php$ {
        include fastcgi.conf;
        fastcgi_pass   127.0.0.1:9000;
        #fastcgi_pass unix:/var/run/php5-fpm.sock;
        try_files $uri =404;
    }

    location ~ /\.(ht|svn|git) {
        deny all;
    }
}
```

Usando questa configurazione dovresti anche impostare `cgi.fix_pathinfo=0` in `php.ini` per evitare molte chiamate di sistema `stat()` 
inutili.

Inoltre considera che nel caso di server HTTPS dovrai aggiungere `fastcgi_param HTTPS on;` così che Yii possa correttamente rilevare
se la connessione è sicura.
