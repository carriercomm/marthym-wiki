Normalement ici gollum est installé, reste plus qu'a le faire démarrer en même temps que la machine. Sur Debian c'est 
systemd le nouveau gestionnaire de service donc voici un script systemd à placer dans :
`/usr/lib/systemd/system/gollum.service`

~~~
[Unit]
Description=Gollum server
After=syslog.target
After=network.target

[Service]
User=fcombes
Environment="WIKI_DIR=/home/fcombes/docker-home/marthym-wiki"
ExecStartPre=cd ${WIKI_DIR} && git pull
ExecStart=/usr/local/bin/gollum --no-edit --gollum-path ${WIKI_DIR}
TimeoutSec=10

[Install]
WantedBy=multi-user.target
~~~

On note le `ExecStartPre` qui va permettre de synchroniser le wiki au démarrage. Après on peut aussi mettre en place un
chron pour l'actualiser régulièrement mais dans le cas d'un wiki perso c'est pas forcément judicieux.

On lance gollum avec `--no-edit` pour éviter que les personnes sur le même réseau ne modifient le wiki.

<!-- --- tags: tools, gollum -->