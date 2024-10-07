# Contribuer au projet

Nous sommes ravis que vous envisagiez de contribuer à notre projet ! Chaque contribution est importante et aide à améliorer la communauté.

## Comment contribuer ?

Les contributions peuvent prendre différentes formes, telles que :

- Signaler des bugs
- Proposer de nouvelles fonctionnalités
- Améliorer la documentation
- Soumettre des correctifs

## Signaler des bugs

Si vous trouvez un bug, merci de vérifier si celui-ci a déjà été signalé. Si ce n'est pas le cas, ouvrez une nouvelle issue en fournissant un titre et une description clairs, ainsi qu'une étape par étape pour reproduire le problème.

## Proposer des fonctionnalités

Si vous avez une idée pour améliorer le projet, ouvrez une issue pour en discuter avec les mainteneurs. Assurez-vous de donner autant de contexte que possible.

## Configuration du développement local

### Gestion des secrets d'application

Pour le développement local, nous utilisons l'outil Secret Manager pour stocker des informations sensibles telles que les secrets JWT en dehors de notre code de projet. Cela garantit que nos secrets sont conservés en sécurité et ne sont pas accidentellement intégrés au contrôle de source.

#### Configuration du Secret Manager

Pour utiliser l'outil Secret Manager, suivez ces étapes :

1. Naviguez jusqu'au répertoire où se trouve votre fichier `.sln`.

2. Exécutez la commande suivante pour initialiser le Secret Manager pour chaque projet :

    ```bash
    dotnet user-secrets init --project .\src\Beagl\
    ```

3. Définissez la chaîne de connexion dans le Secret Manager en exécutant :

    ```bash
    dotnet user-secrets set "ConnectionStrings:Beagl" "Data Source=./Beagl.db" --project .\src\Beagl\
    ```

4. Ajoutez le secret JWT à vos secrets locaux en utilisant la commande suivante :

    ```bash
    dotnet user-secrets set "JWT:Secret" "<Votre_Secret_JWT>" --project .\src\Beagl\
    ```

    Remplacez `<Votre_Secret_JWT>` par votre véritable secret JWT.

5. (Optionnel) Définissez le `ValidAudience` et le `ValidIssuer` pour la configuration JWT :

    ```bash
    dotnet user-secrets set "JWT:ValidAudience" "<Votre_Audience>" --project .\src\Beagl\
    dotnet user-secrets set "JWT:ValidIssuer" "<Votre_Emetteur>" --project .\src\Beagl\
    ```

    Remplacez `<Votre_Audience>` et `<Votre_Emetteur>` par les valeurs réelles que vous souhaitez utiliser.

6. Pour vérifier que les secrets ont été correctement définis, listez tous les secrets pour le projet :

    ```bash
    dotnet user-secrets list --project .\src\Beagl\
    ```

Les secrets sont stockés de manière sécurisée sur votre machine locale et sont associés à votre profil utilisateur.

## Pull Requests

Pour les pull requests, voici la procédure à suivre :

1. **Fork** le projet sur votre compte GitHub.
2. **Clone** le projet sur votre machine.
3. **Créez une nouvelle branche** pour vos modifications.
4. **Faites vos modifications** et committez-les avec des messages clairs et explicatifs.
5. **Poussez** votre branche et ouvrez une pull request sur le projet original.
6. Assurez-vous que votre pull request passe tous les **tests** et **checks** mis en place.

## Code de conduite

Nous attendons de tous les contributeurs qu'ils respectent notre Code de Conduite. Par votre participation, vous acceptez de respecter ce code dans toutes vos interactions avec le projet.

## Besoin d'aide ?

Si vous avez besoin d'aide ou avez des questions, n'hésitez pas à nous contacter.

Merci de contribuer à notre projet !

## Convention de Nommage des Commits

### Structure Générale

Chaque message de commit doit être structuré comme suit :

```text
<type>(<portée>): <sujet> <corps du message> <pied de page>
```

### Description des éléments

- **type** : Indique le type de changement que vous apportez.
  - `feat` : Nouvelle fonctionnalité pour l'utilisateur.
  - `fix` : Correction d'un bug pour l'utilisateur.
  - `docs` : Changements dans la documentation.
  - `style` : Changements qui n'affectent pas le sens du code (espaces, formatage, points-virgules manquants, etc).
  - `refactor` : Changement du code qui ne corrige ni ajoute une fonctionnalité.
  - `perf` : Changement du code qui améliore les performances.
  - `test` : Ajout ou correction de tests.
  - `chore` : Changements aux tâches de build ou aux outils auxiliaires et bibliothèques.

- **portée** : La portée du commit, par exemple `login`, `userModel`, `clientApp`, etc.

- **sujet** : Un bref résumé des changements.

- **corps du message** : Une description plus détaillée des changements.

- **pied de page** : Références aux numéros d'issue fermés par ce commit.

### Exemples

```text
feat(login): ajouter la vérification du captcha

Ajoute une vérification captcha sur la page de connexion pour réduire les tentatives de spam.

Closes #123
```

```text
fix(server): corriger le crash lors de la réinitialisation du mot de passe

Un crash se produisait lorsque l'email était null. Cela a été résolu en ajoutant une vérification préalable.

Closes #456
```
