# Installer et exécuter une application JEE

## Plan d'execution :

1. *Telechargements* :
  * XAMPP : pour les modules tomcat, apache et mySql en locale 
  * Netbeans
    
2. *Etapes (configuration)*

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
    
Puis lancer les services suivants : Apache, MySQL (si vous comptez utiliser phpmyadmin)

Ces ajouts permetteront la connexion locale au serveur et manager/html de tomcat.

Modifier aussi les password présents dans la page en les remplacant par *tomcat*

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

     
### Conclusion

Ce tutoriel n'est qu'un court résumé des nombreuses étapes que j'ai pu effectué pour parvenir à une Java Web Application, il se peut alors que des oublis puissent avoir été faits.

Cependant, n'hésitez pas à me contacter si vous rencontrer un problème : @tbouchou
 
 

