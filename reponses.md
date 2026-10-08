# Réponses – TP final Git NovaTech

## Mission 5 – Analyse de l'historique

1. Identifiant court du premier commit : `56aeabe`
2. Commit correspondant à l'ajout de la page Contact : `a5963bd` (création de la page), complété par `1a5335b` (ajout du formulaire)
3. Nombre de commits à ce stade : 8 (obtenu avec `git rev-list --count HEAD`)
4. Commande pour afficher l'historique sous forme graphique : `git log --oneline --graph --all`

Commande utilisée pour examiner un commit Contact : `git show a5963bd`


## Mission 8 – Annulation d'un commit local

Commande utilisée : `git reset HEAD~1` (équivalent à `git reset --mixed HEAD~1`)

Cette commande déplace HEAD et la branche `master` d'un commit en arrière : le commit « Test affichage » disparaît de l'historique. Les modifications restent présentes dans le fichier, car le mode `--mixed` ne touche pas à la zone de travail : il vide seulement la zone de staging.

## Mission 9 – Annulation d'un commit partagé

Commande utilisée : `git revert HEAD`

`git revert` crée un nouveau commit qui applique l'inverse des modifications du commit « Ajout promotion ». Le commit d'origine reste dans l'historique.
Avec `git reset`, l'historique aurait été réécrit, ce qui aurait créé des incohérences. `git revert` est la méthode sûre pour un commit déjà partagé.