# Logiception
## Résumé en 1 phrase :
Conception D'une bibliothèque numérique décentralisée.
## Description du projet :
Le projet de CultureDiffusion consiste à développer une bibliothèque numérique où les membres peuvent numériser et partager des œuvres, avec une gestion décentralisée permettant un accès gratuit aux œuvres du domaine public et une location de deux semaines pour les œuvres sous droits d'auteur, soutenue par une structure de fichiers et une modération collaborative pour enrichir et maintenir la collection.

## Sommaire

[**Glossaire**](./glossaire.md)  
[**Scénario**](./Scenario)  
[**Suivi**](./suivi.md)  

## Diagramme de séquence du logiciel : 

```mermaid

sequenceDiagram
    participant Membre as Membre de l'Association
    participant Systeme as Système de Bibliothèque
    participant BaseDeDonnees as Base de Données
    participant Moderateur as Modérateur
    participant Bibliothequaire as Bibliothécaire

    Membre->>Systeme: Propose une œuvre numérisée
    activate Systeme
    Note right of Systeme: Vérification initiale de l'œuvre
    Systeme->>BaseDeDonnees: Enregistre l'œuvre proposée
    activate BaseDeDonnees
    Note right of BaseDeDonnees: Stockage temporaire en attente de modération
    BaseDeDonnees-->>Systeme: Confirmation d'enregistrement
    deactivate BaseDeDonnees
    Systeme-->>Membre: Accusé de réception

    Systeme->>Moderateur: Soumet l'œuvre pour modération
    activate Moderateur
    Note right of Moderateur: Vérifie les informations de l'œuvre
    Moderateur-->>Systeme: Résultat de la modération

    Moderateur->>Bibliothequaire: Transfert de l'œuvre pour vérification
    activate Bibliothequaire
    Note right of Bibliothequaire: Vérifie les informations détaillées
    Bibliothequaire-->>Moderateur: Résultat de la vérification

    Bibliothequaire->>Systeme: Transmet les informations vérifiées
    Note right of Systeme: Décide du statut légal de l'œuvre
    Systeme->>BaseDeDonnees: Met à jour le statut de l'œuvre
    activate BaseDeDonnees
    BaseDeDonnees-->>Systeme: Confirmation de mise à jour
    deactivate BaseDeDonnees
    Systeme-->>Bibliothequaire: Notification du statut légal

    alt Œuvre dans le domaine public
        Systeme->>BaseDeDonnees: Demande d'ajout au fond commun
        activate BaseDeDonnees
        Note right of BaseDeDonnees: Ajoute l'œuvre au fond commun
        BaseDeDonnees-->>Systeme: Confirmation d'ajout
        deactivate BaseDeDonnees
    else Œuvre sous droits
        Systeme->>BaseDeDonnees: Demande d'ajout au séquestre
        activate BaseDeDonnees
        Note right of BaseDeDonnees: Ajoute l'œuvre au séquestre
        BaseDeDonnees-->>Systeme: Confirmation d'ajout
        deactivate BaseDeDonnees
    end

    Systeme-->>BaseDeDonnees: Demande de mise à jour de l'index
    activate BaseDeDonnees
    Note right of BaseDeDonnees: Met à jour l'index des œuvres
    BaseDeDonnees-->>Systeme: Confirmation de mise à jour
    deactivate BaseDeDonnees

    Membre->>Systeme: Demande d'emprunt ou de location
    activate Systeme
    Note right of Systeme: Vérifie la disponibilité et les droits
    Systeme->>BaseDeDonnees: Vérifie les informations de l'œuvre
    activate BaseDeDonnees
    BaseDeDonnees-->>Systeme: Fournit les informations
    deactivate BaseDeDonnees
    Systeme-->>Membre: Confirme l'emprunt ou la location

    alt Location d'une œuvre sous droits
        Systeme->>BaseDeDonnees: Demande de contrôle des copies
        activate BaseDeDonnees
        Note right of BaseDeDonnees: Vérifie le nombre et l'état des copies
        BaseDeDonnees-->>Systeme: Rapport sur les copies
        deactivate BaseDeDonnees
        alt Nombre de copies < 3
            Systeme->>BaseDeDonnees: Demande de génération de copie chiffrée
            activate BaseDeDonnees
            Note right of BaseDeDonnees: Génère la copie chiffrée
            BaseDeDonnees-->>Systeme: Copie chiffrée générée
            deactivate BaseDeDonnees
            Systeme-->>Membre: Place la copie chiffrée dans le répertoire 'Emprunts'
            activate Membre
            Note right of Membre: Réception et stockage de la copie
            Membre-->>Systeme: Confirmation de réception
            deactivate Membre
        else Nombre de copies ≥ 3
            Systeme-->>Membre: Notification de la limite atteinte
        end
    end
```
