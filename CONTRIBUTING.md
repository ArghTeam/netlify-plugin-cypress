How to [code a plugin](https://github.com/netlify/build/blob/master/docs/creating-a-plugin.md)

## Testing

End-to-end tests are in folder [tests](tests) and they use this [plugin locally](https://github.com/netlify/build/blob/master/README.md#using-a-local-plugin) and build each subfolder using Netlify CLI on CircleCI.

## Releasing a new version

Before releasing check that each CircleCI job has actually run the tests correctly. We don't have a way to check if Cypress _executed all tests_, other than looking at the CircleCI terminal output.

Try using `beta` branch to release new pre-release versions of the plugin by following [the semantic release guide](https://github.com/semantic-release/semantic-release/blob/master/docs/recipes/pre-releases.md). You can fork and test out new versions published to NPM using the [netlify-plugin-cypress-example](https://github.com/cypress-io/netlify-plugin-cypress-example) repository. Hope the `master` branch merged into `beta` does not bring features and fixes *already released*. Thus I suggest using `beta` branch for new features.

**Do not open pull request on CircleCI** while adding new features to the `beta` branch. If there is a pull request, semantic-release refuses to publish new versions. Instead just watch the [builds on CircleCI](https://circleci.com/gh/cypress-io/netlify-plugin-cypress/tree/beta) directly and open the PR after the new version has been tested.
