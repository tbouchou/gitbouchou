# Installer et exécuter une application JEE

## Plan d'execution :

1. *Telechargements* :
  * XAMPP : pour les modules tomcat, apache et mySql en locale 
  * Netbeans
    
2. *Etapes (configuration)*

3. *Remarques et complications*

### Telechargements

Pour telecharger XAMPP, c'est très simple, il vous suffit de cliquer sur ce lien : [XAMPP dernière version](https://www.apachefriends.org/fr/index.html)

Pour Netbeans, voici le lien : [Netbeans dernière version]https://netbeans.apache.org/download/

### Etapes

La configuration est une étape essentiel pour la future construction de projets, il s'agit donc très attentif.

Pour XAMPP, ouvrir le control pannel et effectuer les commandes suivantes :

    Tomcat : Config -> tomcat-users.xml
    
Ajouter les 3 lignes suivantes dans la balise *tomcat-users*
 
     <role rolename="manager-gui"/>
     <user username="tomcat" password="tomcat" roles="manager-gui"/>
     <user username="tomcat" password="tomcat" roles="standard,manager-script" />

Modifier aussi les password présents dans la page en les remplacant par *tomcat*
    

