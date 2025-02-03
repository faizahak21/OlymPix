NOM : HAKEM Faiza
DATE : 01/12/2024
INTITULE : Application de gestion de concours en ligne («OlymPix»)
SUJET : Concours de couture créative.
1.Nom du template Bootstrap choisi :
Front Office : https://startbootstrap.com/previews/creative
Back Office: https://startbootstrap.com/previews/sb-admin
2.URL de la dernière version de l'application hébergée sur le serveur de
production :
https://obiwan.univ-brest.fr/~e22210261/
3.Commandes pour la sauvegarde des fichiers de l'application Web :
Sous terminal Linux, pour sauvegarder une version V de l’application :
ssh faiza.hakem@vador-fs.univ-brest.fr
cd projet_isi
mkdir V_sauv
Dans un autre terminal :
ssh e22201443@obiwan.univ-brest.fr
cd V
scp -r ci/ faiza.hakem@vador-fs.univ-brest.fr:projet_isi/V_sauv
cd ..
mkdir V_copie
cp -r V/ci V_copie
Mise en ligne sur Gitlab :
cd V
git init .
git status
git add .
git status
git commit -m «V de l’appli web»
git config faiza.hakem
git config e22210261@etudiant.univ-brest.fr
git branch V
got checkout V
git remote add gitlab https://gitlab-depinfo.univ-brest.fr/e22210261/
git push gitlab V4. Rappel des comptes créés pour tester l'application :
Organisateur 1: organisateur@OlymPix.com
mot de passe : org24*PMYLO
Organisateur2 : organisateur1@olympix.fr
mot de passe : org25*CLMPM
Membre du jury : akhedimZohra4@gmail.com
Mot de passe : @Q3v$K9r^F2w*R8t
Un autre membre du jury : khDahouia21@gmail.com
Mot de passe : G7x!9nLm&8Qk@YzP
Une candidature : code Inscription : XmnOp02qghytrPazemc9
Code Candidat : C1vcLdhe
Une autre candidature : Code inscription : IbcMc14sdfhklSqwmlk1
Code candidat : N4cdKhdu
5. Court descriptif de la version en ligne (V1, V2 ) :
Version 1 (Sprint 1)
Cette version offre une interface publique où les visiteurs peuvent consulter les dernières actualités,
la liste des concours (passés, en cours, ou à venir), ainsi que les détails d'une candidature et ses
documents associés.
Dans la partie privée, les membres du jury et les administrateurs peuvent accéder aux concours qui
leur sont assignés ou à l'ensemble des concours, respectivement. Chaque utilisateur connecté peut
également consulter les informations de son compte et modifier son mot de passe. Un
administrateur peut gérer les profils utilisateurs en créant de nouveaux comptes. Enfin, les candidats
peuvent soumettre et supprimer leurs candidatures via un formulaire dédié.
Version 2 (Sprint 2)
Cette version introduit une galerie des candidatures pré-sélectionnées pour un concours en
particulier, accessible au public et aux jurys.
Du côté administrateur, il est désormais possible d’ajouter ou de supprimer des concours, ainsi que
de gérer les inscriptions des candidats (validation et enregistrement dans la base de données).
L’administrateur peut également afficher et organiser les candidatures par état, gérer la phase de
pré-sélection, la finale, et publier le palmarès.
Pour les candidats, cette version propose une interface complète pour soumettre ou annuler leurs
candidatures.
Nom de la base de données utilisée pour l'application : e22210261_db1
Court descriptif des trigger(s), fonction(s), procédure(s), vue(s) (...) créés en rapport
avec l'application Web et utilisés car fonctionnels :5.
1) Vues
• Vue des organisateurs de concours : Liste les noms, prénoms, et identifiants des
administrateurs responsables de chaque concours (organisateurs_concours).
• Vue des jurys et spécialités : Affiche les jurys des concours avec leurs domaines expertise
pour chaque concours (vue_jury_concours).
• Vue des discussions et messages : Regroupe les discussions et messages associés à chaque
concours, avec l'état des messages (vue_discussions_concours).
• Vue des catégories des concours : Montre les concours et leurs catégories respectives
(concours_categories).
2) Fonctions
• Nombre total de candidats par concours : Retourne le nombre total de candidats pour un
concours spécifique (nombre_candidats).
• Catégorie par ID de candidature : Fournit le nom de la catégorie associée à une
candidature (nom_categorie_candidature).
• Liste des jurys : Renvoie les noms et les domaines d’expertise des jurys pour un concours
donné (donner_jury).
• Liste des catégories : Affiche les catégories associées à un concours
(donner_categorie).
• Organisateurs d’un concours : Liste les organisateurs d’un concours spécifique
(donner_org).
• Dates intermédiaires d’un concours : Retourne les principales dates d’un concours
(candidature, pré-sélection, sélection) (donner_date_inter).
• Phase actuelle d’un concours : Indique la phase actuelle d’un concours en fonction de la
date (donner_phase).
• ID de l’organisateur : Retourne l’identifiant de l’organisateur d’un concours donné
(id_organisateur).
• Dernier concours ajouté : Renvoie l’identifiant du dernier concours inséré dans la table des
concours (denier_concours).
3) Procédures
• Insertion d’actualité : Insère une actualité liée au dernier concours créé avec un texte
descriptif incluant le nom du concours, sa date de début et un texte introductif
(annoncer_concours).• Désactivation des messages : Met à jour l’état des messages associés à un concours
spécifique pour les désactiver (desactiver_messages).
• Insertion d’actualité par concours : Insère une actualité pour un concours donné en
utilisant son ID et l’information de l’organisateur (insere_act).
4) Déclencheurs (Triggers)
• Vérification de doublons : Empêche l’insertion d’une candidature si le même candidat est
déjà inscrit au concours (doublon_candidature).
• Mise à jour des candidatures : Met automatiquement à jour l’état des candidatures d’un
concours si celui-ci est terminé (etat_candidature).
6. Procédure à suivre pour installer l'application Web sur un serveur :
Afin de pouvoir au mieux profiter des services proposés par notre application, nous vous
conseillons d’installer Code Igniter version 4.5.5. Voici la procédure à suivre :
1. Sous Linux, dans un terminal de commande, connectez vous à votre machine serveur en ssh.
2. Allez sur https://codeigniter.com/download afin de récupérer le lien de téléchargement de la
version 4.5.5 de CodeIgniter (et non pas une version ultérieur, cela pouvant entraîner des
erreurs entre votre machine et l’application).
3. Créez le répertoire où vous voulez installer l’application web, puis exécutez les commandes
suivantes :
wget lien vers le téléchargement de CodeIgniter (nommé v4.5.5)
unzip v4.5.5
mv codeigniter4-framework-f5844cb/* ./
chmod -R g+w writable
4. Supprimez le répertoire dézippé.
5. Mettez à jour le fichier App.php en ajoutant l’URL de base de votre site.
6. Testez afin de bien vérifier le bon fonctionnement de l’application.
De plus, il est conseillé d’installer la base de données fournie avec les fichiers d’application, afin de
servir de fondation solide pour votre propre utilisation. Voici comment procéder pour télécharger la
base de donnée :
1. Ouvrez votre Système de Gestion de Base de Données (SGBD).
2. Vérifiez que vous avez un emplacement de base de donnée libre.
3. Importez la base de donnée en vous assurant de la bonne mise en forme.
7.
Titre : Plan de tests de validation de la version 1 (V1) de
l’application Web «OlymPix»
Date de création du plan de tests :
01/09/24Dernière date de modification du plan de tests : 13/09/24
Version du plan de tests : V2
Auteur : V.MARC
Sprint : Sprint 1
Date de passage des tests :
02/12/24
URL de l’application Web testée : https://obiwan-2024.univ-brest.fr/~e22210261/
Nom du développeur de l’application Web testée : Faiza Hakem
Nom du testeur : Kerzil Hugo
Opération
Résultat attendu
Résultat du test
+
commentaires
Saisie de l’URL du site Web Affichage correct de la page d’accueil Test Ok
dans la barre d’adresse du du site Web sur laquelle on voit :
navigateur Web.
• les actualités publiées, s’il y en
a, ou dans le cas contraire, un
message « Aucune actualité
pour le moment »,
• un hyperlien / bouton de
connexion.
Appui sur le bouton ou
l’hyperlien de connexion.Une page de connexion avec 2
Test Ok
champs de saisie pour les identifiants
s’affiche.
Appui sur le bouton / la
rubrique « Suivi de
candidature » dans le menu
accessible à tous les
visiteurs.Affichage correct de la page du
Test Ok
formulaire de saisie des 2 codes
(identification / inscription) présentant
2 champs de saisie et un bouton
« Valider ».
Saisie, dans le formulaire de Le récapitulatif de la candidature
saisie des codes d’une
choisie s’affiche correctement sur la
candidature, de 2 codes
page (avec les données générales et
présents dans la base de
les documents associés à la
données.
candidature) ainsi qu’un bouton
« supprimer ma candidature ».Test Ok
Saisie de 2 codes NON
présents dans la base de
données.Un message d’erreur s’affiche
« Code(s) erroné(s), aucune
candidature (/inscription) trouvée ! »
et l’utilisateur est redirigé vers le
formulaire.Test Ok
Appui sur le bouton
« Valider » pour voir la
candidature alors que les
champs de saisie ne sont
pas remplis.Un message d’erreur « Veuillez
remplir le formulaire s’affiche » et
l’utilisateur est redirigé vers le
formulaire.Test Ok
Sur la page affichant le
récapitulatif d’une
candidature, appui sur le
bouton « Supprimer ».Un message « Candidature
Test Ok
supprimée » s’affiche puis l’utilisateur
est redirigé vers le formulaire de suivi
de candidature. Il n’est plus possibled’afficher le récapitulatif de la
candidature supprimée !
Saisie, dans le formulaire de La page d’accueil de l’espace privé
connexion, d’un identifiant des membre du jury s’affiche avec le
et d’un mot de passe
menu visible. Un message de
(caché) d’un membre du jury bienvenue s’adresse au membre du
présents dans la base de
jury connecté. Il est impossible pour
données.
un administrateur connecté d’afficher
une des pages de l’espace privé des
membres du jury en saisissant
directement son URL dans la barre
d’adresse du navigateur Web.Test Ok
Saisie d’un identifiant et d’un Un message d’erreur s’affiche
mot de passe NON présents "Identifiants erronés ou inexistants !"
dans la base de données.
puis la page de connexion est ré-
affichée pour permettre une nouvelle
saisie.Test Ok
Dans l’espace membre du
jury, le membre du jury
connecté clique sur la
rubrique « mon profil ».Le profil du membre du jury connecté Test Ok
s’affiche dans la page (ou dans un
formulaire pré-rempli).
Dans la rubrique « mon
profil », le membre du jury
modifie dans le formulaire
une ou plusieurs données
qui le concernent, appuie
sur le bouton « Valider »
puis ré-affiche son profil.Le profil du membre du jury connecté Test Ok
s’affiche dans la page. Les
modifications effectuées ont été
prises en compte.
Dans la rubrique « mon
profil », le membre du jury
appuie sur le bouton
« Valider » alors que le
formulaire est vide.Un message d’erreur s’affiche
« Champ de saisie vide » et
l’utilisateur est redirigé vers le
formulaire (ou la rubrique « mon
profil »).
testOk
Dans la rubrique « mon
profil », le membre du jury
appuie sur le bouton
« Valider » alors que les 2
saisies du mot de passe ne
sont pas identiques.Un message d’erreur s’affiche
« Confirmation du mot de passe
erronée, Veuillez réessayer » et
l’utilisateur est redirigé vers le
formulaire (ou la rubrique « mon
profil »).
Test Ok
Le membre du jury appuie L’utilisateur est redirigé vers le
sur le bouton « Annuler » du formulaire (ou la rubrique « mon
formulaire de modification
profil ») de son espace privé.
du profil.
Test Ok
Dans l’espace jury, le
membre du jury connecté
clique dans le menu sur la
rubrique « Concours ».Test Ok
Tous les concours auxquels il est
associé classés selon leur date de
début (ou leur phase actuelle)
s’affichent dans un tableau
récapitulatif.Dans l’espace jury, le
La session se ferme, l’utilisateur est
membre du jury connecté
redirigé vers la page d’accueil (Front
clique sur « Déconnexion ». Office) de l’application Web et il est
impossible d’afficher une des pages
de l’espace privé jury en saisissant
directement son URL dans la barre
d’adresse du navigateur Web.
Test Ok
Saisie, dans le formulaire de La page d’accueil de l’espace privé
Test Ok
connexion, d’un identifiant des administrateurs s’affiche avec le
et d’un mot de passe
menu visible. Un message de
(caché) d’un administrateur bienvenue s’adresse à
présents dans la base de
l’administrateur connecté. Il est
données.
impossible pour un membre du jury
connecté d’afficher une des pages de
l’espace privé des administrateurs en
saisissant directement son URL dans
la barre d’adresse du navigateur Web.
Saisie d’un identifiant et d’un Un message d’erreur s’affiche
mot de passe NON présents "Identifiants erronés ou inexistants !"
dans la base de données.
puis la page de connexion est ré-
affichée pour permettre une nouvelle
saisie.Test Ok
Dans l’espace
Le profil de l’administrateur connecté
administrateur,
s’affiche dans la page (ou dans un
l’administrateur connecté
formulaire pré-rempli).
clique sur la rubrique « mon
profil ».Test Ok
Dans la rubrique « mon
profil », l’administrateur
modifie dans le formulaire
une ou plusieurs données
qui le concernent, appuie
sur le bouton « Valider »
puis ré-affiche son profil.Test Ok
Le profil de l’administrateur connecté
s’affiche dans la page. Les
modifications effectuées ont été
prises en compte.
Dans la rubrique « mon
L’utilisateur est redirigé vers le
profil », l’administrateur
formulaire (ou la rubrique « mon
appuie sur le bouton
profil ») de son espace privé.
« Annuler » du formulaire de
modification du profil.Test Ok
Dans la rubrique « mon
profil », l’administrateur
appuie sur le bouton
« Valider » alors que le
formulaire est vide.Un message d’erreur s’affiche
« Champ de saisie vide » et
l’utilisateur est redirigé vers le
formulaire (ou la rubrique « mon
profil »).Test Ok
Dans la rubrique « mon
profil », l’administrateur
appuie sur le bouton
« Valider » alors que les 2
saisies du mot de passe neUn message d’erreur s’affiche
« Confirmation du mot de passe
erronée, Veuillez réessayer » et
l’utilisateur est redirigé vers le
formulaire (ou la rubrique « monTest Oksont pas identiques.profil »).
Dans l’espace
administrateur,
l’administrateur connecté
clique dans le menu sur la
rubrique « Comptes ».Le tableau de tous les profils s’affiche Test Ok
sur la page.
Dans la rubrique
« Comptes »,
l’administrateur connecté
clique sur « Ajouter un
compte ».Le formulaire d’ajout d’un compte
s’affiche correctement sur la page.
Saisie, dans le formulaire
Un message « Compte créé »
d’ajout de compte, de toutes s’affiche et le compte (+ profil)
les données (avec choix du nouvellement créé (et complet)
type de compte / profil à
apparaît bien dans la liste des
créer, c’est à dire
comptes ré-affichés.
administrateur / membre du
jury à faire via une liste
déroulante) et appui sur le
bouton « Créer compte » (ou
« Valider »).
Test Ok
Test Ok mais ne ré-
affiche pas la liste
des comptes
Dans la page du formulaire
d’ajout d’un compte, appui
sur le bouton de validation
alors que tous les champs
ne sont pas remplis.Un message d’erreur s’affiche
Test Ok
« Veuillez remplir les champs » et
l’utilisateur connecté est redirigé vers
le formulaire.
Dans la page du formulaire
d’ajout d’un compte, appui
sur le bouton de validation
alors que les 2 mots de
passe saisis ne sont pas
identiques.Un message d’erreur s’affiche : « les
2 mots de passe saisis sont
différents ! » et l’utilisateur connecté
est redirigé vers le formulaire.
Dans la page du formulaire
d’ajout d’un compte,
l’administrateur connecté
essaie de créer à nouveau
un compte (/ un profil) qui
existe déjà !Un message d’erreur s’affiche : « Le Test Ok
compte ne peut pas être créé ! » et
l’utilisateur connecté est redirigé vers
le formulaire.
Dans l’espace
administrateur,
l’administrateur connecté
clique dans le menu sur la
rubrique « Concours ».Tous les concours classés selon leur Test Ok
date de début (ou leur phase actuelle)
s’affichent dans un tableau
récapitulatif.
Dans l’espace
administrateur,
l’administrateur connecté
clique sur « Déconnexion ».La session se ferme, l’utilisateur est
Test Ok
redirigé vers la page d’accueil (Front
Office) de l’application Web et il est
impossible d’afficher une des pages
de l’espace privé des administrateurs
en saisissant directement son URL
Test Okdans la barre d’adresse du navigateur
Web.
Un administrateur connecté
ou un visiteur non connecté
essaie d'accéder
directement à une page de
l’espace privé jury (en
saisissant son URL dans
son navigateur Web).L’utilisateur est redirigé vers la page
d’accueil (ou page de connexion) du
site Web.Test Ok
Un membre du jury
connecté ou un visiteur non
connecté essaie d'accéder
directement à une page de
l'espace administrateur (en
saisissant l'URL de la page
Web dans son navigateur
Web).L’utilisateur est redirigé vers la page
d’accueil (ou page de connexion) du
site Web.Erreur page
codeIgniter
