[home](README.md) - [makefile](makefile.md) - [git](git.md) - [gdb](gdb.md) - [valgrind](valgrind.md) - [strace](strace.md) - [objdump](objdump.md) - [gprof](gprof.md) - [calgrind](callgrind.md) - [linux](linux.md)- [escape code](ainsi_escape_code.md)
***
# PHP
# Sommaire

[Sécurité pour un projet](#Sécurité_pour_un_projet)
1. [Protection des Données](#protection-des-données-bdd-et-affichage)
   - [Injection SQL](#injection-sql-vol-de-données)
   - [Protection XSS](#protection-xss)
   - [Stockage des mots de passe](#stockage-des-mots-de-passe-bdd)

2. [Architecture et Environnement](#architecture-et-environnement)
   - [Isolation des dossiers](#isolation)
   - [Fichiers sensibles](#fichiers-sensibles)
   - [Fichiers Git](#fichiers_git)

3. [Gestion des Erreurs en Production](#gestion-des-erreurs-en-environnement-de-prod)

4. [Contrôle d'Accès et Sessions](#contrôle-daccès--sessions)
   - [Routeur](#routeur-indexphp)
   - [Protection CSRF](#protection-csrf-cross-site-request-forgery)

5. [Configuration du Serveur (Apache/.htaccess)](#serveur-apache--htaccess)
   - [Dossier Public](#dossier-public)
   - [Racine du Projet](#racine-du-projet)

6. [Content Security Policy (CSP)](#content-security-policy-csp)

7. [Protection des Utilisateurs](#protection-utilisateurs)
   - [Accès](#accès)
   - [Validation des Données](#données)
   - [Upload de Fichiers](#upload)

8. [Divers](#divers)
   - [Fonctions dangereuses](#empecher-lexecution-de-phpinfo-ou-system)

## Sécurité pour un projet

### Protection des Donées (BDD et Affichage)
* Injection SQL (vol de données)
    - Interdiction formelle : Ne jamais concaténer ou injecter directement des variables ($id, $_GET, etc.) dans une chaîne de requête SQL.
    - Solution unique : Utiliser systématiquement les requêtes préparées (Prepared Statements) avec PDO.
    - Principe : Séparer la structure de la requête (le code SQL) des données (les valeurs). Le moteur SQL analyse la structure d'abord, rendant l'injection de code malveillant impossible.

        Exemple À PROSCRIRE (Vulnérable) :
        ``` PHP
        $db->query("SELECT * FROM users WHERE email = '" . $_POST['email'] . "'");
        // Un pirate peut entrer : ' OR '1'='1
        ```
        Exemple À UTILISER (Sécurisé) :
        ``` PHP
        $query = $db->prepare("SELECT * FROM users WHERE email = :email");
        $query->execute(['email' => $_POST['email']]);
        $user = $query->fetch();
        ```
* Protection XSS
    - Le contenu dynamique doit être traité comme du texte, jamais comme du code HTML potentiel.
    - Ne jamais faire de echo sur une variable sans utiliser htmlspecialchars().
* Stockage des mots de passe (BDD)
    - Règle d'or : Ne jamais stocker un mot de passe en clair ou utiliser des algorithmes obsolètes (MD5, SHA1).
    - Hachage obligatoire : Utiliser password_hash($password, PASSWORD_DEFAULT) lors de l'inscription/modification.
    - Vérification : Utiliser password_verify($password, $hash) lors de l'authentification.

### Architecture et Environnement
* Isolation
    - Seul le dossier public/ (contenant index.php) doit être accessible par le serveur web.
    - Tout le code source (src/, app/) est à l'extérieur.
* Fichiers sensibles
    - Placer en dehors du dossier public
    - Idéalement a la racine du projet ou dans un dossier spécifique a la racine du projet
    - Ne pas versionner de fichier contenant de mot de passes
    - Versionner un placeholder pour avoir la liste des informations a renseigner
* Fichiers Git
    - fichiers .git, .gitignore, .gitattributes a la racine du projet.

### Gestion des Erreurs en environnement de prod
- display_errors doit être à Off.
- display_startup_errors doit être à Off.
- log_errors à On vers un fichier protégé. Ne jamais montrer de PDOException (stack trace) à l'utilisateur final.
    
- Exemple :
    ``` PHP
    <?php
    error_reporting(E_ALL);
    ini_set('log_errors', 1);
    ini_set('error_log', __DIR__ . '/../logs/php_errors.log');
    $config = parse_ini_file(__DIR__ . '/../.env');
    if ($config['APP_ENV'] === 'dev') {
        ini_set('display_errors', 1);
        ini_set('display_startup_errors', 1);
    } else {
        ini_set('display_errors', 0);
        ini_set('display_startup_errors', 0);
    }
    ```

### Contrôle d'Accès & Sessions
* Routeur (index.php)
    - Vérification par Liste Blanche. Rejeter immédiatement toute URI non déclarée et non valide en 404.
    - Vérification de la methode de requete (GET pour la lecture, POST pour la création...) => éviter les erreurs d'exécution.
    - Transformer l'URI validée (client, liste) en noms de code (ClientController, listeAction) => garantir que seules les méthodes désignées sont exécutables.

* Protection CSRF (Cross-Site Request Forgery)
    - **Objectif** : Empêcher un site tiers de forcer un utilisateur authentifié à exécuter des actions non souhaitées sur ton site.
    - **Règle** : Toute requête modifiante (POST, PUT, DELETE) doit impérativement contenir et valider un token CSRF.
    - **Principe** : Associer chaque formulaire à un jeton (token) unique, stocké en session et vérifié lors de la soumission.
      - Générer un jeton unique en session : `$_SESSION['csrf_token'] = bin2hex(random_bytes(32));`
      - Inclure le jeton dans les formulaires : `<input type="hidden" name="csrf_token" value="<?= $_SESSION['csrf_token'] ?>">`
      - Comparer le jeton à la réception du POST : `hash_equals($_SESSION['csrf_token'], $_POST['csrf_token'])`

### Serveur (Apache/ .htaccess)
* Dossier Public
    - Tous dossiers accessible publiquement doit avoir un fichier .htacces definissant les autorisations specifiques a ce dossier.

    - Empecher l'execution directe du code sans etre passe par index.php. Verification  d'une constante ou d'un token n'existant que dans index.php.

    - Réécriture d'URL
        - Forcer la réécriture d'URL vers index.php.
            ```
            RewriteEngine On, RewriteCond %{REQUEST_FILENAME} !-f, RewriteCond %{REQUEST_FILENAME} !-d, RewriteRule ^(.*)$ index.php [QSA,L]
            ```
    - Header de Sécurité
        ```
        X-Content-Type-Options "nosniff"
        X-Frame-Options "SAMEORIGIN"
        Referrer-Policy "strict-origin-when-cross-origin"
        ```
    - Restrictions d'accés 
        - Désactiver l'affichage des répertoires
            ```
            Options -Indexes
            ```
        - desactivation du suivi des liens symboliques
            ```
            Options +SymLinksIfOwnerMatch
            ```
        - interdiction d'acces aux fichiers cachés
            ```
            <FilesMatch "^\.">
                Require all denied
            </FilesMatch>
            ```
        - interdiction d'acces aux fichiers sensibles
            ```
            <FilesMatch "\.(bak|inc|orig|sql|tpl|yaml|yml|json|log|md|ini|conf|env)$">
                Require all denied
            </FilesMatch>
            ```
        - interdiction d'executer un script sauf index.php
            ```
            <FilesMatch "^(?!index\.php$).*\.php$">
                Require all denied
            </FilesMatch>
            ```
        - interdiction d'executer un script (dossier d'asset par exemple)
            ```
            <FilesMatch "\.(php|phtml|php3|php4|php5|phps|pht|exe|com|bat|sh)$">
                Require all denied
            </FilesMatch>
            ```
* Racine du projet
    - un fichier .htaccess contenant
        ```
        Require all denied
        ```

### Content Security Policy (CSP)

- **Rôle**: Header HTTP qui définit les sources de contenus autorisées (scripts, styles, images).

- **Sécurité** : Bloque l'exécution de scripts injectés (XSS) et les ressources non approuvées.

- Exemple strict : Header set Content-Security-Policy "default-src 'self'; script-src 'self'; style-src 'self'; object-src 'none';"
### Protection utilisateurs
* Accés
    - Vérifier les droits et permissions de l'utilisateur connecté avant d'exécuter la logique métier (protection contre l'accès non autorisé).
* Données
    - Validation des Données => S'assurer que les données reçues ($_POST, $_GET) sont complètes, conformes au type attendu et sécurisées (nettoyage / échappement)."
* Upload
    - vérification de l'extension
    - vérification du type MIME
    - renommage
    - stockage en dehors du dossier publique

### Divers
- empecher l'execution de phpinfo()
- empecher l'execution de la commande system
- ne jamais utiliser de directives Alias
