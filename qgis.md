# Tutoriel QGIS : Préparation et Analyse des Couches Géographiques

**Conseil** : Renommer clairement les couches pour une meilleure lisibilité.
              Pour chercher les fonctions utilisées dans ce tutoriel, faire CTRL + K pour rechercher

## Étape 1 : Vérification et Uniformisation des Systèmes de Projection

0. Importer les couches shapefiles, Typo_CLC.dbf et le mnt.asc du dossier couches

### Projection des Couches Existantes

1. **Couche CLC 2018 Pilat** 
   - Système de projection : WGS 84
   - Objectif : Uniformiser en Lambert 93 pour un travail à l'échelle française
   - Méthode : Utiliser la fonction "Enregistrer sous" pour reprojeter en faisant un clique droit sur la couche
   
![Image](images/image1.png)

2. **Couche des Limites Administratives**
   - Problème initial : Absence de projection correcte
  ![Image](images/image2.png) 
   - Solution : Utiliser "Assign Projection" dans QGIS
     * Correction : La couche était en Lambert II (EPSG:27572)
     ![Image](media/image4.png)
     * Reprojeter correctement en Lambert 93 (EPSG:2154)
     ![Image](media/image5.png)
     ![Image](media/image6.png)
     Cliquer sur le premier choix car cela semble ne pas avoir      d'importance sur notre sujet d'étude

## Étape 2 : Préparation des Données

### Mise à Jour du Système de Référence Spatial (CRS)
- Utiliser la fonction "Enregistrer sous" pour mettre à jour le CRS de la couche MNT
![Image](media/image7.png)
### Création d'un Buffer

0. faire une selection des commuens suivante :

1.  • Colombier
    • Doizieux
    • Graix
    • La Valla-en-Gier
    • Le Bessat
    • Pélussin
    • Roisey
    • Saint-Appolinard
    • Thélis-la-Combe
    • Véranne

Pour le faire , faite clique droit sur la couche limites adminstrative et aller dans table attributaire
![Image](image/select_qgis.png)
une fois dedans, selectionner sur le coter les communes ayant le même nom.
Ensuite faite un clic droit sur le nom de la couche puis faite exporter les objets selectionné et sauvegarder votre couche
3. Créer un buffer de 500 mètres à partir de la couche des limites administratives du crêt du pilat
![Image](media/image.png)
4. Options importantes :
   - Cocher la case "Dissolve" pour obtenir un buffer unifié
   - Éviter les zones fragmentées
5. Sauvegarder la couche
![Image](media/image9.png)
## Étape 3 : Analyse Altimétrique

### Calcul des Altitudes Supérieures à 1300m
- Utiliser la calculatrice raster de QGIS
- Expression : `("mtn_pilat@1" > 1300) * 1`
  * Sélectionner la couche MNT en entrée
  * Filtrer les altitudes > 1300m
  * Générer une couche binaire (0/1)
![Image](media/image14.png)
- Résultat obtenu devrait ressembler à cela:
![Image](media/image15.png)
- Sauvegarder la couche
![Image](media/image16.png)

### Conversion en Polygones
- Utiliser la fonction "Polygoniser" pour transformer le raster
![Image](media/image17.png)
- Nommer la nouvelle couche : "mtn_pilat_1300m"
- Sauvegarder la couche
![Image](media/image18.png)
- Appliquer un style Jenks natural avec deux classes pour la visualisation
![Image](media/image19.png)

## Étape 4 : Analyse des Pentes

### Calcul de la Couche des Pentes
- Utiliser "Raster Analysis Slope" dans QGIS
![Image](media/image20.png)
- utiliser la calculatrice raster et entrez en calcule (mtn_pilat_slope@1 < 4) * 1 
![Image](media/image21.png)
- Vectoriser le raster
- Exemple de couche : "pente_4_degre_pilat"
- Appliquer une classification Jenks en 2 classes
![Image](media/image24.png)

## Étape 5 : Jointure et Stylisation

### Jointure avec la Couche Typo_CLC
- clique droit sur la couche CLC_2018_Pilat puis propriété et aller dans jointure puis fait une jointure avec la couche TYPE_CLC entre le code_18 et le code_06
![Image](media/image_jointure.png)
- Télécharger les fichiers de style depuis data.gouv.fr
- Charger le style .qml dans QGIS avec le bouton style puis cliquer "load style"
![Image](media/image27.png)
![Image](media/image28.png)
- Appliquer la stylisation personnalisée
![Image](media/image29.png)

- couper les couches avec le buffer fait sur la couche des limites du crêt. Utiliser la fonction de batch pour aller plus vite.
![Image](image/batch.png)
 
  
## Étape 6 : Création de la Mise en Page

### Préparation de la Carte
1. Aller dans "Projet" > "Nouvelle mise en page"
![Image](images/image30.png)
2. Ajouter les éléments :
![Image](images/37.png)
   - Carte
   - Légende
   - Titre(label)
   - Sources/ Auteur(label)
   - Flèche du Nord
   - Échelle

### Paramétrage de la Légende
![Image](media/image31.png)
- Désactiver la mise à jour automatique
- Cocher "Afficher uniquement les éléments dans la carte liée"
![Image](media/image32.png)
- Choisir un format A3 pour plus d'espace en cliquant sur l'espace vide de la mise en page et en allant sur les propriétés à droite
![Image](media/image33.png)
- Pour changer le texte des couches, double-cliquer sur le nom de la couche puis écrire le nom que vous souhaitez dans la case
![Image](images/image35.png)

### Paramétrage de titre et des sources
- En allant sur les propriétés à droite, en horizontale et verticale, cliquer centrer
![Image](images/image28.png)


### Finalisation
- Exporter la carte en image
- Enregistrer dans le dossier souhaité
![Image](image/pilat_mont.png)

