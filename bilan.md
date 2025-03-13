# Bilan comparatif d'ArcGIS Pro et QGIS

## QGIS
- **Reprojection** : La gestion des systèmes de coordonnées présentait des difficultés, particulièrement pour le Modèle Numérique de Terrain (MNT). La fonction "Assigner un système de référence" a montré des limitations, potentiellement liées à la version 3.40 utilisée sous environnement Linux.
- **Interface de composition** : La mise en page cartographique s'est révélée intuitive et accessible, offrant un avantage notable par rapport à ArcGIS Pro dans ce domaine.

## ArcGIS Pro
- **Gestion des projections** : Le processus de correction et d'harmonisation des systèmes de coordonnées s'est avéré particulièrement efficace, rapide et fiable.
- **Symbolisation thématique** : Pour la représentation de Corine Land Cover, QGIS bénéficiait d'un fichier .qml préconfiguré disponible sur data.gouv.fr, alors qu'ArcGIS Pro ne proposait pas de fichier .lyr équivalent. La création manuelle d'une symbologie appropriée a donc été nécessaire avant de pouvoir générer un style .lyr réutilisable.
- **Composition cartographique** : L'élaboration des mises en page s'est révélée plus complexe, notamment concernant l'intégration et la manipulation de texte dynamique. Les mécanismes d'ajustement typographique manquent de fluidité comparativement à QGIS.

## Points d'équivalence
- **Analyse spatiale** : Les fonctionnalités d'analyse de pente et les calculatrices raster ont démontré des performances similaires dans les deux logiciels, ne permettant pas d'établir une distinction significative sur ces aspects.

## Conclusion
Contrairement aux attentes initiales, ArcGIS Pro s'est distingué par une expérience utilisateur globalement plus satisfaisante, offrant un environnement de travail plus fluide malgré quelques limitations en matière de mise en page cartographique.
