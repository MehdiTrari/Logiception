# Si l'œuvre est sous droits, elle est ajoutée au répertoire "séquestre" et est disponible pour location.
## Description du Scénario : Ajout au Séquestre

### Acteurs Impliqués :
1. **Système de Bibliothèque** : Plateforme numérique qui gère l'ajout des œuvres au séquestre.
2. **Base de Données** : Stocke les informations des œuvres et leur statut.

### Processus :
1. **Sélection des Œuvres pour le Séquestre** :
   - Le Système de Bibliothèque identifie les œuvres sous droits d'auteur qui doivent être ajoutées au séquestre.

2. **Ajout des Œuvres au Séquestre** :
   - Le Système de Bibliothèque transfère les œuvres sélectionnées dans le répertoire "séquestre".
   - Ces œuvres sont chiffrées et leur accès est restreint.

3. **Mise à Jour de la Base de Données** :
   - Le Système de Bibliothèque met à jour la Base de Données pour refléter le nouvel emplacement et le statut d'accès des œuvres.

### Diagramme de Séquence :
- Les interactions débutent avec le Système de Bibliothèque qui sélectionne et déplace les œuvres dans le séquestre.
- Le Système de Bibliothèque interagit ensuite avec la Base de Données pour la mise à jour des informations.

### Diagramme de Classe :
- **Classe Système de Bibliothèque** : Contient des méthodes pour gérer le transfert des œuvres au séquestre et la mise à jour des informations.
- **Classe Base de Données** : Stocke les informations des œuvres, y compris leur emplacement et leur statut d'accès.

### Points Clés pour le Codage des Diagrammes :
- Les interactions entre le Système de Bibliothèque et la Base de Données doivent être clairement représentées.
- La classe Système de Bibliothèque doit avoir des méthodes spécifiques pour la gestion et la mise à jour des œuvres dans le séquestre.
- Le diagramme de séquence doit illustrer l'ordre des étapes et les interactions pour l'ajout des œuvres au séquestre.

## Diagramme de séquence

```mermaid
sequenceDiagram
    participant Systeme as Système de Bibliothèque
    participant BaseDeDonnees as Base de Données

    Systeme->>BaseDeDonnees: Demande d'ajout au séquestre
    activate BaseDeDonnees
    Note right of BaseDeDonnees: Ajoute l'œuvre au séquestre
    BaseDeDonnees-->>Systeme: Confirmation d'ajout
    deactivate BaseDeDonnees
```

## Diagramme de classe

```mermaid

classDiagram
    class SystemeBibliotheque {
        +demanderAjoutSequestre()
    }
    class BaseDeDonnees {
        +List sequestre
        +ajouterAuSequestre()
        +confirmerAjout()
    }

    SystemeBibliotheque --> BaseDeDonnees : demande ajout
    BaseDeDonnees --> SystemeBibliotheque : confirme ajout
```
