
# Gérer les Clés SSH

Ce mémo explique comment utiliser une seule paire de clés SSH sur plusieurs ordinateurs et présente quelques bonnes pratiques de sécurité.

-----

## Copier ses clés SSH

Pour utiliser une même clé SSH sur plusieurs machines, il suffit de copier les deux fichiers de la paire de clés (la clé privée et la clé publique) dans le dossier `.ssh` situé à la racine du **dossier utilisateur** sur chaque nouvel ordinateur. Ce dossier se trouve généralement à `/home/nom_utilisateur/.ssh/` sur Linux/macOS ou `C:\Users\NomUtilisateur\.ssh\` sur Windows.

**Exemple de fichiers :**

  * `id_rsa` (la clé privée)
  * `id_rsa.pub` (la clé publique)

-----

## Vérifier et définir les permissions des fichiers

Il est crucial de vérifier et d'ajuster les permissions des fichiers de clés et du dossier `.ssh` pour des raisons de sécurité. Des permissions incorrectes peuvent empêcher les clés de fonctionner.

Voici les permissions recommandées et les commandes pour les définir :

  * **Dossier `.ssh` :**

      * **Permissions :** Seul l'utilisateur propriétaire doit avoir les droits de lecture, écriture et exécution.
      * **Exemple de permissions affichées :** `drwx------`
      * **Commande pour définir :**
        ```bash
        chmod 700 ~/.ssh
        ```

  * **Clé privée (`id_rsa` ou similaire) :**

      * **Permissions :** Seul l'utilisateur propriétaire doit avoir les droits de lecture et d'écriture.
      * **Exemple de permissions affichées :** `-rw-------`
      * **Commande pour définir :**
        ```bash
        chmod 600 ~/.ssh/id_rsa
        ```

  * **Clé publique (`id_rsa.pub` ou similaire) :**

      * **Permissions :** L'utilisateur propriétaire doit avoir les droits de lecture et d'écriture, et d'autres utilisateurs peuvent avoir les droits de lecture.
      * **Exemple de permissions affichées :** `-rw-r--r--`
      * **Commande pour définir :**
        ```bash
        chmod 644 ~/.ssh/id_rsa.pub
        ```

-----

## Ajouter la clé à l'agent SSH (Recommandé)

Pour éviter de retaper le mot de passe de la clé privée à chaque connexion, il est possible de l'ajouter à l'agent SSH.

1.  **Lancer l'agent SSH** (si ce n'est pas déjà fait ; il est souvent lancé automatiquement au démarrage de la session) :
    ```bash
    eval "$(ssh-agent -s)"
    ```
2.  **Ajouter la clé privée à l'agent :**
    ```bash
    ssh-add ~/.ssh/id_rsa
    ```
    Si la clé privée est protégée par une phrase secrète (passphrase), il sera demandé de la saisir une seule fois.

-----

## Conseils de Sécurité Importants

  * **Utiliser une phrase secrète (passphrase) :** Toujours protéger la clé privée avec une phrase secrète forte. Cela ajoute une couche de sécurité cruciale : si le fichier de clé privée tombe entre de mauvaises mains, il sera inutile sans la phrase secrète.
  * **Ne jamais partager la clé privée :** La clé privée est un secret absolu. Ne jamais la partager et ne jamais la stocker dans des endroits non sécurisés. La clé publique, en revanche, est conçue pour être partagée.

-----
