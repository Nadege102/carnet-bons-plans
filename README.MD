[![Netlify Status](https://api.netlify.com/api/v1/badges/1c93a85c-b198-489b-8d7a-d46f79e3d930/deploy-status)](https://app.netlify.com/sites/carnetbonsplans/deploys)

# Carnet de bons plans

Le carnet de bons plans est une initiative de [SOFFT Liège](https://sofft.be/), le service de formation pour les femmes à la recherche d'un emploi ou d'une formation. SOFFT fait partie du [CVFE, le collectif Contre les Violences Familiales et l'Exclusion](https://www.cvfe.be/).

Ce site reprend tous les bons plans dénichés par nos participantes, toutes filières de formation confondues, lors des ateliers "Vie Sociale".

Le carnet a été réfléchi dans le cadre du projet [SPINIC (Scénarios Pédagogiques Intégrateurs pour un Numérique Inclusif)](https://www.spinic.uliege.be/) mené par l'Université de Liège, le [LabSET](https://www.labset.uliege.be/cms/c_15785891/fr/labset). N'hésitez pas à vous rendre sur le site de SPINIC pour voir les différents projets et mallettes pédagogiques déjà disponibles.

Vous souhaitez reproduire cette partie du projet avec vos participants ? Retrouvez toutes les informations nécessaires ci-dessous.

Le site attaché au carnet de bons plans se veut le plus simple possible, tout en répondant à la demande / aux besoins. 

## Reproduire le site

### Cloner le projet

La première étape est de cloner/copier ce projet, ce repository (dépôt). Pour faire ceci, il existe plusieurs moyens, mais nous vous recommandons vivement de continuer à utiliser un outil de versionning tel que Git et GitHub pour plein de raisons :

- Retrouver ce qu'on avait fait précédemment en détails (historique de toutes les modifications)
- Sauvegarde et redondance, sur GitHub, le code est beaucoup plus en sécurité qu'au fond d'un vieux serveur de stockage privé.
- Praticité et portabilité (disponible partout où internet est disponible aussi)
- Partageabilité du projet
- C'est gratuit, et ce n'est pas négligeable (mais ça ne fait pas le café)

Voici un tutoriel relativement complet et bien expliqué sur Git et ses comparses : 
[https://blent.ai/blog/a/git-tutoriel-complet](https://blent.ai/blog/a/git-tutoriel-complet)

De plus, le reste du tutoriel pour la mise en ligne facile va s'appuyer sur Git / Github.

**Note**: Pour les personnes qui ne seraient pas à l'aise avec les outils en ligne de commande, il est possible d'utiliser Git et Github avec l'application Github Desktop

#### a. Avec Git, sur Github

- Créez-vous un compte Github si ce n'est pas déjà fait
- Revenez sur ce projet
- Cliquez sur [Fork](https://docs.github.com/fr/pull-requests/collaborating-with-pull-requests/working-with-forks/fork-a-repo) (cela va créer une copie dans votre espace)
![](https://docs.github.com/assets/cb-34352/mw-1440/images/help/repository/fork-button.webp)
- Remplissez les détails et validez lorsque vous avez terminé

#### b. Télécharger le projet en .zip (si vraiment, vous avez d'autres solutions)

- Cliquez sur "Code"
- Cliquez ensuite sur "Download ZIP"

### Importer vos données

Vu la quantité raisonnable de données, nous avons opté pour une solution simple, les données sont stockées dans le projet GitHub, dans le fichier [/data.csv](/data.csv). Il suffit donc d'ajouter de nouvelles lignes au format CSV, ou de remplacer le fichier. Il est également possible de renommer le fichier à condition de modifier la référence dans le fichier [index.html](https://github.com/sofft-cvfe/carnet-bons-plans/blob/master/index.html#L87)

Les catégories sont hardcodées, ce qui signifie qu'elles sont écrites en dur dans le code. Pour les modifier, il va falloir modifier [les lignes suivantes](https://github.com/sofft-cvfe/carnet-bons-plans/blob/master/index.html#L63-L71)

Les images, comme nos données, sont stockées dans le dépôt. La solution est loin d'être idéale et nous songeons actuellement a d'autres options.

### Personnalisation

La structure de base des pages de ce site web ont été générées via ChatGPT 3.5, il a tout de même fallu faire des corrections, et savoir quoi demander exactement. Mais ce fût un gain de temps considérable. 

Quand cela fût possible, nous nous sommes servis d'outils externes, déjà prêts, dans le but d'accélérer la sortie du projet, de le rendre le plus "léger" possible, et le plus reproductible également, ainsi que de rester en maîtrise des ressources disponibles.

Par exemple : 

Tailwind 2.2.19 (Framework CSS) implémenté avec un CDN ainsi que des composants "Flowbite"

```html
<link href="https://cdn.jsdelivr.net/npm/tailwindcss@2.2.19/dist/tailwind.min.css" rel="stylesheet">
<link href="https://cdnjs.cloudflare.com/ajax/libs/flowbite/2.3.0/flowbite.min.css" rel="stylesheet" />
```

Une librairie pour le traitement du fichier CSV (PapaParse)

```html
<script src="https://cdnjs.cloudflare.com/ajax/libs/PapaParse/5.3.0/papaparse.min.js"></script>
```

Des polices gratuites de Google Fonts

```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Patrick+Hand&display=swap" rel="stylesheet">
```

Un fichier de style ([/style.css](/style.css)) contenant un minimum de personnalisation est disponible à la racine du projet et peut être modifié en fonction de vos besoins et de vos envies. 

Il conviendra également de remplacer les liens des logos et des URL vers nos ressources. Le code HTML a été commenté afin de vous faciliter la recherche des éléments a changer.

```html
<div class="max-w-screen-xl flex flex-wrap items-center justify-between mx-auto p-4">
        <!-- Modifier l'attribut HREF suivant avec l'url de votre version du site -->
        <a href="https://carnetbonsplans.netlify.app" class="flex items-center space-x-4 rtl:space-x-reverse">
            <!-- Modifier l'attribut SRC avec l'url de votre logo hébergé -->
            <img src="https://sofft.be/wp-content/uploads/2021/05/Service-dOrientation-pour-Femmes-a-la-recherche-dune-Formation-ou-dun-Travail-1500-×-1500-px-1-150x150.png" class="h-12" alt="Sofft Logo" />
            <span class="self-center text-2xl font-semibold whitespace-nowrap dark:text-white"></span>
        </a>
```

### Mise en ligne (déploiement)

*Avec Github et Netlify*

1. Rendez-vous sur Netlify, et connectez-vous à l'aide de votre compte Github. (Vous pouvez créer un compte indépendant, mais cela demandera d'autres configurations)


2. Cliquez sur "Add New site" > "Import an existing project"

3. Sélectionnez "Github", une fenêtre s'ouvre, et vous demande l'autorisation d'accès. Si vous l'avez déjà fait, la fenêtre se refermera tout de suite. 

4. Sélectionnez le dépot "carnet-bons-plans" que vous aurez copié / "fork" au préalable

5. Dans "Site name" vous devez choisir le nom du projet, c'est aussi ce qui sera dans l'URL de votre site, devant le .netlify.app (notre exemple : carnetbonsplans.netlify.app). Si vous possédez un nom de domaine, il est possible de le connecter plus tard. 

6. Les paramètres suivants doivent être encodés : 
- Base Directory : /
- Build Command : " " (Vider le champ, s'il ne l'est pas)
- Publish directory : " " (Vider le champ, s'il ne l'est pas)
- Functions directory : netlify/functions (ne pas toucher ce champ)

7. Cliquez sur "Deploy leNomDeVotreSite", vous devriez recevoir un lien vers votre site fraichement déployé.