# kerberos
 tp kerberos
 j'ai fait aussi quelques captures d'ecrans de la fin
 pour me faciliter la tache j'ai uploadé une fois les captures d'ecran de la partie client au lieu de pusher encore tout les fichiers.
 merci pour votre bonne comprehension
 
'Client machine ip address is 192.168.1.24
'Service server machine ip address is 192.168.1.28
'KDC machine ip address is 192.168.1.27
![Capture d’écran (123)](https://user-images.githubusercontent.com/108520553/235944662-e734444b-0479-49a8-a215-17e2fab854d4.png)

Normalement on doit installer les packages necessaire pour kerberos avec les commandes ci-dessous mais chez moi j'avais déjà installer:
  $ sudo apt-get update
  $ sudo apt-get install krb5-kdc krb5-admin-server krb5-config
![Capture d’écran (124)](https://user-images.githubusercontent.com/108520553/235944755-9dda5b11-03ac-45bd-9536-93bbbef56120.png)

On a installer les packages pour le serveur machine avec les commandes ci-dessous:
$ sudo apt-get update
$ sudo apt-get install krb5-user libpam-krb5 libpam-ccreds
![Capture d’écran (125)](https://user-images.githubusercontent.com/108520553/235944846-2c3bc708-7b78-44c7-b684-ce40fce53617.png)
![Capture d’écran (126)](https://user-images.githubusercontent.com/108520553/235944880-9ef60f93-599d-4c22-ad95-baaa8d2bf2ad.png)

![Capture d’écran (127)](https://user-images.githubusercontent.com/108520553/235944906-1a0d04f2-bbe3-44af-9515-bb54a08a73ca.png)

Pour générer le keytab file on tape:
 $ ktutil 
   ktutil:  add_entry -password -p oracle/mn.insat.tn@INSAT.TN -k 1 -e aes256-cts-hmac-sha1-96
   Password for oracle/mn.insat.tn@INSAT.TN: 
   ktutil:  wkt oracle.keytab
![Capture d’écran (128)](https://user-images.githubusercontent.com/108520553/235944928-5f92fa66-7730-465c-820f-5b82b421ee39.png)

![Capture d’écran (129)](https://user-images.githubusercontent.com/108520553/235944953-597d7560-3340-4dc7-a4e7-dc9c6db1e426.png)

![Capture d’écran (130)](https://user-images.githubusercontent.com/108520553/235944987-f0b8597f-72bf-4b52-8678-47acfc7be514.png)

![Capture d’écran (131)](https://user-images.githubusercontent.com/108520553/235945033-404fca11-3096-46cd-9d6d-6ed31814bb76.png)

Après l'installation de oracle 
1-crée un utilisateur qui a le même nom qu'on a donné depuis le début
2-specifier le chemin de votre fichier oracle.keytab dans le fichier de configuration de oracle:
 #krb_server_keyfile = '/home/postgres/pgsql/data/postgres.keytab'
3-authentifier l'utilisateur que vous avez créer:
 $psql -d yosra -h mn.insat.tn -U ablo
4-faire le : $kinit de votre user(ablo)
