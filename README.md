# Reconnaissance visuelle pour le suivi d’objets

*Projet 2A ENSEA  · 2026–2027*

Nous développons une caméra motorisée capable de repérer un objet dans le flux vidéo et de s’orienter automatiquement pour le maintenir près du centre de l’image. Le système combine vision par ordinateur, commande et intégration embarquée sur une **NVIDIA Jetson Nano**. Le principal défi est de réagir assez vite aux déplacements de l’objet tout en limitant les oscillations de la caméra.

<!-- Photo d’ouverture
![Vue d’ensemble du prototype avec la Jetson Nano et la caméra motorisée](docs/images/prototype.jpg)
-->

## Fonctionnement

1. **Acquérir l’image.** La caméra transmet son flux vidéo à la Jetson Nano.
2. **Localiser et suivre l’objet.** Le traitement d’image estime le centre de l’objet sélectionné et cherche à retrouver le même objet d’une image à l’autre.
3. **Calculer la correction.** Le programme mesure en pixels l’écart horizontal et vertical entre le centre de l’objet et le centre de l’image.
4. **Réorienter la caméra.** Deux servomoteurs corrigent le pointage horizontal (*pan*) et vertical (*tilt*). L’image suivante permet de mesurer l’effet de la correction et d’ajuster la commande.

Par exemple, si l’objet se déplace vers la droite de l’image, la caméra pivote vers la droite pour le ramener vers le centre.


<!-- Capture du suivi
![Capture du flux vidéo avec l’objet encadré et le centre de l’image repéré](docs/images/detection.png)
-->

## Matériel

| Élément | Rôle |
| --- | --- |
| NVIDIA Jetson Nano | Traiter le flux vidéo et calculer les corrections d’orientation |
| Caméra | Acquérir les images de la scène |
| Support pan-tilt | Permettre les rotations horizontale et verticale de la caméra |
| Deux servomoteurs | Orienter la caméra selon les consignes de commande |

<img width="1600" height="1200" alt="image" src="https://github.com/user-attachments/assets/4299d2fe-0cb5-4b6e-a84d-c306368a3a6b" />

<img width="1600" height="1200" alt="image" src="https://github.com/user-attachments/assets/d0aad480-4d24-4f9c-841f-eece649db1f1" />

**Figure 1 — Détail du support motorisé montrant les deux axes de rotation.**

## Démonstration et validation

La démonstration prévue consiste à déplacer l’objet horizontalement puis verticalement pour observer le recentrage de la caméra. Un second essai consiste à sortir brièvement l’objet du champ, puis à le réintroduire pour observer la reprise du suivi.

| Indicateur | Mesure prévue |
| --- | --- |
| Erreur de centrage | Écart entre le centre de l’objet et celui de l’image, en pixels |
| Cadence de traitement | Nombre d’images traitées par seconde sur la Jetson Nano |
| Temps de réponse | Délai entre un déplacement de l’objet et le début de la correction |

<!-- Ajouter ici un lien vers la vidéo de démonstration lorsqu’elle est disponible. -->

## Équipe et encadrement

Projet réalisé en groupe à l’ENSEA, **sous l’encadrement de M. Abed-Elhak Kasbari.**

**Amel BOUDIEB, Mahawa NDIAYE, Sara REGUEMALI**
