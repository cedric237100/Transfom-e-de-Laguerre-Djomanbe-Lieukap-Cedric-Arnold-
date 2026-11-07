# laguerreRC

Package R : identification d'un circuit RC à trois étages avec les fonctions de Laguerre.
Résultat de référence : 1er ordre 51,7 %, Laguerre (N = 5, p = 1) 98,82 %, meilleur p ≈ 0,83.

## Installation (RStudio)

Option 1, depuis le dossier source : ouvrir `laguerreRC.Rproj`, puis menu Build, **Install Package**.

Option 2, depuis l'archive :

```r
install.packages("laguerreRC_0.1.0.tar.gz", repos = NULL, type = "source")
```

## Utilisation

```r
library(laguerreRC)
res <- lancer_projet()      # figures dans le volet Plots + dossier sortie/
res$resultats               # fits de validation

lancer_projet(p_ref = 0.5)  # une expérience : changer un paramètre à la fois
lancer_projet(N_ref = 3)
lancer_projet(sigma = 0.1)
```

Tous les anciens paramètres du script (`TAUS`, `SIGMA_BRUIT`, `P_REF`, `N_REF`...) sont des arguments de `lancer_projet()` : `taus`, `sigma`, `p_ref`, `N_ref`...

## Contenu

| Fichier | Rôle |
| --- | --- |
| `R/systeme.R` | circuit RC, génération des données, réponse impulsionnelle exacte |
| `R/laguerre.R` | réseau de Laguerre, polynômes, auto-test |
| `R/identification.R` | moindres carrés (équations normales), modèle 1er ordre, balayages en N et p |
| `R/figures.R` | les trois figures |
| `R/projet.R` | `lancer_projet()` : l'expérience complète |
| `tests/run-tests.R` | tests : orthonormalité, exemple à la main, chiffres du rapport |
| `man/` | documentation des fonctions (`?lancer_projet`) |

## Tests et vérification

```r
source("tests/run-tests.R")          # ou: R CMD check laguerreRC_0.1.0.tar.gz
```
