# Pr�sentation
Ce projet est un plugin pour Gramps qui doit permettre l'extraction et le stockage des pages d'archives correspondant aux anc�tres d'un arbre g�n�alogique.
En effet, avec la d�mocratisation des archives d�partementales en lignes, il est commun d'effectuer ses recherches int�gralement sur internet.
Pour la p�rennit� des recherches effectu�es, nombre de g�n�alogistes enregistrent les coordonn�es des informations consult�es (Type et num�ro d'acte, num�ro de page...), afin d'�tre en mesure d'y retourner par la suite. Ces �tapes, indispensables pour beaucoup, sont fortement d�pendantes de la disponibilit� des sites d'archives, dans l'imm�diat et sur le long terme.
Ce plugin permet simplement de conserver une copie, comme la prise de photos en salle d'archive, des documents concernant vos anc�tres.

## Mise en garde
L'utilisation d'un tel outil peut �tre contraire aux conditions d'utilisation des sites d'archives d�partementales. En tout �tat de cause, il incombe � chaque utilisateur de prendre connaissance de ces conditions d'utilisation, et de se r�f�rer aux archives utilis�es en cas de doute. 
En outre, l'utilisation du plugin n'est pas triviale, car tous les sites ne facilitent pas cette extraction. Il est souvent n�cessaire de mettre � jour le plugin pour avoir � sa disposition les derniers algorithmes d'extraction, les sites �tant modifi�s par leurs auteurs sans pr�avis.

**Aucune garantie n'est fournie quand au fonctionnement d'une extraction.**

## Appel � contribution
Le maintient des algorithmes d'extraction est un travail long �tant donn� le nombre de sites vis�s. Toute aide est la bienvenue, ce travail �tant plus facilement effectu� par les personnes disposant :
1. de recherches r�elles sur les sites concern�s, ce qui permet de balayer tous les types d'actes et de documents, et donc d'obtenir un algorithme le plus g�n�rique possible
2. de connaissance en d�veloppement informatique. Ce plugin est d�velopp� en Python, langage puissant � la fois adapt� aux d�butants et aux d�veloppeurs exp�riment�s.
Pour toute information, contactez moi : olivier [arob@se] coupelon.net

## Installation
L'installation du plugin revient � un simple copier/coller dans le dossier utilisateur de Gramps. Il faut donc avoir ex�cut� au moins une fois Gramps pour que ce dernier existe. Il contient un dossier plugins, dans lequel les fichiers *.py de ce projet doivent �tre copi�s.
Sous windows 7, le dossier se trouve g�n�ralement � l'emplacement : _C:\Users\<utilisateur>\AppData\Roaming\gramps\gramps34\plugins_.

## Utilisation du plugin
L'utilisation de ce plugin est complexe. En pratique, il n'existe pas actuellement de moyen standard pour enregistrer les informations n�cessaires � l'extraction des pages recherch�es. La convention adopt�e par le plugin est donc la suivante.

### Enregistrement pour chaque individu d'un lien vers la page
Pour associer une page d'acte � un individu, il est n�cessaire d'enregistrer une adresse internet correspondant � celle qui sera utilis�e par l'algorithme lors de l'extraction (voir figure ci-dessous). L'adresse de cette page peut parfois n�cessiter des outils suppl�mentaires, car les adresses recherch�es, qui permettent d'acc�der directement � la page d'acte qui nous int�resse, ne sont pas toujours expos�es directement par les sites web. C'est notamment le cas des sites d'archives qui ne comporte pas de liens 'permanents', qui ont pour fonction de retourner directement sur une page visit�e, une sorte de marque page. Les d�tails pour chaque site permettant d'enregistrer une adresse utilisable par le plugin sont donn�s dans la section 'Guide des archives couvertes par le plugin'.

![alt text](https://github.com/coupelon/gramps-dis/raw/master/images/gramps_saisie_site_internet.png "Saisie d'un site internet pour un individu, correspondant � l'extrait d'acte � conserver")

### Execution de l'extraction
Une fois les liens cr��s pour les individus, il faut ex�cuter le plugin qui va alors, pour chaque individu :
1. Explorer les liens internet disponibles
2. V�rifier que pour cette personne, ce lien et cette description, qu'un fichier n'existe pas d�j�
3. T�l�charger l'image de la page
4. Enregistrer cette image dans la galerie de cet indidu.

## Guide des archives couvertes par le plugin
La version actuelle (1.0.1 du 20/10/2013) couvre les sites d'archives d�partementales suivants.

### 12 Aveyron
Site : http://archives.aveyron.fr
Extraction du lien d'un acte : Une fois sur la page � conserver, il suffit de copier le lien permanent disponible en haut � droite :
![alt text](https://github.com/coupelon/gramps-dis/raw/master/images/permalien_ligeo.png "Lien permanent AD12")

### 43 Haute Loire
Site : http://www.archives43.fr
Note : Les administrateurs du site travaillent � l'ajout d'un lien permanent, ce qui devrait faciliter les op�rations.
Extraction du lien d'un acte : Pour trouver le lien permanent d'une page, il faut une fois sur cette derni�re cliquer sur le bouton d'impression du site. Une nouvelle fen�tre s'ouvre alors dans la navigateur, il faut copier l'adresse de cette page, g�n�ralement situ�e dans la barre d'adresse en haut de l'�cran.

### 48 Loz�re
Site : http://archives.lozere.fr
Extraction du lien d'un acte : Une fois sur la page � conserver, il suffit de copier le lien permanent disponible en haut � droite :
![alt text](https://github.com/coupelon/gramps-dis/raw/master/images/permalien_ligeo.png "Lien permanent AD48")

### 63 Puy-de-d�me
Site : http://www.archivesdepartementales.puydedome.fr
Extraction du lien d'un acte : Une fois sur la page � conserver, il suffit de copier le lien permanent disponible en haut � droite :
![alt text](https://github.com/coupelon/gramps-dis/raw/master/images/permalien_ligeo.png "Lien permanent AD63")

### 67 Bas-Rhin
Site : http://etat-civil.bas-rhin.fr/
Extraction du lien d'un acte : Une fois sur la page � conserver, il faut activer dans le navigateur web le mode d'analyse r�seau. Voir la section 'Analyse r�seau'. Il faut ensuite cliquer sur Imprimer, une adresse apparait alor dans l'analyseur r�seau, il faut copier cette adresse.

### 81 Tarn
Site : http://archives.tarn.fr/
Extraction du lien d'un acte : **l'extraction n'est pas encore fonctionnelle, mais en cours de d�veloppement.** Il faut tout d'abord s'enregistrer sur le site des archives du tarn, pour obtenir un login et mot de passe qui devront �tre renseign�s au lancement du plugin.

## Analyse r�seau
Le mode analyse r�seau permet aux navigateurs web d'exposer les op�rations qu'ils effectuent sur le r�seau de mani�re habituellement transparante pour l'utilisateur.

Pour l'activer sous Google Chrome il faut utiliser la combinaison de touches Ctrl + Maj + I. Apparait alors une zone/fen�tre dont l'ent�te poss�de de multiples onglets. Cliquer sur l'onglet R�seau (Network). Au fur et � mesure des pages visit�es sur internet, des liens vont appara�tre dans la liste de cette fen�tre. Il suffit de faire un clic droit sur un des liens et de cliquer sur 'Copier le lien' (Copy link address) pour sauvegarder l'adresse d'un acte. Pour que la liste soit id�alement courte, et ne contienne que la page recherch�e, il suffit d'ouvrir cette fen�tre au dernier moment et de la refermer entre chaque page.

![alt text](https://github.com/coupelon/gramps-dis/raw/master/images/chrome_copie_lien.png "Analyse des flux r�seau sous Chrome")

## Test du plugin

Le plugin, pour �tre test�, utilise une base de d�monstration disponible dans le dossier test de ce projet. Le choix d'un chemin alternatif pour le stockage des fichiers t�l�charg�s est support� par le plugin, il est donc conseill� de la modifier lors des tests dans le menu 'pr�f�rences' de Gramps.