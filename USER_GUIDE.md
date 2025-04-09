# Guide Utilisateur - Meilisearch Data Manager

## Table des matières
1. [Vue d'ensemble](#vue-densemble)
2. [Prérequis](#prérequis)
3. [Interface principale](#interface-principale)
4. [Gestion des fichiers](#gestion-des-fichiers)
5. [Visualisation des données](#visualisation-des-données)
6. [Gestion des doublons](#gestion-des-doublons)
7. [Opérations Meilisearch](#opérations-meilisearch)
8. [Sécurité](#sécurité)

## Vue d'ensemble

Meilisearch Data Manager est une application web conçue pour gérer et synchroniser efficacement des données produits avec Meilisearch. Elle offre des fonctionnalités avancées pour :
- Importer et valider des données JSON
- Détecter et gérer les doublons
- Synchroniser les données avec Meilisearch
- Visualiser et manipuler les données produits

## Prérequis

- Un navigateur web moderne (Chrome, Firefox, Safari, Edge)
- Une instance Meilisearch active
- Les codes secrets pour les opérations (fournis par l'administrateur)
- Des fichiers JSON conformes au format requis

## Interface principale

L'interface se divise en trois sections principales :
1. Zone d'upload de fichiers
2. Gestionnaire de doublons
3. Onglets de visualisation et d'opérations

### Format JSON requis
```json
{
    "id": "",
    "name": "Nom du produit",
    "brand": null,
    "description": "Description du produit",
    "image": "",
    "type": null,
    "category": "Catégorie",
    "subcategory": "Sous-catégorie",
    "variants": [
        {
            "id": "",
            "size": "Taille",
            "case-size": 12,
            "container": "type de contenant",
            "dist-sku": ["ID-Distributeur"],
            "distributors": ["Nom-Distributeur"],
            "skus": ["SKU"]
        }
    ]
}
```

## Gestion des fichiers

### Upload de fichiers
1. Glissez-déposez vos fichiers JSON dans la zone prévue
2. Ou cliquez pour sélectionner les fichiers
3. Limitations :
   - Taille maximale : 100MB par fichier
   - Format accepté : JSON uniquement
   - Maximum 5 fichiers simultanés

### Validation des données
Après l'upload, l'application effectue automatiquement :
1. Validation de la structure JSON
2. Vérification des champs obligatoires
3. Détection des images manquantes
4. Attribution d'IDs uniques aux produits sans ID

## Visualisation des données

### Vue données
- Affichage tabulaire des produits
- Filtrage et recherche
- Tri par colonnes
- Export des données

### Fonctionnalités de reset
- Button "Reset Data" pour réinitialiser toutes les données
- Confirmation requise avant suppression
- Action irréversible

## Gestion des doublons

### Types de doublons
1. **Doublons exacts** (rouge) :
   - Produits identiques sur tous les champs clés
   - Même SKU, même caractéristiques

2. **Doublons partiels** (jaune) :
   - Même SKU mais différences dans certains champs
   - Variations dans les caractéristiques

### Actions sur les doublons
- Visualisation détaillée des différences
- Fusion de produits
- Suppression sélective
- Édition manuelle

## Opérations Meilisearch

### Push vers Meilisearch
1. Entrez le nom de l'index
2. Fournissez le code secret PUSH
3. Cliquez sur "Push to Meilisearch"
- Les données sont envoyées par lots de 100 documents

### Pull depuis Meilisearch
1. Entrez le nom de l'index
2. Fournissez le code secret PULL
3. Cliquez sur "Pull from Meilisearch"
- Limite de 10,000 documents par pull

### Suppression d'index
1. Entrez le nom de l'index
2. Fournissez le code secret REMOVE
3. Confirmez la suppression

## Sécurité

### Codes secrets
Trois codes différents sont requis pour les opérations sensibles :
- `CODE_SECRET_PUSH` : Pour envoyer des données
- `CODE_SECRET_PULL` : Pour récupérer des données
- `CODE_SECRET_REMOVE` : Pour supprimer un index

### Bonnes pratiques
1. Ne partagez jamais les codes secrets
2. Vérifiez toujours les données avant un push
3. Faites des sauvegardes régulières
4. Utilisez des noms d'index explicites

## Résolution des problèmes

### Erreurs communes
1. "Invalid API key" : Vérifiez le code secret
2. "Index name is required" : Le nom d'index est manquant
3. "Failed to push to Meilisearch" : Vérifiez la connexion au serveur
4. "JSON validation error" : Format de données incorrect

### Solutions
- Vérifiez la connexion internet
- Assurez-vous que Meilisearch est accessible
- Validez le format JSON
- Vérifiez les codes secrets
- Réduisez la taille des lots si nécessaire

## Support

Pour toute assistance supplémentaire :
1. Consultez la documentation technique
2. Ouvrez un ticket sur GitHub
3. Contactez l'équipe support
