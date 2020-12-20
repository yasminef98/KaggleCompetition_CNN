# "Histopathologic Cancer Detection"
Identifier les tissus métastatiques dans les scans histopathologiques des sections de ganglions lymphatiques
![](header.png)

## Contexte du projet : 
Créer un  algorithme permettant d'identifier la présence de  cancers métastatiques à partir d’images histologiques.
Les images sont obtenues à partir  d'examen microscopique d'une biopsie chirurgical qui est traité et fixé sur des lames de verre. Pour visualiser les différents composants du tissu sous un microscope, les coupes sont teintées avec de l’hématéine (teint noyau bleu, violet très foncée) et l’éosine colore le cytoplasme en rose).

## Métrique utilisée : Courbe ROC-AUC
Mesure de performance pour les problèmes de classification : mesure la capacité du modèle à distinguer les classes.

### Courbe ROC

Une courbe ROC (receiver operating characteristic) est un graphique représentant les performances d'un modèle de classification pour tous les seuils de classification. Cette courbe trace le taux de vrais positifs en fonction du taux de faux positifs :
Vrai positive, vrai négative, faux positif, faux negatif calculés à partir de la matrice de confusion :

![](matrice_confusion.png)

* Taux de vrais positifs (TVP)= > sensibilité

  Sensibilité = (vrai positif)/(vra positifs+faux negatifs)
*	Taux de faux positifs => 1- specificité

  TFP= faux positifs/(faux positifs+vrai negatifs)
  
En médecine, la sensibilité d'un test diagnostic est ainsi sa capacité à détecter un maximum de malades (c'est-à-dire à avoir le moins de faux négatifs), tandis que la spécificité de ce test est sa capacité à ne détecter que les malades (avoir le moins de faux positifs). Une courbe ROC trace les valeurs TVP et TFP pour différents seuils de classification. Diminuer la valeur du seuil de classification permet de classer plus d'éléments comme positifs, ce qui augmente le nombre de faux positifs et de vrais positifs. La figure ci-dessous représente une courbe ROC classique. (le modèle sera performant pour deceler les cs positifs. L’interet dans ce cas c’est que le modèle aura moins de chanche de classer des images cancereurses comme non cancereuses. Problème : si un cas est négétifs, il risquera d’etre classé comme positifs( sera en ralité un faux positifs) 

![](roc_auc1.png)
Avec une Ric_Auc de cette forme (AUC =1), alors le modèle distingue parfaitement les classes positives et negatives.

![](roc_auc2.png)
Lorsque AUC = 0.5, le classificateur prédit une classe aléatoirement 

Ainsi, plus la valeur AUC d'un classificateur est élevée, meilleure est sa capacité à faire la distinction entre les classes positives et négatives.
Interet d’utiliser cette métrique pour ce sujet : 
Une courbe ROC trace les valeurs TVP et TFP pour différents seuils de classification. Diminuer la valeur du seuil de classification permet de classer plus d'éléments comme positifs, ce qui augmente le nombre de faux positifs et de vrais positifs. La figure ci-dessous représente une courbe ROC classique. (le modèle sera performant pour deceler les cs positifs. L’interet dans ce cas c’est que le modèle aura moins de chanche de classer des images cancereurses comme non cancereuses. Problème : si un cas est négétifs, il risquera d’etre classé comme positifs( sera en ralité un faux
La Roc-AUc peut elle etre pour tous les modèles binaires ?
•	à ne pas utiliser c'est l'echelles dans notre jeu de données est important dans l'interprétation
•	Pas utlisale dans le cas ou l'écart entre faux positifs et faux negatifs est important et qu'il est souhaitable de minimiser l'un des types d'erreur de classification

## Optimisation Adam
Méthode d'optimisation stochastique : technique mettant en œuvre un taux d'apprentissage adaptatif distinct pour chaque paramètre
Les paramètres qui recevraient normalement des mises à jour plus petites ou moins fréquentes reçoivent des mises à jour plus importantes avec Adam (l'inverse est également vrai). Cela accélère l'apprentissage dans les cas où les taux d'apprentissage appropriés varient selon les paramètres. Par exemple, dans les réseaux profonds, les gradients peuvent devenir petits aux premières couches et il est judicieux d'augmenter les taux d'apprentissage pour les paramètres correspondants. Un autre avantage de cette approche est que, comme les taux d'apprentissage sont ajustés automatiquement, le réglage manuel devient moins important. 




