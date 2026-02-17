# Algorithme-de-Déquantification

Nom de l encadrant :Mahé Gaël

Catégorie(s): app. scientifique

Contexte
Coder les nombres sur un nombre minimal de bits - autrement dit, quantifier les nombres - était motivé historiquement par la limitation et le coût de la mémoire. Si cette contrainte s’est progressivement relâchée, les applications sont devenues de plus en plus gourmandes, si bien que la question de la quantification reste cruciale. Elle se pose par exemple dans la représentation des données multimédia (image, audio, vidéo) et dans le paramétrage des réseaux de neurones.

On appelle sous-quantification la réduction du nombre de bits utilisés pour représenter des valeurs. Cette opération est irréversible : une fois les données sous-quantifiées, il est impossible de retrouver la précision initiale. L’objectif ici est d’étudier expérimentalement la possibilité de déquantifier (retrouver la précision initiale) sous certaines conditions.

Dans les exemples cités précédemment, cela se traduirait, pour les données multimédia par une amélioration de la qualité du son ou de l’image, pour les réseaux de neurones par une amélioration des performances.

Objectifs :
Sous certaines conditions, à partir de l’histogramme de données sous-quantifiées, il est possible de retrouver l’histogramme originel, c’est-à-dire celui des données dans leur précision initiale [1]. Dans le cas de données ayant un ordre particulier (par exemple une série temporelle), cela vaut aussi pour l’histogramme des couples de valeurs successives. Pour une série temporelle x(n), c’est une matrice P indexée dans chaque dimension par les valeurs possibles, telle que P(i,j) est le nombre de couples (x(n-1),x(n)) prenant les valeurs correspondant respectivement aux indices i et j.

Comment exploiter cet histogramme ? Supposons que la série x, constituée d’entiers, ait été sous-quantifiée de 1 bit et appelons xQ la version sous-quantifiée : pour tout x(n), xQ(n) est le nombre pair inférieur ou égal le plus proche. Si on veut restaurer x, pour chaque xQ(n), on doit choisir entre un nombre pair et un nombre impair, de sorte que l’ensemble des séries x possibles est représentable par un arbre binaire.

Si on peut restaurer l’histogramme P des couples (x(n-1),x(n)), on va utiliser P pour construire cet arbre en l’élaguant progressivement : au rang n, chaque branche possible x(1)…x(n-1) peut être poursuivie selon 2 valeurs de x(n) (paire et impaire). Pour chacune, on regarde si le couple (x(n-1),x(n)) est permis par P. Si oui, on poursuit selon cette valeur et on décrémente la case de P concernée. Dès qu’un nœud est une feuille, on le supprime, et ainsi de suite récursivement. À la fin, on espère avoir une seule branche, ou du moins un nombre limité de x branches, c’est-à-dire de séries déquantifiées x possibles.

Travail : Un jeu de données sera fourni, incluant une série temporelle quantifiée et son histogramme des couples de valeurs successives. Le travail consistera à implémenter l’algorithme décrit ci-dessus. L’implémentation devra inclure un mode graphique permettant de visualiser le processus de construction/élagage de l’arbre.

Références bibliographiques
[1] H. Halalchi, G. Mahé, M. Jaïdane, “Revisiting quantization theorem through audiowatermarking.” , Proc. ICASSP 2009, avril 2009, pp. 3361-364

Technologies
Programmation en C ou en Julia
