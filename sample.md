### Commandes pour lancer son projet sur le serveur :

**Se connecter sur ovh :**
		
- Sur Linux :

		Se connecter au serveur sas tout en récupérerant votre clé ssh :
			ssh VotreIdentifiantCentrale@sas1.ec-m.fr -A
			
		Quitter le serveur sas :
			exit
			
		Se connecter sur le serveur ovh :
			ssh VotrePlante@ovh1.ec-m.fr

- Sur Windows (PowerShell) :

        ssh VotrePlante@ovh1.ec-m.fr
			
**Créer un nouveau dossier pour le projet :**

	    mkdir nom_du_projet
			
**Entrer dans le dossier nom_du_projet :**

		cd nom_du_projet
			
**Récupérer le projet depuis GitHub et le mettre dans le dossier :**

		- Aller sur la page GitHub du projet (le repository)
		- Cliquez sur Code (en vert)
		- Copier le lien disponible dans Clone -> SSH (Il suffit de cliquer sur
		le petit bouton à droite du lien pour le mettre dans votre presse-papier.)
			
		Récupérez les fichiers :
		    git clone VotreLienSSH
		
**Créer le dossier node**

        Regarder s'il y a un dossier "node" :
            cd /
            ls
        
        Si c'est le cas, le supprimer :
            rm -rf node
            
        Créer un dossier node qui est lié au projet :
            ln -s nom_du_projet/nom_du_repository node
    

**Installer les modules node.js :**

- Dans le dossier node :
	    cd node
	    npm install

- et dans le dossier node/static :
	    cd node/static
	    npm install

**Récupérer votre port Node.js :**
    
    	cd /
    	cat readme.txt
    	- Le port s'affiche à côté de "Node"

**Ecrire le code du port dans le fichier node.js du serveur :**

- Avec nano :	
		nano node/server.js
		
- Avec vim :

		vim node/server.js
		:m! (pour sauvegarder)
		:q! (pour quitter)

**Lancer votre projet sur le serveur :**

    	node node/server.js
	
Votre page web est maintenant accesible à l'adresse :

    	http://VotrePlante.ovh1.ec-m.fr

Mais alors votre serveur node s'arrêtera quand vous quitterez ovh et la page ne sera plus sur le web.

 - Vous pouvez arrêter node :
    
        Pour gérer les processus :
            top
        chercher vore processus "node" et tuez-le

* Ou alors, quittez votre ovh :
    
        exit

    Constatez que votre page web n'est plus accessible sur internet à l'adresse :
    
        http://VotrePlante.ovh1.ec-m.fr

    Reconnectez-vous sur ovh :
    
        ssh -A VotrePlante@ovh1.ec-m.fr
    
    Vous pouvez vérifier que node n'est plus dans les proccesus avec :

        top

    Car le processus s'est arrêté quand vous aviez quitté votre ovh.

**Lancer votre projet sur le serveur sans qu'il s'arrête quand vous quitter le serveur :**

- Solution 1, avec screen :
		screen -d -m -S node node node/server.js
- Solution 2, lancer le processus en arrière-plan :
		node node/server.js &

Vous pouvez maintenant quitter votre ovh :

    	exit

Et vous pouvez constater que maintenant votre projet est toujours accessible sur le web à l'adresse :

        http://VotrePlante.ovh1.ec-m.fr

### Pour gérer les screens :

Pour afficher tous les screens existants, sur toutes les sessions :

    	VotrePlante@ovh1 ~/node (git)-[master] % ps aux

Pour afficher les screens existants, uniquement sur votre session :

    	VotrePlante@ovh1 ~/node (git)-[master] % ps

Pour afficher uniquement les screens de sa propre session :

	    VotrePlante@ovh1 ~/node (git)-[master] % ps aux | grep VotrePlante

Pour tuer le screen 3031408 (gentiment) :

    	    VotrePlante@ovh1 ~/node (git)-[master] % kill 3031408
      ou :  VotrePlante@ovh1 ~/node (git)-[master] % kill -13 3031408

Pour tuer le screen 3031408 (méchamment) :
    
	    VotrePlante@ovh1 ~/node (git)-[master] % kill -9 3031408

Sinon, vous pouvez aussi utiliser un outil plus convivial pour faire ces opérations :

	    top
	
	
