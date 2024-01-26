# Shopify-Starter
A concise guide to start up your Shopify development environment.

## Getting Started

Shopify offers numerous tools to work within its environment. In this guide, we will discuss the most commonly used tools in the process of developing a Shopify theme and how to install them. Each tool will enhance your development experience. Additionally, we will cover project setup.

> Note: This guide is based on the official Shopify developer documentation. If you have any questions that cannot be resolved here, we recommend checking the [oficial documentation here](https://shopify.dev/docs/themes/tools).

## Shopify CLI

Shopify CLI is command-line interface tool, it helps you to quickly generate apps, themes and custome storefronts. It's also used for development task automation.

### How to install Shopify CLI

| Operating System | Requirements |
| --- | --- |
| macOS | <ul><li><a href="https://brew.sh/">Homebrew</a></li><li><a href="https://nodejs.org/en/download/">Node.js</a> 18 or higher</li><li><a href="https://www.ruby-lang.org/en/">Ruby</a></li><li><a href="https://git-scm.com/downloads">Git</a></li></ul> |
| Windows | <ul><li><a href="https://nodejs.org/en/download/">Node.js</a> 18 or higher</li><li>Ruby+Devkit 3.0, installed using <a href="https://rubyinstaller.org/downloads/">RubyInstaller for Windows</a> (select the MSYS2 component and the MSYS2 base installation option)</li><li><a href="https://git-scm.com/downloads">Git</a></li><li><a href="https://bundler.io/">Bundler</a> 2.3.8 or higher</li></ul> |
| Linux | <ul><li><a href="https://nodejs.org/en/download/">Node.js</a> 18 or higher</li><li><a href="https://www.ruby-lang.org/en/">Ruby</a> 3.0</li><li>Ruby development environment (`ruby-dev` / `ruby-devel`)</li><li><a href="https://git-scm.com/downloads">Git</a></li><li>cURL</li><li>GCC</li><li>g++</li><li>Make</li></ul> |

#### Windows/Linux installation
First you must use the following commands to install all of the requirements **(only for linux)** to install and run Shopify CLI on Linux, other than Node.js:

```bash
sudo apt update && sudo apt upgrade
sudo apt install curl gcc g++ make
sudo apt install ruby-full
sudo apt install ruby-dev
# Ruby development environment
sudo apt install git
```

To install Shopify CLI, you need to install `@shopify/cli` and `@shopify/theme` Node.js packages globally. 
```bash
npm install -g @shopify/cli @shopify/theme
```

#### macOS installation
You can install Shopify CLI on macOS using Homebrew. You need to add Shopify's third-party repositories to Homebrew using brew tap before you can install Shopify CLI:
```bash
brew tap shopify/shopify
brew install shopify-cli
```

#### Verify the installation
Finally after the installation, you can verify if Shopify CLI is installed properly by running the following command:

```bash
shopify version
```

### Create a new theme

Shopify CLI comes with a lot of [commands](https://shopify.dev/docs/themes/tools/cli/commands#command-overview) usefull for you development experience, but in this case we will use only two of them, `theme init` and `theme dev`.

#### Create themes with `theme init` command
The command [`theme init`](https://shopify.dev/docs/themes/tools/cli/commands#init) clones a Git repository to your local machine to use as the starting point for building a theme. It can by used like this:

```bash
shopify theme init [name]
```

Where the `[name]` parameter is the name of your new theme. By default, this command creates a copy of [`Dawn`](https://github.com/Shopify/dawn), Shopify's example theme (if no Git repository is defined), with the specified name in the current folder.

#### Preview themes with `theme dev` command
After creating your new theme, you may want to test and preview the current state of your project. This can be done by using [`theme dev`](https://shopify.dev/docs/themes/tools/cli/commands#dev).

Before testing the theme, you must have a Shopify account and shop. After creating your Shopify account and shop, you need to log in to your Shopify account through the Shopify CLI using the following command:

```bash
shopify login
```

This command will open a browser tab where you must authenticate. Then you can run your theme preview by running the following command:

```bash
shopify theme dev -s "[store-name].myshopify.com"
```

Where the `[shopify-name]` parameter is the slug name of your shop. Finally you can your shopify preview by addressing to [http://127.0.0.1:9292](http://127.0.0.1:9292) in your browser.

Congrats! Your theme was installed successfully (You should see something similar to this image after completing this last step.)

![Theme preview](/imgs/preview.png)


## Deployment

One of the most important things you must do is deploy your theme in your shop using the GitHub Shopify integration. This integration will assist you with the pull and push of your theme changes. Each time you push a commit to your linked branch, the integration will automatically deploy this change to your remote shop theme. This ensures that your shop theme stays in sync with your GitHub repository theme.

To synchronize a shop theme with a repository, you only need to add a new theme in your shop and click the `Connect from GitHub` option.

![Connect from Github](/imgs/connect-from-github.png)

Next, add a new GitHub account in case you do not have the Shopify integration set up on your GitHub. During this process, the integration will be automatically installed.

![Add github account](/imgs/add-account.png)

> Note: In some situations, after adding a new account, you may notice that your account has not been added. You must retry the previous steps. In case it does not work, try clearing the cache and reloading the page.

Finally add your respective theme repository.

![Add github repository](/imgs/add-repository.png)


Congratulations! Your theme was deployed successfully. (You should see something similar to this image after completing this last step.)

![Add github repository](/imgs/theme-connected.png)