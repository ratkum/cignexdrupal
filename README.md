# BLT Experimental Project

This is experimental project to get an undersanding of BLT setup.


## Getting Started

This project is based on BLT, an open-source project template and tool that enables building, testing, and deploying Drupal installations following Acquia Professional Services best practices. While this is one of many methodologies, it is our recommended methodology. 

1. Review the [Required / Recommended Skills](http://blt.readthedocs.io/en/latest/readme/skills) for working with a BLT project.
2. Ensure that your computer meets the minimum installation requirements (and then install the required applications). See the [System Requirements](http://blt.readthedocs.io/en/latest/INSTALL/#system-requirements).
3. Request access to organization that owns the project repo in GitHub (if needed).
4. Fork the project repository in GitHub.
5. Request access to the Acquia Cloud Environment for your project.
6. Setup a SSH key that can be used for GitHub and the Acquia Cloud (you CAN use the same key).
      i. [Setup GitHub SSH Keys](https://help.github.com/articles/adding-a-new-ssh-key-to-your-github-account/)
      ii. [Setup Acquia Cloud SSH Keys](https://docs.acquia.com/acquia-cloud/ssh/generate)
      
7. Clone your forked repository. By default, Git names this "origin" on your local.
    ```
    $ git clone git@github.com:<account>/cignexdrupal.git
    ```
8. To ensure that upstream changes to the parent repository may be tracked, add the upstream locally as well.
    ```
    $ git remote add upstream git@github.com:ratkum/cignexdrupal.git
    ```

9. Setup Vagrant Auto-networking (if you haven't already). This is so you can have multiple DrupalVM instances running without needing to muck with IPs in /etc/hosts.:

    ```
    $ vagrant plugin install vagrant-auto_network
    ```
# Setup local environment.

BLT provides an automation layer for testing, building, and launching Drupal 8 applications. For ease when updating codebase it is recommended to use  Drupal VM. If you prefer, you can use another tool such as Docker, Docksal, Lando, (other) Vagrant, or your own custom LAMP stack, however support is very limited for these solutions.

1. After you have forked and cloned the project. Install Composer Dependencies. (Warning: this can take some time based on internet speeds.)
   ```
    $ composer install
   ```

2.  Use BLT to setup the Drupal VM with the configuration from this repositories [configuration files](#important-configuration-files) (one time only).

    ```
    $ blt vm
    ```

3. If blt alias is not available use this command outside and inside vagrant (one time only).
    ```
    $ composer run-script blt-alias
    ```

4. SSH into your localized Drupal VM environment automated with the BLT launch and automation tools.
    ```
    $ vagrant ssh
    ```

5. Use BLT to setup the site with configuration. 
    ```
    $ blt setup
    ```

6. Access the site and do necessary work at #LOCAL_DEV_URL by running the following commands.
    ```
    $ cd docroot
    $ drush uli
    ```

---

# Resources

Additional [BLT documentation](http://blt.readthedocs.io) may be useful. You may also access a list of BLT commands by running this:
```
$ blt
```

Note the following properties of this project:
* Primary development branch: `develop`
* Local environment: @cignex-drupal.local
* Local site URL: http://local.cignex-drupal.com

## Working With a BLT Project

BLT projects are designed to instill software development best practices (including git workflows).

Our BLT Developer documentation includes an [example workflow](http://blt.readthedocs.io/en/latest/readme/dev-workflow/#workflow-example-local-development).

### Important Configuration Files

BLT uses a number of configuration (`.yml` or `.json`) files to define and customize behaviors. Some examples of these are:

* `blt/blt.yml` (formerly blt/project.yml prior to BLT 9.x)
* `blt/local.blt.yml`
* `box/config.yml` (if using Drupal VM)
* `drush/sites` (contains Drush aliases for this project)
* `composer.json` (includes required components, including Drupal Modules, for this project)



## Working With a BLT Project

BLT projects are designed to instill software development best practices (including git workflows). 

Our BLT Developer documentation includes an [example workflow](http://blt.readthedocs.io/en/latest/readme/dev-workflow/#workflow-example-local-development).

### Important Configuration Files

BLT uses a number of configuration (`.yml` or `.json`) files to define and customize behaviors. Some examples of these are:

* `blt/blt.yml` (formerly blt/project.yml prior to BLT 9.x)
* `blt/local.blt.yml`
* `box/config.yml` (if using Drupal VM)
* `drush/sites` (contains Drush aliases for this project)
* `composer.json` (includes required components, including Drupal Modules, for this project)



## Using This Template


Remove this section after initial setup!

Search for and replace the following placeholders within this file:

| Placeholder | Example |
| --- | --- |
| `#ACQUIA_CLOUD_URL` | https://cloud.acquia.com/app/develop/applications/d9bcae8b-fea0-41b8-81f3-5ebb0247164c |
| `#GIT_PRIMARY_DEV_BRANCH` | `develop` |
| `#GITHUB_ORG` | The "org" https://github.com/ratkum/cignexdrupal |
| `#GITHUB_PROJECT` | https://github.com/ratkum/cignexdrupalt |
| `#LOCAL_DEV_URL` | http://local.cignex-drupal.com/ |
| `#TRAVIS_URL` | https://travis-ci.com/ratkum/cignexdrupal |


