# Shopify-Starter
A small guide to startup your Shopify dev environment.

## Getting Started

Shopify has many tools to work with its environment. In this guide we will talk about the most common tools used in the process of development a Shopify theme and how to install it, each tool will help you to improve your developtment experience. Also we will talk about a project setup. 

> Note: This guide is base on the official `Shopify` dev docs, if you have any question that cannot be solve here, we recommend you to see the [oficial documentation here](https://shopify.dev/docs/themes/tools).

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

Where the `[name]` parameter is the name of your new theme. By default this command create a copy of [`Dawn`](https://github.com/Shopify/dawn) Shopify's example theme (if no Git repository is defined), with the specified name in the current folder.

#### Preview themes with `theme dev` command
After the creation of your new theme, maybe you want to test and preview the current state of your project. We can do that by using [`theme dev`](https://shopify.dev/docs/themes/tools/cli/commands#dev).

Before to test the theme you must need a shopify account and shop. After you create your shopify account and shop, you must need to login in your shopify account through the Shopify CLI, using the following command:

```bash
shopify login
```

This command will open a browser tab where you must authenticate. Then you can run your theme preview by running the following command:

```bash
shopify theme dev -s "[store-name].myshopify.com"
```

Where the `[shopify-name]` parameter is the slug name of your shop. Finally you can your shopify preview by addressing to [http://127.0.0.1:9292](http://127.0.0.1:9292) in your browser.

Congrats! You installed and tested your shopify theme locally. (You must have something similar to this image after finish this last step).

![Theme preview](/imgs/preview.png)
