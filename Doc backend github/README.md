# Documentation Repository Backend Python

## 📌 Vue d'ensemble

Ce dossier contient toute la documentation et les scripts pour gérer le repository GitHub spécifique au backend Python du projet Claraverse.

### 🎯 Objectif

Le repository `Back-end-python-V0_03_03_2026` est un repository **séparé** qui contient **uniquement** le dossier `py_backend/` du projet complet.

## 🏗️ Architecture des Repositories

```
Projet Local (PC)
├─ py_backend/              ← Indexé sur repo backend
├─ src/
├─ public/
├─ Doc menu demarrer/
└─ ... (autres dossiers)    ← Indexés sur repo principal

GitHub Repositories
├─ Claverse_windows         ← Projet complet
└─ Back-end-python-V0_03_03_2026  ← py_backend/ uniquement
```

## ⚠️ Spécificités Critiques

### 1. Deux Repositories Distincts

- **Repository Principal** : `Claverse_windows__v_9_19-04-2026_V5-Export_CAC-V0-Public`
  - Contient : Projet complet
  - Remote : `origin`

- **Repository Backend** : `Back-end-python-V0_03_03_2026`
  - Contient : Dossier `py_backend/` uniquement
  - Remote : Changé temporairement lors du push

### 2. Workflow de Sauvegarde

Le script automatique :
1. Sauvegarde le remote actuel
2. Change vers le repository backend
3. Push avec `--force` (version locale prioritaire)
4. Restaure le remote original

### 3. Version Locale Prioritaire

⚠️ **IMPORTANT** : La version locale du backend est toujours prioritaire
- Le push utilise `--force` pour écraser la version distante
- Justification : Mises à jour quotidiennes du backend en local

## 📂 Structure de la Documentation

```
Doc backend github/
├─ 00_COMMENCER_ICI.txt              ← Démarrage rapide
├─ README.md                          ← Ce fichier
├─ Documentation/
│  ├─ ARCHITECTURE_BACKEND_GITHUB.md
│  ├─ PRECAUTIONS_IMPORTANTES.md
│  ├─ GUIDE_UTILISATION_QUOTIDIENNE.md
│  ├─ TROUBLESHOOTING.md
│  └─ HISTORIQUE_MODIFICATIONS.md
└─ Scripts/
   ├─ push-backend-to-github.ps1
   ├─ verifier-etat-backend.ps1
   └─ restaurer-remote-original.ps1
```

## 🚀 Utilisation Rapide

### Sauvegarder le Backend

```powershell
.\Doc backend github\Scripts\push-backend-to-github.ps1
```

### Vérifier l'État Avant Push

```powershell
.\Doc backend github\Scripts\verifier-etat-backend.ps1
```

## 📖 Documentation Détaillée

- **Architecture** : Voir `Documentation/ARCHITECTURE_BACKEND_GITHUB.md`
- **Précautions** : Voir `Documentation/PRECAUTIONS_IMPORTANTES.md`
- **Guide quotidien** : Voir `Documentation/GUIDE_UTILISATION_QUOTIDIENNE.md`
- **Dépannage** : Voir `Documentation/TROUBLESHOOTING.md`

## 🔗 Liens Utiles

- Repository Backend : https://github.com/sekadalle2024/Back-end-python-V0_03_03_2026.git
- Repository Principal : https://github.com/sekadalle2024/Claverse_windows__v_9_19-04-2026_V5-Export_CAC-V0-Public.git

## 📅 Historique

- **19/04/2026** : Création de la documentation complète
- **Contexte** : Plusieurs sauvegardes existantes, version locale prioritaire

## 🆘 Support

En cas de problème :
1. Consulter `Documentation/TROUBLESHOOTING.md`
2. Vérifier l'état avec `verifier-etat-backend.ps1`
3. Restaurer le remote si nécessaire avec `restaurer-remote-original.ps1`
