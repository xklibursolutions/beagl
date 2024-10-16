# Contributing to the Project

We are delighted that you are considering contributing to our project! Every contribution is important and helps improve the community.

## How to Contribute?

Contributions can take various forms, such as:

- Reporting bugs
- Proposing new features
- Improving documentation
- Submitting fixes

## Reporting Bugs

If you find a bug, please check if it has already been reported. If not, open a new issue providing a clear title and description, along with step-by-step instructions to reproduce the problem.

## Proposing Features

If you have an idea to improve the project, open an issue to discuss it with the maintainers. Make sure to provide as much context as possible.

## Local Development Setup

### Managing Application Secrets

For local development, we use the Secret Manager tool to store sensitive information such as JWT secrets outside of our project code. This ensures that our secrets are kept secure and are not accidentally included in source control.

#### Configuring the Secret Manager

To use the Secret Manager tool, follow these steps:

1. Navigate to the directory where your `.sln` file is located.

2. Run the following command to initialize the Secret Manager for each project:

    ```bash
    dotnet user-secrets init --project .\src\Beagl\
    ```

3. Set the connection string in the Secret Manager by running:

    ```bash
    dotnet user-secrets set "ConnectionStrings:Beagl" "Data Source=./Beagl.db" --project .\src\Beagl\
    ```

4. Add the JWT secret to your local secrets using the following command:

    ```bash
    dotnet user-secrets set "JWT:Secret" "<Your_JWT_Secret>" --project .\src\Beagl\
    ```

    Replace `<Your_JWT_Secret>` with your actual JWT secret.

5. (Optional) Set the `ValidAudience` and `ValidIssuer` for the JWT configuration:

    ```bash
    dotnet user-secrets set "JWT:ValidAudience" "<Your_Audience>" --project .\src\Beagl\
    dotnet user-secrets set "JWT:ValidIssuer" "<Your_Issuer>" --project .\src\Beagl\
    ```

    Replace `<Your_Audience>` and `<Your_Issuer>` with the actual values you want to use.

6. To verify that the secrets have been set correctly, list all secrets for the project:

    ```bash
    dotnet user-secrets list --project .\src\Beagl\
    ```

The secrets are securely stored on your local machine and are associated with your user profile.

## Pull Requests

For pull requests, follow this procedure:

1. **Fork** the project on your GitHub account.
2. **Clone** the project to your machine.
3. **Create a new branch** for your changes.
4. **Make your changes** and commit them with clear and explanatory messages.
5. **Push** your branch and open a pull request on the original project.
6. Ensure that your pull request passes all the **tests** and **checks** in place.

## Code of Conduct

We expect all contributors to adhere to our Code of Conduct. By participating, you agree to abide by this code in all your interactions with the project.

## Need Help?

If you need help or have questions, feel free to contact us.

Thank you for contributing to our project!

## Commit Message Convention

### General Structure

Each commit message should be structured as follows:

```text
<type>(<scope>): <subject> <message body> <footer>
```

### Description of Elements

- **type**: Indicates the type of change you are making.
  - `feat`: A new feature for the user.
  - `fix`: A bug fix for the user.
  - `docs`: Changes to the documentation.
  - `style`: Changes that do not affect the meaning of the code (white-space, formatting, missing semi-colons, etc).
  - `refactor`: A code change that neither fixes a bug nor adds a feature.
  - `perf`: A code change that improves performance.
  - `test`: Adding or correcting tests.
  - `chore`: Changes to the build process or auxiliary tools and libraries.

- **scope**: The scope of the commit, for example `login`, `userModel`, `clientApp`, etc.

- **subject**: A brief summary of the changes.

- **message body**: A more detailed description of the changes.

- **footer**: References to issue numbers closed by this commit.

### Examples

```text
feat(login): add captcha verification

Adds captcha verification on the login page to reduce spam attempts.

Closes #123
```

```text
fix(server): fix crash on password reset

A crash occurred when the email was null. This has been resolved by adding a prior check.

Closes #456
```
