# Précautions Importantes - Repository Backend

## ⚠️ AVERTISSEMENTS CRITIQUES

### 1. 🔴 Push avec --force

**DANGER** : Le script utilise `git push --force`

```powershell
git push -u origin master --force
```

**Conséquences** :
- ✅ Écrase la version distante
- ✅ Version locale devient la référence
- ⚠️ Perte des commits distants non présents en local

**Justification** :
- Version locale mise à jour quotidiennement
- Version locale toujours prioritaire
- Plusieurs sauvegardes déjà effectuées avec succès

**Précaution** :
- ✅ Toujours vérifier l'état local avant push
- ✅ S'assurer que les modifications locales sont correctes
- ✅ Utiliser le script de vérification avant push

### 2. 🟡 Changement de Remote

**ATTENTION** : Le remote est changé temporairement

```powershell
# Sauvegarde
$currentRemote = git remote get-url origin

# Changement
git remote set-url origin https://github.com/sekadalle2024/Back-end-python-V0_03_03_2026.git

# ... push ...

# Restauration
git remote set-url origin $currentRemote
```

**Risques** :
- ⚠️ Si le script est interrompu, le remote reste changé
- ⚠️ Commits suivants iraient vers le mauvais repository

**Protection** :
- ✅ Script de restauration disponible
- ✅ Vérification du remote après chaque opération
- ✅ Message de confirmation à l'utilisateur

### 3. 🟢 Dossier py_backend/ Uniquement

**IMPORTANT** : Seul le dossier `py_backend/` est poussé

```powershell
git add py_backend/
```

**Implications** :
- ✅ Autres dossiers ignorés
- ✅ Taille du repository backend réduite
- ⚠️ Modifications hors py_backend/ non sauvegardées dans ce repo

**Vérification** :
```powershell
git status py_backend/
```

## 🛡️ Mesures de Sécurité

### Avant Chaque Push

1. **Vérifier l'État Local**
   ```powershell
   git status
   git status py_backend/
   ```

2. **Vérifier le Remote Actuel**
   ```powershell
   git remote -v
   ```

3. **Vérifier la Branche**
   ```powershell
   git branch
   ```

### Pendant le Push

1. **Confirmation Utilisateur**
   - Le script demande confirmation avant `--force`
   - Lire attentivement le message
   - Répondre "o" seulement si sûr

2. **Surveillance des Messages**
   - Vérifier les messages de succès
   - Noter les erreurs éventuelles
   - Vérifier "Everything up-to-date" ou "Branch 'master' set up to track"

### Après le Push

1. **Vérifier le Remote Restauré**
   ```powershell
   git remote -v
   # Doit afficher le repo principal
   ```

2. **Vérifier sur GitHub**
   - Aller sur https://github.com/sekadalle2024/Back-end-python-V0_03_03_2026
   - Vérifier que les fichiers sont à jour
   - Vérifier la date du dernier commit

## 🚫 Erreurs à Éviter

### 1. Ne PAS Interrompre le Script

❌ **MAUVAIS** : Ctrl+C pendant l'exécution
```
Script en cours...
^C  ← NE PAS FAIRE
```

✅ **BON** : Laisser le script terminer
```
Script en cours...
✓ Push réussi!
✓ Remote restauré
```

**Si Interrompu** :
```powershell
# Restaurer manuellement le remote
.\Doc backend github\Scripts\restaurer-remote-original.ps1
```

### 2. Ne PAS Modifier Manuellement le Remote

❌ **MAUVAIS** : Changer le remote manuellement
```powershell
git remote set-url origin [autre-url]  # NE PAS FAIRE
```

✅ **BON** : Utiliser le script
```powershell
.\Doc backend github\Scripts\push-backend-to-github.ps1
```

### 3. Ne PAS Pusher Sans Vérification

❌ **MAUVAIS** : Push direct sans vérification
```powershell
git push --force  # NE PAS FAIRE
```

✅ **BON** : Utiliser le script avec vérifications
```powershell
.\Doc backend github\Scripts\verifier-etat-backend.ps1
.\Doc backend github\Scripts\push-backend-to-github.ps1
```

## 🔧 Procédures de Récupération

### Si le Remote N'est Pas Restauré

```powershell
# 1. Vérifier le remote actuel
git remote -v

# 2. Si c'est le repo backend, restaurer
git remote set-url origin https://github.com/sekadalle2024/Claverse_windows__v_9_19-04-2026_V5-Export_CAC-V0-Public.git

# 3. Vérifier
git remote -v
```

### Si le Push Échoue

```powershell
# 1. Vérifier l'état
git status

# 2. Vérifier la connexion
git remote -v

# 3. Vérifier les credentials
# S'assurer d'être authentifié sur GitHub

# 4. Réessayer
.\Doc backend github\Scripts\push-backend-to-github.ps1
```

### Si Conflit de Versions

```powershell
# La version locale est prioritaire
# Le --force écrase la version distante
# C'est le comportement attendu

# Si besoin de récupérer la version distante d'abord :
git fetch origin
git log origin/master  # Voir les commits distants
# Puis décider si merge ou force push
```

## 📋 Checklist de Sécurité

Avant chaque sauvegarde backend :

- [ ] Vérifier que py_backend/ contient les dernières modifications
- [ ] Vérifier qu'aucun fichier sensible n'est inclus
- [ ] Vérifier le remote actuel (doit être le repo principal)
- [ ] Lancer le script de vérification
- [ ] Lire attentivement les messages du script
- [ ] Confirmer le push seulement si tout est correct
- [ ] Vérifier le remote après le push (doit être restauré)
- [ ] Vérifier sur GitHub que les fichiers sont à jour

## 🆘 En Cas de Problème

1. **Ne pas paniquer**
2. **Noter l'erreur exacte**
3. **Consulter TROUBLESHOOTING.md**
4. **Utiliser les scripts de récupération**
5. **Vérifier l'état avec `git status` et `git remote -v`**

## 📞 Support

En cas de problème persistant :
1. Consulter `Documentation/TROUBLESHOOTING.md`
2. Vérifier les logs Git
3. Restaurer le remote si nécessaire
4. Recommencer avec le script de vérification

## 🔒 Bonnes Pratiques

1. **Toujours utiliser les scripts fournis**
2. **Ne jamais modifier Git manuellement pour ce workflow**
3. **Vérifier avant et après chaque opération**
4. **Garder une copie locale de sauvegarde**
5. **Documenter les modifications importantes**

---

**Date de dernière mise à jour** : 19 avril 2026
**Version** : 1.0
