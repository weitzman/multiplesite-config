Introduction
================
Much more information about this project is at https://github.com/weitzman/multiplesite.

About this repository
================
 This repo has the base configuration in the master branch. In addition, there is 1 branch for each client site, also storing configuration. This arrangement makes it easy to merge configuration changes from master to clients which still allowing clients to vary slightly when necessary. Furthermore, it is very easy to compare client configuration against master or against another client.

Minutia
==============

1. The master config is force pushed from multiplesite to this repo via `git-subsplit.sh publish config/master:git@github.com:weitzman/multiplesite-config.git --heads=master`. This depends on the [git-subsplit](https://github.com/dflydev/git-subsplit/) helper tool. This can be automated for every push via a web hook. [Webtask.io](https://webtask.io/) looks great for hosting web hook code.
1. The [composer.json](https://github.com/weitzman/multiplesite-config/blob/alpha/composer.json) files in each branch specify a package type of 'bonefish-package.' We need to specify a type in order for composer-installers to work, and bonefish is the silliest option.
1. It is possible to have git conflicts when merging from master to client branches. There may be a way with [rerere](https://medium.com/@porteneuve/fix-conflicts-only-once-with-git-rerere-7d116b2cec67#.cofpprewi) to save the conflict resolution for use on other client branches.
