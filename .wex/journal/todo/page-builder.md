# Page builder : composer pages, formulaires et tunnels depuis la base

Opened: 2026-10-12
Updated: 2026-10-12
Author: agent:main

Pour plus tard, à discuter avec le propriétaire avant toute ligne de code. Cette todo rassemble ce qui a été décidé ailleurs ; lire les todos citées plutôt que de les recopier.

## L'idée

Un éditeur WYSIWYG où l'on place n'importe quel composant du design system, puis où l'on règle ses données. Ce que l'éditeur produit est rangé en base et rendu par les mêmes composants. Un formulaire n'est qu'un cas particulier : des composants de champ, plus une soumission. Un tunnel est une suite de pages ou de formulaires. Le form builder de network est abandonné (`NETWORK/archeo/proposed-packages/dismiss/symfony-form-builder`, environ 590 lignes jamais en prod) : on n'en garde que l'idée.

## Ordre et dépendances

1. **Préalable : les JSON schemas des composants**, dans `symfony-design-system/.wex/journal/todo/component-schemas.md`. Une fois chaque composant décrit (ses entrées, leurs types et leurs défauts), le builder devient surtout un éditeur générique de ces données.
2. **Formulaires définis en base**, dans `symfony-forms/.wex/journal/todo/forms-defined-in-database.md` : entités Form / FormField / FormSubmission, type de formulaire générique, processeur. Il faudra décider s'ils restent dans symfony-forms ou viennent ici.
3. **Tunnels définis en base**, dans `symfony-tunnels/.wex/journal/todo/98c8549c5f90.md`. Ils dépendent du point 2.
4. **Ici, dans symfony-builder** : le modèle d'une page (un arbre de composants et leurs données validées par les schémas), son rendu, l'éditeur (`symfony-builder-ds` le moment venu), la publication et les versions.

## Idées voisines à garder en vue

Ce sont des tiroirs de network, chacun déjà décrit dans sa propre todo :

- les blocs intégrables dans un site extérieur : `NETWORK/archeo/drawers/todo/embeddable-blocks.md` ;
- la vitrine publique (portfolio, page projet) : `NETWORK/archeo/drawers/todo/public-showcase.md` ;
- le mur de médias : `symfony-media-ds/.wex/journal/todo/drawer-media-wall.md` ;
- le fond animé de tuiles : `NETWORK/archeo/drawers/todo/home-blocks-map.md`.

## Questions ouvertes

1. Le stockage d'une page : un document JSON unique, ou des lignes par composant ?
2. Les formulaires et tunnels en base vivent-ils ici, ou restent-ils dans leurs packages, avec symfony-builder comme simple consommateur ?
3. Les droits d'édition et de publication : par rôle, ou par appartenance à un groupe (symfony-memberships) ?
