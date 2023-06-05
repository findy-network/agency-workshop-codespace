# agency-workshop-codespace

[GitHub codespace](https://github.com/features/codespaces)
for the [Findy Agency Workshop](https://github.com/findy-network/agency-workshop).
The workshop instructions work best with Mac or Linux computers. If you have Windows,
or trouble setting up the environment locally, you can use
this codespace to do the workshop tasks.

1. Navigate with browser to <https://github.com/codespaces>
1. Choose *"New codespace"* from upper right corner. *"Create a new codespace"* view is opened.
1. Choose Repository *"findy-network/agency-workshop-codespace"*. Other settings can be left as they are.
1. Click *"Create codespace"* button. Codespace is created and opened in browser.
1. Wait until the codespace is ready and Terminal window becomes active in `/workshop`.
It takes a while, because it needs to download and install all the tools.
1. Now you have an instance of VS Code running in the cloud that you can access through the browser.
The environment contains already the cloned workshop codes in path `/workshop`.
Ensure you have the latest codes. Type to terminal:

    ```bash
    cd /workshop
    git pull
    ```

1. **[CLI track]** Follow the instructions for [the CLI track](https://github.com/findy-network/agency-workshop/tree/master/track1-cli#0-set-your-findy-network-root-directory).

1. **[Code track]** You should cd to your target track app directory. E.g. for TypeScript track:

    ```bash
    cd /workshop/track2.1-ts/app
    ```

1. **[Code track]** Follow the instructions for the code tracks from following steps onwards:

* [TypeScript Track Step 0.5](https://github.com/findy-network/agency-workshop/blob/master/track2.1-ts/README.md#5-set-environment-variables)
* [Go Track Step 0.5](https://github.com/findy-network/agency-workshop/blob/master/track2.2-go/README.md#5-set-environment-variables)
* [Kotlin Track Step 0.6](https://github.com/findy-network/agency-workshop/blob/master/track2.3-kt/README.md#6-set-environment-variables)

  Whenever the instructions ask to navigate to localhost endpoint,
  you should use your codespace URL instead.
  It is something like `https://<username>-<container-name>-<id>-3001.preview.app.github.dev/`.

  **NOTE for Kotlin developers**
  After executing step 0.6, you should acquire [your library access token from GitHub](https://github.com/findy-network/agency-workshop/blob/master/track2.3-kt/README.md#4-setup-authentication-to-github-registry).
  Declare the needed environment variables to `.envrc` (described in step 0.4).
