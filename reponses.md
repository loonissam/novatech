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

## Mission 11 – Récupération d'un commit précis

Commande utilisée : `git cherry-pick dea898d`


Une fusion classique (`git merge test`) aurait intégré les trois commits de la branche, y compris la modification expérimentale des couleurs et le texte de test dans le footer, qui ne devaient pas arriver sur la branche principale. `git cherry-pick` permet de n'appliquer que le commit voulu (la correction orthographique), en créant une copie de ce commit sur `master`.

## Mission 12 – Version stable

Commandes utilisées : `git tag -a v1.0.0 -m "Première version stable de NovaTech"` puis `git show v1.0.0`

Signification de 1.0.0:
- 1 (MAJEUR) : changements incompatibles avec les versions précédentes
- 0 (MINEUR) : ajout de fonctionnalités compatibles
- 0 (CORRECTIF) : corrections de bugs sans nouvelle fonctionnalité

Versions suivantes :
- Correction d'un bug mineur : 1.0.1
- Nouvelle fonctionnalité compatible : 1.1.0
- Refonte majeure incompatible : 2.0.0

## Questions finales

1. **Zone de travail / staging / historique** : la zone de travail contient les fichiers tels qu'on les modifie. La zone de staging (index) contient ce qu'on a préparé avec `git add` pour le prochain commit. L'historique contient les commits enregistrés avec `git commit`.

2. **Branche dédiée** : elle permet de développer une fonctionnalité sans casser la branche principale, de travailler en parallèle et de n'intégrer le travail qu'une fois terminé et testé.

3. **Missions 8 et 9** : `git reset` supprime le commit de l'historique (il le réécrit), ce qui ne convient qu'à un commit local non partagé. `git revert` ajoute un nouveau commit qui annule le précédent, sans réécrire l'historique : c'est la méthode sûre pour un commit déjà partagé.

4. **Mettre de côté (stash)** : quand on doit changer de tâche ou de branche en urgence alors que le travail en cours n'est pas prêt à être commité.

5. **Cherry-pick plutôt que merge** : il permet de récupérer uniquement une correction précise sans importer les autres commits de la branche (tests, expérimentations non validées).

6. **HEAD** : c'est le pointeur vers le commit actuellement extrait, en général le dernier commit de la branche courante.

7. **HEAD~2** : le commit situé deux commits avant HEAD (le « grand-parent » du commit actuel).

8. **Tag** : il marque un commit précis de façon permanente, généralement pour identifier une version publiée (ex. v1.0.0).

9. **Commits petits et précis** : l'historique est plus lisible, il est plus facile de retrouver l'origine d'un bug, et on peut annuler ou récupérer une modification précise sans toucher au reste.

10. **Fichiers non versionnés** : certains fichiers sont générés automatiquement, propres à chaque machine, ou contiennent des données sensibles (mots de passe, clés API dans `.env`). Les versionner alourdirait le dépôt ou exposerait des secrets.