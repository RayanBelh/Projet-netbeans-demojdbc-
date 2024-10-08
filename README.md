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
#### Les attributs :
- **id** : un entier représentant l'identifiant unique du site.
- **nom** : une chaîne de caractères représentant le nom du site.

#### Méthodes principales :
- `getId()` : Retourne l'identifiant du site.
- `setId(int id)` : Définit l'identifiant du site.
- `getNom()` : Retourne le nom du site.
- `setNom(String nom)` : Définit le nom du site.

### 2. `Test`

Cette classe contient les méthodes pour interagir avec la base de données MySQL et manipuler les données de la table `site`. Voici le code utilisé : 
```java
public class Test {

    public static void save(Site s) {
//Information d'accès à la base de données
        String user = "root";
        String password = "";
        String url = "jdbc:mysql://localhost/db";
        Connection cn = null;
        Statement st = null;
        try {
//Etape 1 : Chargement du driver
            Class.forName("com.mysql.jdbc.Driver");
//Etape 2 : Récupération de la connexion
            cn = (Connection) DriverManager.getConnection(url, user, password);
//Etape 3 : Création d'un statement
            st = (Statement) cn.createStatement();
            String req = "insert into site values(null,'" + s.getNom() + "')";
//Etape 4 : Exécution de la requête
            st.executeUpdate(req);
        } catch (SQLException e) {
            System.out.println("Erreur SQL");
        } catch (ClassNotFoundException ex) {
            System.out.println("Impossible de charger le driver");
        } finally {
            try {
//Etape 5 : Libérer les ressources de la mémoire
                st.close();
                cn.close();
            } catch (SQLException ex) {
                System.out.println("Impossible de libérer les ressources");
            }
        }
    }

    public static void main(String[] args) {
//insertion des données
        save(new Site("SAFI"));
        save(new Site("MARRAKECH"));
        save(new Site("EL JADIDA"));
    }

}
```

#### Méthodes principales :
- `save(Site s)` : Permet d'insérer un nouveau site dans la base de données.
- `main(String[] args)` : Appelle la méthode `save` pour ajouter des sites à la base de données.

## Fonctionnement de l'application

### 1. Connexion à la base de données

L'application se connecte à une base de données MySQL nommée **db** sur `localhost` en utilisant l'utilisateur **root** et un mot de passe vide (`""`). Les informations de connexion sont gérées par les lignes suivantes dans le code :

```java
String url = "jdbc:mysql://localhost/db";
String user = "root";
String password = "";
```
### 2. Main - Exécution des insertions
Dans la méthode main, les trois sites suivants sont insérés dans la base de données :
SAFI
MARRAKECH
EL JADIDA

Voici le bloc d'insertion :

```java
public static void main(String[] args) {
//insertion des données
        save(new Site("SAFI"));
        save(new Site("MARRAKECH"));
        save(new Site("EL JADIDA"));
    }
```
## Affichage dans la base de données : 
- Voici ce que ça donne sur phpMyadmin :

![WhatsApp Image 2024-09-30 à 20 00 53_7d05db0f](https://github.com/user-attachments/assets/b3e7a0fa-2d0e-4d51-9523-942708925965

# Conclusion : 
Ce projet offre une illustration simple mais efficace de la façon d'utiliser JDBC pour interagir avec une base de données MySQL dans une application Java. Grâce à l'utilisation des classes Site et Test, nous avons pu facilement insérer, consulter et gérer des enregistrements de sites web dans une table de base de données.

# Video démonstrative : 

https://github.com/user-attachments/assets/ad3e3367-04d4-48a1-9b30-11c50c8197ce




