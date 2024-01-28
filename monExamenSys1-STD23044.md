# EXAMEN-SYS1-WARCHALL-STD23044
## Training: Warchall - The Beginning 

1. **Level 0 :**
    - Direction : `cd /home/level/00_welcome`
    - Commande : `cat`
  
2. **Level 1 :**
    - Direction : `cd /home/level/01_choice_tree`
    - Actions :
        - Regarder dans les dossiers : `ls -R`
        - Aller à : `cd ./blue/hats/grey/solution/patience`
        - Voir le mot de passe : `cat SOLUTION.txt`

3. **Level 2 :**
    - Direction : `cd /home/level/02/.porb`
    - Commande : `cat .solution`

4. **Level 3 :**
    - Direction : `cd /home/level/03`
    - Options :
        - Ouvrir `.bash_history` ou aller à `.shared`
    - Commande : `cat .bash_history`

5. **Level 4 :**
    - Direction : `cd /home/level/04_kwisatz`
    - Instructions du README dans le directory est d' aller dans le répertoire personnel : `cd ~`
    - Actions :
        - Explorer : `ls -R`
        - Modifier les permissions : `chmod 700 README2.md`
        - Ouvrir le fichier : `cat README2.md`

6. **Level 5 :**
    - Direction : `cd /home/level/05_privacy`
    - Actions :
        - Voir le contenu : `ls -al`
        - Ouvrir le README : `cat README`


## Choose your Path [level10]:
**1-demarche :**
  - Direction : `cd /home/level/10_Choose_your_Path`
    
  - Actions : 
      - voir le contenu : `ls -al`
      - Excecution du fichiers : `./charp  "solution.txt; cat solution.txt > ~/solutionPath1.txt` 
      - On a changé de directory : `cd ~` (allé dans notre repertoire personnelle pour voir les contenus transferer
      - voir le contenu : `ls`
      - affichier le contenus du fichiers solutionPath1.txt que nous avons créé : `cat solutionPath1.txt`

**2-explication :**  
  - constation : on a put constaté que `charp` est un fichier de qui contient des textes avec des symboles,
    c'est à dire des commandes  qui permet de compter les lignes, telles que wc (comptage de mots, de lignes, etc. dans un fichier).

  - details sur `./charp "solution.txt; cat solution.txt > ~/solutionPath1.txt` :
      - `./charp` : l'exécution du script "charp" dans le répertoire actuel. Le point "." représente le répertoire actuel,
        et "charp" est le nom du programme ou script à exécuter.
        
      - `"solution.txt; cat solution.txt > ~/solutionPath1.txt"`: C'est l'argument passé au programme `charp`. Il y a deux commandes ici séparées par le point-virgule `;`,
        car d'apres ce que nous avons vu dans le code source du level dans l'enonncé du challenge à sa page, la fonction contenait 2 argument que nous allons fournir.
        Et la logique qui nous avons eu en tete pour faire sortir notre solution a ete de cette manière (la methode dans j'ai utilisé)
        - `solution.txt`: Il s'agit du premier morceau de la commande. Une entrée pour le programme `charp`.
        - `cat solution.txt > ~/solutionPath1.txt` : C'est le deuxième morceau de la commande.
        Cela utilise la commande `cat` pour afficher le contenu du fichier `solution.txt`et
        le redirige ``>`` vers un nouveau fichier appelé `solutionPath1.txt` dans notre répertoire personnel `~`.

        
## Warchall : Live LFI & RFI [level 14 & 15]
  **I-Demarche :**
  - (1) Ouvrir le lien de la page du challenge en appuiant sur ` Live LFI ` mentionner dans l'énonncer [URL:`https://lfi.warchall.net/`]
  - (2) Une fois sur la page `cliquer` sur le drapeau `Anglais(UK)`
  - (3) L'URL de la page a changé en : `https://lfi.warchall.net/index.php?lang=en`

  - (4) avec une tentative d'injerctions de fichier locaux(LFI), et des notions de php filter, en s'y est pris directement comme suite pour : (modifiant l'URL)
      - `URL : https://lfi.warchall.net/index.php?lang=php://filter/convert.base64-encode/resource=solution.php`
      **details :**
      - `https://lfi.warchall.net/index.php?lang=` : C'est la base de l'URL.
      - `php://filter/convert.base64-encode/resource=` : C'est la partie vulnérable de l'URL. Tentative d'exploitation d'une LFI en utilisant le protocole `php://filter`
        pour appliquer une "conversion Base64" à la ressource spécifiée. 
      - `filter/convert.base64-encode/resource=` : Utilisation de la fonction de filtre PHP pour convertir le contenu du ressource en Base64.
      - `solution.php` : C'est le fichier ciblé de notre attaque LFI.

  - (5) Obtention du code base64 : `PGh0bWw+Cjxib2R5Pgo8cHJlIHN0eWxlPSJjb2xvcjojMDAwOy.......`

  - (6) Decodage du code par un decodeur base64 en ligne : 
      **Actions :**
      - copie du code
      - collage du code dans le prompt du decodeur
      - decode
      - obtention de la "solution" en code html avec une petite section de php

  **II-Notion approfondie :**
  - (1) php filter avec LFI
  - (2) code base64
  - (3) decodage base64

