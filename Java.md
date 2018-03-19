# MÉMO JAVA


## Classe

Une classe modélise un type d'entité. Elle donne la description d'un ensemble d'attributs et de méthodes chargées de gérer ces attributs.

Une classe comporte :
* des attributs, d'instance ou de classe
* des méthodes, d'instance ou de classe
* plus rarement des classes internes, d'instance ou de classe

Une classe peut être qualifiée de :
1) abstraite
2) finale
3) publique
 
À partir d’une classe on peut créer un ou plusieurs objets par instanciation. **Chaque objet est une instance d’une seule classe**.

Visibilité :

1) **Publique** : le mot class est alors précédé de public, tout utilisateur qui importe le paquetage peut utiliser la classe. Dans ce cas elle doit être définie dans un fichier qui a pour nom le nom de la classe.
2) **Privé** : le mot class est alors précédé de private, seules des classes définies dans le même fichier peuvent utiliser cette classe.
3) **Paquetage**: le mot class n’est pas précédé de mot particulier, toutes les classes du paquetage peuvent utiliser la classe.


### Les types de classes 

Classe **abstraite**

Dès qu'une classe contient une méthode abstraite, elle doit elle aussi être déclarée abstraite.

Une classe abstraite ne peut pas être instanciée. Il faudra l'étendre et définir toutes les méthodes abstraites qu'elle contient pour pouvoir l'utiliser.

Classe **enveloppe**

À chaque type primitif est associée une classe qui permet de disposer de méthodes pour gérer ce type ; au type int est associée la classe Integer etc.

Classe **générique**

Il s'agit d'une classe dont la définition dépend d'un (ou plusieurs) « paramètre de type » représentant un nom de classe qui devra être précisé au moment de l'utilisation de la classe. La possibilité des classes génériques date du JDK 5.0.

Classe **interne**

Une classe peut être définie comme champ d'une classe ou bien à l'intérieur d'un bloc d'une méthode. Dans les deux cas, on dira qu'il s'agit d'une classe interne.

On peut attribuer à une classe qui figure comme champ d'une autre classe les mêmes modificateurs de visibilité que pour des attributs ou des méthodes, ainsi que les modificateurs abstract et final. Ces mots gardent le même sens que pour une classe non interne.

````
Une classe B interne à une classe A (mais non à une méthode) se nomme A.B. Pour instancier B de l'extérieur de A, on peut invoquer le constructeur de la classe B à partir d'une instance de la classe A. Par exemple, si A et B ont des constructeurs sans paramètre, on pourrait écrire :
    A.B b = (new A()).(new B());

De l'intérieur de A, on peut écrire :
    A b = new B();

On peut aussi qualifier de static une classe interne à une autre classe ; on ne peut alors pas y référencer une instance englobante. Si B est une classe statique interne à une classe A, on peut l'instancier par :
    A.B b = new A.B();

Une classe locale, définie à l'intérieur d'une méthode, n'est visible qu'à l'intérieur de celle-ci. On ne peut l'instancier que de l'intérieur de cette méthode. 
````


## Attribut

Un attribut se définit en donnant son type, puis son nom, et éventuellement une partie initialisation.

Visibilité :

1) **Public** : sa définition est précédée de public, et il peut être utilisé par tout utilisateur de la classe,
2) **Privé** : sa définition est précédée de private, et il ne peut être utilisé qu’à l’intérieur de la classe,
3) **Protégé** : sa définition est précédée de protected, et il ne peut être utilisé qu’à l’intérieur de la classe, ou des classes dérivées,
4) **Paquetage** : aucun mot particulier ne précède sa définition, ainsi il peut être utilisé dans toute classe du même paquetage.


## Méthode

Une méthode est définie par :

1) **Son type de retour** : type de la valeur retournée par la méthode. Si la méthode ne retourne pas de valeur le type spécifié est alors **void**,
2) **Son nom**,
3) **Ses paramètres** : les paramètres sont spécifiés par leur type et leur nom et sont séparés par des virgules.

Visibilité :
* **Public** : sa définition est précédée de public, et elle peut être utilisée par tout utilisateur de la classe,
* **Privé** : sa définition est précédée de private, et elle ne peut être utilisée qu’à l’intérieur de la classe,
* **Protégé** : sa définition est précédée de protected, et elle ne peut être utilisée qu’à l’intérieur de la classe, ou des classes dérivées,
* **Paquetage** : aucun mot particulier ne précède sa définition, ainsi la méthode peut être utilisé dans toute classe du même paquetage.

#### Prototype d'une méthode

On appelle ainsi la déclaration d'une méthode, qui est en Java de la forme :
    
    typeDeRetour nom(liste des paramètres);

Il n'y a pas de corps, mais à la place un "**;**". Cette déclaration peut être précédée de certains modificateurs. 


## Héritage

En Java, toute classe hérite d'une et une seule classe  _(sa superclasse.)_, sauf la classe Object (_java.lang.Object_), qui n'hérite d'aucune classe. On dit qu'il n'y a pas d'héritage multiple en java.  
Il n'y a pas d'héritage multiple. L'héritage s'exprime grâce au mot réservé **extends**.   
Une classe B qui hérite d'une classe A est dite sous-classe de A. Elle dispose de tous les attributs et méthodes de A, moyennant néanmoins quelques nuances liées aux modificateurs de visibilité, à la possibilité de masquage des attributs et au principe de la redéfinition des méthodes.   
Toute instance de la classe B est aussi considérée comme étant une instance de la classe A.  

Une interface peut hériter d'une ou plusieurs autres interfaces ; elle hérite de leurs constantes et de leurs prototypes de méthodes. 

On indique qu'une classe B hérite d'une classe A de la façon suivante :

    class B extends A  {
     ... 
    }

Alors, la classe B dispose de tous les attributs et méthodes de la classe A  
La classe B peut ajouter des attributs et des méthodes qui lui sont propres.  
Signalons néanmoins que les attributs et méthodes privées de la classe A ne sont pas directement accessibles dans la classe B. On peut éventuellement y faire indirectement appel en utilisant des méthodes accessibles de la classe A les invoquant.

On dit :

    A est la superclasse de B,
    B hérite de A (c'est logique car B possède tout ce que possède A),
    B est une sous-classe de A (c'est logique car B modélise un sous-ensemble de ce que modélise A),
    B étend A (c'est logique car B possède les champs de A et généralement des champs supplémentaires).

Si une classe, sauf la classe _java.lang.Object_ n'indique pas qu'elle étend une superclasse, par exemple :

    class Compte {
        ... 
    }
cela signifie :

    class Compte extends Object {
        ... 
    }

Une classe déclarée final ne peut pas être étendue. Par exemple, si on a :

    final class A {
        ... 
    }

alors la classe A ne peut pas être étendue.   


## Implement

Une classe peut implémenter une ou plusieurs interfaces, ce qui s'exprime à l'aide du mot réservé implements. Si une classe A implémente une interface I, cela implique que :
* la classe A hérite des constantes de I,
* toutes les méthodes figurant dans l'interface I doivent être définies par la classe A, sans quoi A sera une classe abstraite.

Les attributs et les méthodes d'une interface sont automatiquement publics, ce qui entraîne qu'une classe qui implémente l'interface devra déclarer publiques les méthodes de l'interface qu'elle définira. 


## Initialiseur
   
Dans une classe, un initialiseur est l'initialisation d'un attribut simultanément à sa définition ou, plus rarement, la définition d'un bloc d'instructions extérieur aux méthodes de cette classe.  
S'il n'est pas statique, un initialiseur est exécuté au moment de la construction d'une instance, avant l'exécution des constructeurs ; s'il y a plusieurs initialiseurs d'instance, ils sont exécutés dans l'ordre de leurs déclarations.  
On pourrait définir et initialiser deux attributs taille et entier d'une classe par :

    int taille = 5;
    Integer entier = new Integer(1);
   
Un initialiseur est statique s'il est précédé du mot static. 
Le rôle d'un initialiseur statique est en général d'initialiser des attributs statiques de la classe. 
Un initialiseur statique est exécuté au moment du chargement de la classe. 
Il peut arriver qu'on ait besoin d'un initialiseur statique sous forme d'un bloc d'instructions précédé du modificateur static, par exemple pour initialiser un tableau statique. 


## Polymorphisme

Supposons que deux classes B et C héritent d'une même classe A.  
Supposons que la classe A définisse une méthode d'instance meth redéfinie par les classes B et C (la méthode meth peut avoir ou non des paramètres ; nous la supposons ci-dessous sans paramètre).  
Supposons enfin que l'on ait les déclarations et instructions suivantes :

    A a = new A();
    a.meth();       //1
    a = new B();
    a.meth();       //2
    a = new C();
    a.meth();       //3

Alors, au moment de l'instruction 1, c'est la méthode 'meth' de la classe A qui est exécutée,  
au moment de l'instruction 2, c'est la méthode 'meth' de la classe B qui est exécutée,  
au moment de l'instruction 3, c'est la méthode 'meth' de la classe C qui est exécutée.  

On appelle cette propriété le polymorphisme. Une même référence peut désigner des objets ayant des comportements différents. 



## Encapsulation

**L'encapsulation de données constitue un principe fondamental d'un langage objet.**  
Il s'agit de la possibilité de « cacher » des données à l'intérieur d'une classe en ne permettant de les manipuler qu'au travers des méthodes de la classe.  
L'intérêt essentiel d'une telle opération est d'interdire que les données soient modifiées de façon contraire à l'usage attendu dans sa classe, et ainsi de maintenir l'ensemble des données de la classe dans un état cohérent.  
Un exemple simple est le cas d'une donnée numérique qui devrait rester positive pour garder sa signification : il est indispensable qu'un utilisateur ne puisse pas, par mégarde ou ignorance, lui attribuer une valeur négative.  
Pour encapsuler un attribut, il suffit de le déclarer ***privé***, c'est-à-dire de lui attribuer le modificateur de visibilité ***private***.  
On peut aussi encapsuler des méthodes qui ne servent qu'à un usage interne à la classe. 


## Surcharge

Une classe peut définir plusieurs méthodes ayant un même nom du moment que les types des paramètres de ces méthodes diffèrent (globalement, ou par leur ordre) ; on dit alors qu'il y a ***surcharge***.  
Une différence uniquement sur le type de la valeur renvoyée est interdite.  
Lorsqu'une méthode surchargée est invoquée, la différence sur les paramètres permet de déterminer la méthode dont il s'agit. 


## Instance
   
Une classe A est un modèle décrivant un type d'objets. **Une instance** de la classe A est un **objet construit selon le modèle fourni par la classe** A.  
Les expressions « un objet de type A » et « une instance de la classe A » sont synonymes. 


## Constructeur

Toute classe contient une méthode appelée constructeur.  
Cette méthode porte le même nom que la classe qui la contient et ne doit pas indiquer de valeur de retour.  
Un constructeur renvoie implicitement la référence de l'instance construite.  
Un constructeur sert en particulier à initialiser les attributs de la classe.  
La première ligne d'un constructeur est :

* Soit un appel au constructeur de la superclasse, appel effectué à l'aide du mot super suivi de parenthèses contenant éventuellement des paramètres,
* Soit un appel à un autre constructeur de la même classe ayant un jeu différent de paramètres, appel effectué à l'aide du mot this suivi de parenthèses contenant éventuellement des paramètres.

Lorsqu'un constructeur d'une classe ne fait pas appel à un autre constructeur, le compilateur ajoute automatiquement l'instruction :
    
    super();
    
en première ligne du constructeur.  
**Si la superclasse n'a pas de constructeur sans paramètre, une erreur est détectée à la compilation**.

Lorsqu'une classe ne contient pas de constructeur, le compilateur en ajoute automatiquement un qui ne comporte qu'un appel au constructeur sans paramètre de la superclasse.

Un exemple d'une classe possédant deux constructeurs

    class Essai {
    
        private int milieu;
        private int largeur;
        
        Essai(int i) {
        milieu = i;
    }
     
    Essai(int a, int b){
    
        this(a); //effectuera : milieu = a;
        largeur=b;
        }
    }


## Interface

Une interface définit un contrat que certaines classes pourront s'engager à respecter.  
Une interface comporte un en-tête (qui peut posséder le modificateur _**public**_) suivi du nom de l'interface, puis, entre accolades, une liste de **_constantes_** et de **_prototypes de méthodes_**.  
Le modificateur abstract peut figurer ou non devant son nom ; c'est indifférent car une **interface est par nature abstraite**.  
Une interface ne peut pas être instanciée et ne contient pas de constructeur.  
Une interface peut être implémentée par une classe.  
L'existence des interfaces permet de compenser l'absence d'héritage multiple.  
Une interface :
* sert à regrouper des constantes,
* mais surtout sert chaque fois que : 
    1) on veut traiter un ensemble d'objets qui ne sont pas tous nécessairement de la même classe mais qui ont en commun une partie « interface »,  
    2) seule cette partie « interface » intervient dans le traitement que l'on veut définir ; les classes de ces objets pourront alors implémenter une même interface.



## Getters et Setters

Lorsque l’on déclare les attributs en « private » dans notre classe, ces attributs sont accessibles uniquement par les méthodes de la classe.  
Si nous voulons pouvoir les récupérer depuis une autre classe, il nous faut des _**Getters**_ (accesseurs) et des _**Setters**_ pour changer la valeur d’un attribut depuis une autre classe.

Exemple, les getters possibles pour une classe Voiture :

    ...
    
    public Voiture(String marque, String modele, int capacite_passager, int vitesse_max)
        {
           this.marque = marque;
           this.modele = modele;
           this.capacite_passager = capacite_passager;
           this.VITESSE_MAX = vitesse_max;
           this.vitesse_actuelle = 0;
        }
        
        public String getMarque() {
            return marque;
        }
    
        public String getModele() {
            return modele;
        }
    
        public int getCapacite_passager() {
            return capacite_passager;
        }
    
        public int getVitesse_Max() {
            return Vitesse_Max;
        }
    
        public int getVitesse_Actuelle() {
            return vitesse_Actuelle;
        }
        
    ...

Ces **_getters_** nous permettent de récupérer la marque, le modèle, les vitesses max' et actuelle de notre voiture depuis une autre classe ou bien tout simplement si nous souhaitons effectuer un affichage dans notre main.java :

    System.out.println("Vitesse actuelle : " + voiture1.getVitesse_actuelle() + "Km/h");
    

Voici maintenant les **setters** possibles pour la classe Voiture :

    public void setMarque(String marque) {
        this.marque = marque;
    }

    public void setModele(String modele) {
        this.modele = modele;
    }

    public void setCapacite_passager(int capacite_passager) {
        this.capacite_passager = capacite_passager;
    }

    public void setVitesse_actuelle(int vitesse_actuelle) {
        this.vitesse_actuelle = vitesse_actuelle;
    }

Grâce aux **setters**, nous pouvons modifier la valeur des attributs de notre objet _voiture1_.  
Par exemple, si nous souhaitons modifier sa capacité :

    voiture1.setCapacite_passager(4);   // passe de 3 à 4

Au final, le fichier _**main.java**_ ressemble à :

    public class main {

        public static void main(String[] args) {
            
            Voiture voiture1 = new Voiture("Citroen", "C3", 3, 200);
            
            voiture1.accelerer(10);
    
            System.out.println("Notre voiture : " + voiture1.getMarque() + " " + voiture1.getModele());
            System.out.println("Vitesse actuelle : " + voiture1.getVitesse_actuelle() + "Km/h"); // affiche 10
            
            voiture1.setCapacite_passager(4);
        }
    }

Notre fichier _**Voiture.java**_, qui contient notre classe Voiture (avec ses attributs, son constructeur, ses méthodes, setters et getters) a quant à lui cette allure :

    public class Voiture {
        private String marque;
        private String modele;
        private int capacite_passager;
        private final int VITESSE_MAX;
        private int vitesse_actuelle;
    
        // constructeur
        public Voiture(String marque, String modele, int capacite_passager, int vitesse_max)
        {
           this.marque = marque;
           this.modele = modele;
           this.capacite_passager = capacite_passager;
           this.VITESSE_MAX = vitesse_max;
           this.vitesse_actuelle = 0;
        }
        
        // une méthode
        public void accelerer(int vitesse_plus)
        {
            int test_vitesse = vitesse_actuelle + vitesse_plus;
            
            if(test_vitesse > VITESSE_MAX)
            {
                System.out.println("Impossible d'accéler. La vitesse maximale serait dépassée.");
            }
                
            else
            {
                vitesse_actuelle += vitesse_plus;
            }
        }
    
        // getters
        public String getMarque() {
            return marque;
        }
    
        public String getModele() {
            return modele;
        }
    
        public int getCapacite_passager() {
            return capacite_passager;
        }
    
        public int getVITESSE_MAX() {
            return VITESSE_MAX;
        }
    
        public int getVitesse_actuelle() {
            return vitesse_actuelle;
        }
    
        // setters
        public void setMarque(String marque) {
            this.marque = marque;
        }
    
        public void setModele(String modele) {
            this.modele = modele;
        }
    
        public void setCapacite_passager(int capacite_passager) {
            this.capacite_passager = capacite_passager;
        }
    
        public void setVitesse_actuelle(int vitesse_actuelle) {
            this.vitesse_actuelle = vitesse_actuelle;
        }
    }




## TYPES
| Nom      |  Taille en octets lors des calculs  | Valeur par défaut | Valeurs possibles |
|:---------|:-----------------------------------:|:-----------------:|:------------------|
| Object   | _Dépendant de la machine virtuelle_ | null              |                   |
| byte     | 1                                   | 0                 | entiers compris entre −128 et +127 (−2⁷ et 2⁷−1)               |
| short    | 2                                   | 0                 | entiers compris entre −32 768 et +32 767 (−2¹⁵ et 2¹⁵−1)       |
| int      | 4                                   | 0                 | entiers compris entre −2 147 483 648 et +2 147 483 647 (−2³¹ et 2³¹−1)|
| long     | 8                                   | 0                 | entiers compris entre −9 223 372 036 854 775 808 et +9 223 372 036 854 775 807 (−2⁶³ et 2⁶³−1)|
| float    | 4                                   | 0.0               | Ensemble des nombres [−3,40282347 × 10³⁸ .. −1,40239846 × 10⁻⁴⁵], 0, [1,40239846 × 10⁻⁴⁵ .. 3,40282347 × 10³⁸]|
| double   | 8                                   | 0.0               | Ensemble des nombres [−1,79769313486231570 × 10³⁰⁸ .. −4,94065645841246544 × 10⁻³²⁴], 0, [4,94065645841246544 × 10⁻³²⁴ .. 1,79769313486231570 × 10³⁰⁸]|
| char     | 2                                   | '\u0000'          | Ensemble des valeurs Unicode (valeurs de U+0000 à U+FFFF, 4 chiffres obligatoires après '\u') Les 128 premiers caractères sont les codes ASCII et se notent entre apostrophes : 'a', '1', '\, '\n'.|
| boolean  | Un seul bit suffit*                 | false             | true, false      |
\* mais on réserve souvent un octet pour les stocker.


## OPERATEURS

The precedence of each Boolean operator is as follows:

* **!**     est évalué en **premier**
* **&&**    est évalué en **second**
* **||**    est évalué en **troisième**


### Test d'égalité
    
Pour tester l'égalité entre deux nombres, on utilise le double symbole '**==**' . Le signe '**=**' est réservé à l'affectation d'une valeur à une variable.  
Pour tester l'égalité entre deux objets, le double symbole '**==**' ne convient pas, il faut utiliser la méthode equals de la classe Object, à condition que cette méthode soit redéfinie dans la classe des objets qu'on veut comparer. 



## UN EXEMPLE...

De façon à préparer l'exemple suivant, portant sur une banque, on complète la classse `CompteC` pour obtenir une classe Compte qui ne devrait pas présenter de difficultés.  
On ajoute deux attributs : l'un pour un `numéro` de compte (de type int), l'autre pour le nom d'un `propriétaire` (de type String).  
On ajoute par ailleurs une méthode nommée `toString` dont l'objectif est de décrire l'objet considéré avec une chaîne de caractères (i.e. un objet de type String). La méthode `toString` retourne la chaîne de caractères choisie. 

Le fichier **_Compte.java_**
 
    package banque;

    public class Compte {
     private String proprietaire;
     private int numero;
     private int montant;
     
     // Constructeur de la classe Compte
     public Compte(String proprietaire, int numero, int montant){
        this.proprietaire = proprietaire;
        this.numero = numero;
        this.montant = montant;
     }
    
     public void modifier(int somme) {
        if (this.montant + somme > 0) this.montant = this.montant + somme;
     }
    
     public int getMontant() {
        return this.montant;
     }
    
     public int getNumero() {
        return this.numero;
     }
    
     public String getProprietaire() {
        return proprietaire;
     }
     
     public String toString() {
        return "Compte numero " + this.numero + " : proprietaire " + 
        this.proprietaire + ", montant " + this.montant;
     }
    }
    
On a défini précédemment une classe nommée `Compte` qui modélise un compte en banque.  
On imagine que quelqu'un veuille utiliser cette classe en y ajoutant des propriétés pour obtenir une classe qui modélise un compte rémunéré.  
Pour cela, on souhaite  :
* ajouter un attribut de type double, nommé `taux`, pour le taux de rémunération annuelle,  
* une méthode, nommée `prevoirMontant`, ayant un paramètre de type int nommé `nbAnnees`, pour prévoir le montant du compte (si il n'y a plus n'y retrait ni versement) après nbAnnees.  
On décide d'utiliser l'héritage en procédant comme ci-dessous.  

Le fichier _**CompteRemunere.java**_ : 

    public class CompteRemunere extends Compte {
    
        private double taux;
    
        public CompteRemunere(String proprietaire, int numero, int montant, double taux) {	
        
            super(proprietaire, numero, montant);	
            this.taux = taux;
        }
        	
        public double prevoirMontant(int nbAnnees) {
        
            return getMontant() * Math.pow(1 + taux, nbAnnees);
        }
    }
    
    