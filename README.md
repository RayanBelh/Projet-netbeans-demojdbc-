# Application de Gestion de Sites : Projet-netbeans

Ce projet est un exemple simple d'une application Java pour la gestion de sites web en utilisant JDBC pour interagir avec une base de données MySQL. 

## Structure du code

Le code est organisé en deux classes principales dans le package `beans` :

### 1. `Site`

La classe `Site` définit la structure d'un site avec les attributs suivants et des méthodes comme suit :
```java
public class Site {
private int id;
private String nom;

public Site() {
}
public Site(String nom) {
this.nom = nom;
}
public int getId() {
return id;
}
public void setId(int id) {
this.id = id;
}
public String getNom() {
return nom;
}
public void setNom(String nom) {
this.nom = nom;
}
}
```
- **id** : un entier représentant l'identifiant unique du site.
- **nom** : une chaîne de caractères représentant le nom du site.

#### Méthodes principales :
- `getId()` : Retourne l'identifiant du site.
- `setId(int id)` : Définit l'identifiant du site.
- `getNom()` : Retourne le nom du site.
- `setNom(String nom)` : Définit le nom du site.

### 2. `Test`

Cette classe contient les méthodes pour interagir avec la base de données MySQL et manipuler les données de la table `site`. 

#### Méthodes principales :
- `save(Site s)` : Permet d'insérer un nouveau site dans la base de données.
- `main(String[] args)` : Appelle la méthode `save` pour ajouter des sites à la base de données.

#
