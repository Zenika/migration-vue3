# TP : Migration d'un projet vue 2 en vue 3

## 1 - Installation et configuration de la migration

Dans le `package.json`, mettre à jour vue en remplacant `vue ^2.7.16` par `vue ^3` puis lancer la commande `npm update vue`

Lancer la commande `npm i @vue/compat`

Remplacer `vue-template-compiler` par `@vue/compiler-sfc@^3.1.0`

Modifier le fichier de configuration `vue.config.js` comme vu dans les slides 

## 2 - Correction des erreurs liées à la migration 

Il se peut que la migration ne soit pas entièrement compatible avec Vue 3 et le démarrage de l'application risque de ne pas fonctionner. Après le passage à la version de migration, on rencontre des warnings à l'exécution (dans la console du navigateur) et à la compilation (dans la ligne de commande). 

On traite en premier les avertissements du compilateur, car certains peuvent casser l'application, comme l'utilisation de filters.

Dans le fichier` TodoList.vue` déplacer et ajuster le contenu de la propriété `filters` dans la proprièté `computed` 

## 3 - Résoudre la compatibilité des paquets
De nombreux paquets sont désormais compatibles avec Vue 3. Il faut les mettre à jour avec leurs dernières versions. 

Si vous ne trouvez pas de version compatible avec Vue 3, trouvez des remplacements appropriés.

**Exemple de vuex**: Il existe une version `^4.1.0` compatible avec vue3 : la remplacer dans `package.json`

## 4 - Correction des warnings liés à la migration
Maintenant, l'application peut s'exécuter, mais il y a encore du travail à faire. 

A l'exécution, vous retrouverez des warning dans la console. 

Ils doivent être corrigés et chaque avertissement a un identifiant (par exemple, GLOBAL_MOUNT, OPTIONS_DATA_FN, etc.). Vous trouverez une liste complète des différents avertissements [ici](https://v3-migration.vuejs.org/migration-build.html#compatibility-types).

## 5 - Migrer vers l'API de composition de Vue 3

### 5.1 - Migrer de vuex à pinia
Installer Pinia

Convertir le contenu du fichier `./stores/store.js` et remplacer l'utilisation de vuex par celle de pinia

### 5.2 Migrer les composants
Reprendre les fichiers `*.vue` et les convertir en Composant de compositions 

## 6 - Testez et assurez la performance et stabilité de l'application
Testez vos composants migrés pour garantir leur fonctionnalité dans l'environnement Vue 3. 

Utilisez l'extension Vue Devtools pour déboguer et inspecter votre application pendant la migration.

## 7 - Désinstaller le build de migration
Une fois que les tests sont terminés et que votre application fonctionne parfaitement dans Vue 3, il faudra :
- Désinstaller le paquet @vue/compat
- Désinstaller les packages deprecated ou inutilisés (ici vuex)
- Supprimez les modifications apportées à l'étape 1 au fichier `vue.config.js`.