.ignore [![Build Status](https://travis-ci.org/hsz/idea-gitignore.svg)](https://travis-ci.org/hsz/idea-gitignore) [![Donate](https://www.paypalobjects.com/en_US/i/btn/btn_donate_SM.gif)](https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=SJAU4XWQ584QL) <a href="http://blockchain.info/address/1BUbqKrUBmGGSnMybzGCsJyAWJbh4CcwE1"><img src="https://www.gnu.org/software/octave/images/donate-bitcoin.png" width="100" height="21"/></a>
==================


Introduction
------------

**.ignore** is a plugin for:
 
- `.gitignore` (GIT),
- `.hgignore` (Mercurial),
- `.npmignore` (NPM),
- `.dockerignore` (Docker)
- `.chefignore` (Chef)
- `.cvsignore` (CVS)
- `.bzrignore` (Bazaar)
- `.boringignore` (Darcs)
- `.mtn-ignore` (Monotone)
- `ignore-glob` (Fossil)
- `.jshintignore` (JSHint)
- `.tfignore` (Team Foundation)
- `.p4ignore` (Perforce)

files in your project. It supports following JetBrains IDEs:

- Android Studio
- AppCode
- CLion
- IntelliJ IDEA
- PhpStorm
- PyCharm
- RubyMine
- WebStorm
- 0xDBE

*Compiled with Java 1.6*


Features
--------

- Files syntax highlight
- Coloring ignored files in the Project View
- Gitignore templates filtering and selecting in rules generator by name and content
- User custom templates
- Show ignored files by specified Gitignore file (right click on `.gitignore` file)
- Create file in currently selected directory
- Generate Gitignore rules basing on [GitHub's templates collection][github-gitignore]
- Add selected file/directory to Gitignore rules from popup menu
- Suggesting `.gitignore` file creation for new project
- Entries inspection (duplicated, covered, unused, incorrect syntax, relative entries) with fix actions
- Comments and brackets support
- Navigation to entries in Project view
- Renaming entries from Gitignore file


Installation
------------

- Using IDE built-in plugin system:
  - <kbd>Preferences</kbd> > <kbd>Plugins</kbd> > <kbd>Browse repositories...</kbd> > <kbd>Search for ".ignore"</kbd> > <kbd>Install Plugin</kbd>
- Manually:
  - Download the [latest release][latest-release] and install it manually using <kbd>Preferences</kbd> > <kbd>Plugins</kbd> > <kbd>Install plugin from disk...</kbd>
  
Restart IDE.


Usage
-----

1. Generate new file and templates usage

   To generate new ignore file, just click on <kbd>File</kbd> > <kbd>New</kbd> or use <kbd>Alt</kbd> + <kbd>Insert</kbd> shortcut and select `.ignore file` element.

   ![Generate new file](http://gitignore.hsz.mobi/usage-1.gif)

2. Support for typing new rules, linking rules with matched files

   ![Support for typing new rules](http://gitignore.hsz.mobi/usage-2.gif)

3. Code inspections

   Code inspections covers few cases:

   - duplicated entries (checks if entry is defined more than once)
   - covered entries - entry is covered by more general one
   - unused entries
   - incorrect syntax (regexp rules)
   - relative entries

   ![Code inspections](http://gitignore.hsz.mobi/usage-3.gif)


Changelog
---------

## [v1.1.4](https://github.com/hsz/idea-gitignore/tree/v1.1.4) (2015-06-02)

[Full Changelog](https://github.com/hsz/idea-gitignore/compare/v1.1.2...v1.1.4)

**Fixed bugs:**

- NoSuchMethodError ContainerUtil.isEmpty(Ljava/util/List;) [\#140](https://github.com/hsz/idea-gitignore/issues/140)
- CacheMap.getParentStatus must not return null [\#138](https://github.com/hsz/idea-gitignore/issues/138)
- Utils.isUnder - directory must not be null [\#137](https://github.com/hsz/idea-gitignore/issues/137)
- NPE after adding null to the files list [\#130](https://github.com/hsz/idea-gitignore/issues/130)
- Exclude ignored `.ignore` files from parsing [\#125](https://github.com/hsz/idea-gitignore/issues/125)
- Error while opening project - messageBus not initialized [\#123](https://github.com/hsz/idea-gitignore/issues/123)
- Access is allowed from event dispatch thread only [\#122](https://github.com/hsz/idea-gitignore/issues/122)


[Full Changelog History](./CHANGELOG.md)


Contribution
------------

Check [`CONTRIBUTING.md`](./CONTRIBUTING.md) file.

### Compiling the source code

- Clone `idea-ignore` project from https://github.com/hsz/idea-gitignore.git
- [Configure IntelliJ IDEA Plugin SDK][idea-sdk-configuration]
- Install required plugins:
  - Plugin DevKit *(bundled)*
  - [Grammar-Kit][grammar-kit-plugin]
  - [PsiViewer][psiviewer-plugin]
  - [JFlex Support][jflex-support-plugin]
- Create *New Project* as a *IntelliJ Platform Plugin* and set *Project location* to the **idea-gitignore** sources
  - In <kbd>Project settings</kbd> > <kbd>Modules</kbd> section mark:
    - `gen` as *Sources*
    - `resources` as *Resources*
    - `src` as *Sources*
    - `tests` as *Test Sources*
    - `.idea` as *Excluded*
    - `out` as *Excluded*
- Add new *Run/Debug configuration*
  - <kbd>+</kbd> <kbd>Add new configuration</kbd> > <kbd>Plugin</kbd>
  - Add `-Didea.is.internal=true` to *VM Options* (it will allow you run internal actions like `View PSI structure` action)
  - Remove `-XX:MaxPermSize=250m` from *VM Options*
- Generate PSI classes
  - Go to [`Gitignore.bnf`][bnf-file] file and **Generate Parser Code**
    - <kbd>Tools</kbd> > <kbd>Generate Parser Code</kbd> (<kbd>Ctrl</kbd> + <kbd>Shift</kbd> + <kbd>G</kbd>)
  - Go to [`Gitignore.flex`][flex-file] file and **Run JFlex Generator**
    - <kbd>Tools</kbd> > <kbd>Run JFlex Generator</kbd> (<kbd>Ctrl</kbd> + <kbd>Shift</kbd> + <kbd>G</kbd>)
    - For the first time it will download `JFlex.jar` and `idea-flex.skeleton` files - save them in the root project directory
- Set *Java Compiler* to **1.6**
  - Go to <kbd>Settings</kbd> > <kbd>Compiler</kbd> > <kbd>Java Compiler</kbd> and set *Project bytecode version* to **1.6**
- In *Ant Build* add [`build.xml`][build-xml] file and mark **generate-templates-list** task as <kbd>Execute on</kbd> > <kbd>Before compilation</kbd>

Developed By
------------

[**@hsz** Jakub Chrzanowski][hsz]


**Contributors**

- [**@zolotov** Alexander Zolotov](https://github.com/zolotov)
- [**@bedla** Ivo Šmíd](https://github.com/bedla)
- [**@danpfe**](https://github.com/danpfe)


License
-------

Copyright (c) 2015 hsz Jakub Chrzanowski. See the [LICENSE](./LICENSE) file for license rights and limitations (MIT).

    
[github-gitignore]:       https://github.com/github/gitignore
[idea-sdk-configuration]: http://confluence.jetbrains.com/display/IntelliJIDEA/Prerequisites
[grammar-kit-plugin]:     http://plugins.jetbrains.com/plugin/6606
[psiviewer-plugin]:       http://plugins.jetbrains.com/plugin/227
[jflex-support-plugin]:   http://plugins.jetbrains.com/plugin/263
[bnf-file]:               ./resources/bnf/Ignore.bnf
[flex-file]:              ./src/mobi/hsz/idea/gitignore/lexer/Ignore.flex
[build-xml]:              ./build.xml
[hsz]:                    http://hsz.mobi
[latest-release]:         https://github.com/hsz/idea-gitignore/releases/latest
