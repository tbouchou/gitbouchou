# Installer et exécuter une application JEE

## Plan d'execution :

1. *Telechargements* :
  * XAMPP : pour les modules tomcat, apache et mySql en locale 
  * Netbeans
    
2. *Etapes (configuration)*

3. *Remarques et complications*

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

Ces ajouts permetteront la connexion locale au serveur et manager/html de tomcat.

Modifier aussi les password présents dans la page en les remplacant par *tomcat*

La partie XAMPP s'arrête là, préparez-vous cependant pour la partie **Netbeans**

Après avoir télécharger vous aurez à créer un nouveau projet (dans notre cas JavaWeb) :

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

    

