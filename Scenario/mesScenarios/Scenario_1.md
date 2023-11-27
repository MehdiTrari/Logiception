# Un membre de l'association numérise une œuvre et la propose à la bibliothèque.

sequenceDiagram
    participant Membre as Membre de l'Association
    participant Systeme as Système de Bibliothèque
    participant BaseDeDonnees as Base de Données

    Membre->>Systeme: Propose une œuvre numérisée
    activate Systeme
    Note right of Systeme: Vérification initiale de l'œuvre
    Systeme->>BaseDeDonnees: Enregistre l'œuvre proposée
    activate BaseDeDonnees
    Note right of BaseDeDonnees: Stockage temporaire en attente de modération
    deactivate BaseDeDonnees
    Systeme-->>Membre: Accusé de réception
    deactivate Systeme


classDiagram
    class Membre {
        +String nom
        +String email
        +proposerOeuvre()
    }
    class SystemeBibliotheque {
        +List oeuvres
        +verifierOeuvre()
        +enregistrerOeuvre()
        +notifierMembre()
    }
    class BaseDeDonnees {
        +List oeuvresEnAttente
        +ajouterOeuvre()
        +supprimerOeuvre()
    }
    
    Membre --> SystemeBibliotheque : propose
    SystemeBibliotheque --> BaseDeDonnees : enregistre
