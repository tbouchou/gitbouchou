# Installer et exécuter une application JEE

## Plan d'execution :

1. *Telechargements* :
  * XAMPP : pour les modules tomcat, apache et mySql en locale 
  * Netbeans
    
2. *Etapes (configuration)*

4. *En cas de complications*

5. *Manuel utilisateur de notre application*

3. *Conclusion* 

### Telechargements

Pour telecharger XAMPP, c'est très simple, il vous suffit de cliquer sur ce lien : [XAMPP dernière version](https://www.apachefriends.org/fr/index.html)

Pour Netbeans, voici le lien : [Netbeans dernière version](https://netbeans.apache.org/download/)

### Etapes

La configuration est une étape essentiel pour la future construction de projets, il s'agit donc très attentif.

Pour **XAMPP**, ouvrir le control pannel et effectuer les commandes suivantes :

    Tomcat : Config -> tomcat-users.xml
    
Ajouter les 3 lignes suivantes dans la balise *tomcat-users*
 
    <role rolename="manager-gui"/>
    <user username="tomcat" password="tomcat" roles="manager-gui"/>
    <user username="tomcat" password="tomcat" roles="standard,manager-script" />
 
Modifier aussi les password présents dans la page en les remplacant par *tomcat*   

Ces ajouts permetteront la connexion locale au serveur et manager/html de tomcat au travers du port 8080.

Puis lancer les services suivants : Apache, MySQL (si vous comptez utiliser phpmyadmin)

La partie XAMPP s'arrête là, préparez-vous cependant pour la partie **Netbeans**

Il vous faut d'abord le jdk (pour permettre l'exéuction java), voici son lien téléchargeable [Last Version](https://www.oracle.com/java/technologies/javase-jdk13-downloads.html). Puis il faudra modifier la variable *Path* d'environnement

     Panneau de Configuration -> Système
     Paramètres systèmes avancés -> Variables d'environnement
     Variables système -> Selectionner Path -> Modifier
     Ajouter l'arborescence du jdk (ex : C:\Program Files\Java\jdk-13.0.2/bin)
     Tester avec le cmd en tapant la commande suivante : java -version

Après avoir télécharger le jdk ainsi que netbeans, vous devrez créer un nouveau projet (dans notre cas JavaWeb) :

    File -> Java With Ant -> Java Web -> Web Application
    Project Name -> <Nom que vous souhaitez>
    Project Location -> <Choisissez une arborescence ou votre application sera placée>
    Next
    
Vous voici dans le menu de *Server And Settings"*, ici intervient notre petit XAMPP qui fera office de server locale :

    Add -> Apache Tomcat or TomEE
    Server Location -> Aller dans votre arborescence XAMPP et accéder au dossier tomcat (pour nous : C:\xampp\tomcat)
    Username -> tomcat (défini précedemment)
    Password -> tomcat 

Et voilà, il ne vous reste plus qu'à *Run* votre projet avec F6, celui-ci ouvrira par défaut internet explorer. Pour modifier le Web browser par défaut :

    Tools -> Options -> Web Browser -> Firefox par exemple 
    
Cependant si un message d'erreur de ce type apparait :

    javaee-endorsed-api-6.0 library could not be found 
    
Il faudra alors installer ici : [javaee-endorsed-api-6.0.jar](http://www.java2s.com/Code/Jar/j/Downloadjavaeeendorsedapi60jar.htm). Puis, dans votre projet :

     Clic droit sur le nom du projet -> Properties
     Libraries ->  Add Jar/Folder -> cliquer sur la javaee-endorsed-api-6.0.jax
     
 **Tout** devrait **fonctionner** dorénavant.

Pour importer un projet éxistant, il suffit de désarchiver le .war et :

    File OpenProject -> Ouvrir la WebApplication
    
**Attention** : Il risque de manquer, si vous utilisez JDBC de MySQL pour votre base de données, ce package, il vous faudra suivre les mêmes étapes que la javaee-endorsed-api avec l'ajout d'une nouvelle librarie.

### En cas de complications

Si jamais votre configuration *Tomcat* ne marche pas, et que dans votre xamp control panel Tomcat
indique une erreur comme "Tomcat started/Stopped with errors, return code : 1", suivez ces instructions à
la lettre :

* En premier lieu, nous allons créer une variable d'environnement nommée "JAVA_MAIN", pour cela :

      Pressez la touche windows + la touche r, et tapez "control" puis Entrée
      Sélectionnez "Système"
      Paramètres de système avancés (sous windows 7, il faut pour cela pressez la touche windows, allez
      dans l'onglet "ordinateur", puis clic droit sur "ordinateur" -> "propriétés").
      Cliquez sur "variables d'environnement" -> "Nouveau" et donner le nom de la variable d'environnement (JAVA_MAIN par   exemple), puis dans la ligne en dessous donnez le chemin du dossier où se trouve l'installation de la JDK.

* Faites de même pour l'environnement JRE en créant une nouvelle variable d'environnement, que l'on
nommera par exemple JRE_MAIN, et indiquez le chemin vers le dossier où se trouve l'environnement
JRE.

* Une fois tout ceci fait, on peut tester si les manipulations se sont bien exécutées en lancer l'invite de
commande :

    Touche windows, puis tapez "cmd" -> "set JRE_MAIN" et "set JAVA_MAIN", si cela se passe bien, vous retrouverez le chemin indiqué dans pour chacune des variables d'environnement rentrée.

* Ensuite allez dans le répertoire xampp, puis dans le sous dossier Tomcat, et enfin dans le dossier conf,
éditez le fichier "server.xml" en allant à la ligne 70 : 
   
    Remplaçer le numéro de port par "port="9999".

* Ensuite toujours dans le dossier conf, éditez "context.xml" et allez à la ligne 19 et changez la balise *Context* :

      "<Context reloadable=true>".

* Allez ensuite dans votre xamp control panel, tout en haut à droite cliquez sur "config", puis dans l'onglet
tomcat changez le HTTP Port par le port que vous avez rentré précédemment : 9999.

* Tout ceci terminé, fermez xamp et relancez le, cela devrait normalement marcher (n'oubliez pas lorsque
vous tenterez d'aller sur la page /manager/html en localhost de changer le port par :9999)

### Manuel utilisateur de notre application

* Page de connexion 

Pour vous connecter en tant que docteur, et ainsi bénéficier des fonctionnalités comme pouvoir rentrer un
nouveau patient dans la base de données ou encore mettre à jour les données d'un patient pour ses visites
suivantes, entrez :

    Login : doctor
    Mot de passe : doctor
     
Pour vous connecter en tant qu'administrateur et ainsi pouvoir voir les statistiques de patients atteints de
maladie a, b ou c ou de patients guéris ou qui ne sont atteints par aucune maladie, entrez :

    Login : admin
    Mot de passe : admin
    
![](/images/CaptureConnexion.PNG)

* Page Docteur

En tant que docteur vous pouvez entrer un nouveau patient dans les champs situés à gauche nommés "Renseignement" et "Maladies?", dans ces champs vous entrerez le nom et l'âge du patient ainsi que son état de santé.

![](/images/CaptureRenseignement.PNG)
     
Appuyez sur valider pour finaliser cette opération. Néanmoins, seul l'admin sera capable de savoir si l'opérations s'est bien déroulé.

En revanche si votre patient revient vous voir après sa première visite, veuillez renseigner les champs situés à droite, nommés "Revisite du patient" et "Nouvel état". 

Vous renseignerez ainsi le nom du patient ainsi que son nouvel état (pour plus de renseignements à ce sujet, hésitez pas à cliquer en dessous de "Guide de revisite" sur le lien "En apprendre plus sur la visite médical" qui vous expliquera en détail le
principe de revisite médical)

Appuez sur Mise à jour pour finaliser cette opération.

![](/images/CaptureRevisite.PNG)

Vous pouvez vous déconnecter proprement en cliquant en haut à droite sur le bouton de déconnexion.

![](/images/CaptureDeconnexion.PNG)

* Page Admin

Sur la page admin vous avez un formulaire qui vous propose de visualiser les statistiques sur les patients
atteints de la maladie a, b, ou c, ou encore des patients n'ayant aucune maladie, et des patients guéris.

Cliquez sur le bouton correspondant à votre choix, puis cliquez sur le bouton choix pour valider votre
requête.

![](/images/CaptureStats.PNG)

S'ouvrira ensuite une page avec la statistique demandée.

Exemple de résultat :

![](/images/CaptureResultat.PNG)

Vous pouvez vous déconnecter proprement en cliquant en haut à droite sur le bouton de déconnexion.

![](/images/CaptureDeconnexion.PNG)

Ou revenir au formulaire de choix en cliquant en haut à gauche.

![](/images/CapturePrecedent.PNG)


### Conclusion

Ce tutoriel n'est qu'un court résumé des nombreuses étapes que nous avons pu effectués pour parvenir à une Java Web Application, il se peut alors que des oublis puissent avoir été faits.

Cependant, n'hésitez pas à nous contacter si vous rencontrer un problème
 

