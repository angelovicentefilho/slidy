
![Pub](https://img.shields.io/pub/v/slidy?color=orange)
[![GitHub stars](https://img.shields.io/github/stars/Flutterando/slidy?color=yellow)](https://github.com/Flutterando/slidy/stargazers)
[![Telegram](https://img.shields.io/badge/telegram-flutterando-blue)](https://t.me/flutterando)

[![Actions Status](https://github.com/AlvaroVasconcelos/slidy/workflows/Dart%20CI/badge.svg)](https://github.com/AlvaroVasconcelos/slidy/workflows/actions)
[![Actions Status](https://github.com/AlvaroVasconcelos/slidy/workflows/Example%20Android/badge.svg)](https://github.com/AlvaroVasconcelos/slidy/workflows/actions)
[![Actions Status](https://github.com/AlvaroVasconcelos/slidy/workflows/Example%20iOS/badge.svg)](https://github.com/AlvaroVasconcelos/slidy/workflows/actions)
[![Actions Status](https://github.com/AlvaroVasconcelos/slidy/workflows/Packages/badge.svg)](https://github.com/AlvaroVasconcelos/slidy/workflows/actions)
[![Actions Status](https://github.com/AlvaroVasconcelos/slidy/workflows/Tests/badge.svg)](https://github.com/AlvaroVasconcelos/slidy/workflows/actions)

[Acesse a documentação em Português-Brasil](README-PT.md)

# Slidy

CLI package manager and template generator for Flutter. Generate Modules, Pages, Widgets, BLoCs, Controllers and tests.

Slidy supports rxBLoC, flutter_bloc and mobx.

# Why should I use?

Slidy's goal is to help you structure your project in a standardized way. Organizing your app in **Modules** formed by pages, repositories, widgets, BloCs, and also create unit tests automatically. The Module gives you a easier way to inject dependencies and blocs, including automatic dispose. Also helps you installing the dependencies and packages, updating and removing them. The best is that you can do all of this running a single command.

# Motivations

We realized that the project pattern absence is affecting the productivity of most developers, so we're proposing a development pattern along with a tool that imitates NPM (NodeJS) functionality as well as template generation capabilities (similar to Scaffold ).

# About the Proposed Pattern

The structure that slidy offers you, it's similar to MVC, where a page keeps it's own **business logic classes(BloC)**.

We recommend you to use [flutter_modular](https://pub.dev/packages/flutter_modular) when structuring with slidy. It offers you the **module structure**(extending the ModuleWidget) and dependency/bloc injection, or you will probably get an error.

To understand **flutter_modular**, take a look at the [README](https://github.com/Flutterando/modular/blob/master/README.md).

We also use the **Repository Pattern**, so the folder structure it's organized in **local modules** and a **global module**. The dependencies(repositories, BloCs, models, etc) can be accessed throughout the application.

Sample folder structure generated by **slidy**:

![Folder example](https://github.com/Flutterando/slidy/blob/master/screenshots/folderw.png?raw=true)

## Installation

1. First of all you need install the Dart:

    [https://dart.dev/get-dart](https://dart.dev/get-dart)

2. Activate the slidy using the pub:

```bash
 pub global activate slidy
```

3. Type `slidy --version` to make sure everything is working properly. This command should return the installed version.

## Commands:

### upgrade:

Updates slidy's version:

```bash
slidy upgrade
```

### create:

Create a new project with same structure describe in start command.

```bash
slidy create **myproject**
```


### start:

Create the basic structure of your project existing (make sure that your "lib" folder it's empty).

```bash
slidy start
```

Then choose your provider:

![Folder example](https://github.com/Flutterando/slidy/blob/master/screenshots/choose_provider.PNG?raw=true)

Then choose your State Manager:

Mobx

![Folder example](https://github.com/Flutterando/slidy/blob/master/screenshots/choose_state_management_mobx.PNG?raw=true)

And you will get this Structure:

![Folder example](https://github.com/Flutterando/slidy/blob/master/screenshots/start_cmd.png?raw=true)

Flutter Bloc:

![Folder example](https://github.com/Flutterando/slidy/blob/master/screenshots/choose_state_management_flutter_bloc.PNG?raw=true)

And you will get this Structure:

![Folder example](https://github.com/Flutterando/slidy/blob/master/screenshots/start_cmd_flutter_bloc.PNG?raw=true)

Bloc With RxDart

![Folder example](https://github.com/Flutterando/slidy/blob/master/screenshots/choose_state_management_rxdart.PNG?raw=true)

And you will get this Structure:

![Folder example](https://github.com/Flutterando/slidy/blob/master/screenshots/start_cmd_rxdart.PNG?raw=true)

If you have the flutter_bloc or flutter_mobx package in pubspec, the generation of pages, widgets, and bloc defaults to the installed manager default.

#### Options

The command allows to specify provider and state manager using the following options:

* Provider:

```bash
-p <provider_name>

Options:
flutter_modular / bloc_pattern

Example:
slidy start -p flutter_modular
```

* State manager:

```bash
-s <state_manager_name>

Options:
mobx / flutter_bloc / rxdart
Example:
slidy start -s mobx
```

* Provider and state manager:

```bash
slidy start -p flutter_modular -s mobx
```

This command asks for permission to erase lib folder. If you don't want to see the warning, type the -f (force) flag:

```bash
slidy start -p flutter_modular -s mobx -f
```

### run:

Runs the scripts in pubspec.yaml:

```bash
slidy run open_folder
```

![Folder example](https://github.com/Flutterando/slidy/blob/master/screenshots/scripts.png?raw=true)

### install:

**Installs or update the packages in dependencies:**

![Folder example](https://github.com/Flutterando/slidy/blob/master/screenshots/dependencies.png?raw=true)

```bash
slidy install rxdart dio bloc_pattern
```

or you can just use the **i** command (both are the same)

```bash
slidy i rxdart dio bloc_pattern
```

**Install packages as dev_dependency:**

```bash
slidy i mockito --dev
```

![Folder example](https://github.com/Flutterando/slidy/blob/master/screenshots/dev_d.png?raw=true)

### uninstall:

Removes a package

```bash
slidy uninstall dio
```

You can also remove a **dev_dependency** using the flag --dev

### generate:

Creates a module, page, widget or repository including its BloC class.

**NOTE:** You can replace "g" with "generate" command.

Creates a new **module**:

```bash
slidy g module folder_name
```

or

```bash
slidy g m folder_name
```

![Folder example](https://github.com/Flutterando/slidy/blob/master/screenshots/module_cmd.png?raw=true)

**NOTE:** You can create a "Complete Module" with Module, Page, Bloc/Controller, tests for Page and for Bloc/Controller using the flag **-c**

**NOTE² :** You can create a "Repository" with your Module using the flag **-r**

```` slidy g m modules/my_module -c -r ````

**NOTE³ :** You can create a "Interface" for your repository with your Module using the flag **-i**

```` slidy g m modules/my_module -c -r -i ````


Creates a new **page** + BloC:

```bash
slidy g page folder_name/pages
```

or

```bash
slidy g p folder_name/pages
```

Creates a new **widget** + BloC:

```bash
slidy g widget folder_name/widgets
```

or

```bash
slidy g w folder_name/widgets
```

**NOTE:** You can create a page or widget using its respective BLoC using the flag **-b**

Create a new **repository**

```bash
slidy g r folder_name/repositories
```

**NOTE :** You can create a "Interface" for your repository using the flag **-i**

```` slidy g m modules/my_module -c -r -i ````

**NOTE :** You can create a "Interface" for your repository using the flag **-i**

```` slidy g m modules/my_module -c -r -i ````

Create a new **service**

```bash
slidy g s folder_name/services
```

**NOTE :** You can create a "Interface" for your service using the flag **-i**

```` slidy g m modules/my_module -c -s -i ````


**NOTE :** You can create a "Interface" for your service using the flag **-i**

```` slidy g m modules/my_module -c -s -i ````


Create a new **model**

```bash
slidy g mm folder_name/model
```

You can also use "repository" in "r"'s place, but it will have the same function.

![Folder example](https://github.com/Flutterando/slidy/blob/master/screenshots/structure.png?raw=true)

## Unit Tests:

Generate **unit tests** on the test folder for you.

```bash
slidy test folder_name/
```

## Common errors:

**I cant update:**

1 - First of all you need uninstall the Slidy on Flutter
```
flutter pub global deactivate slidy
```

2 - After you need uninstall the Slidy on Dart
```
pub global deactivate slidy
```

2 - And now install only in Dart
```
pub global activate slidy
```

3 - If you don't have the Pub you will need to install Dart:

  [https://dart.dev/get-dart](https://dart.dev/get-dart)


**Windows:**

  ![Folder example](https://github.com/Flutterando/slidy/blob/master/screenshots/error_windows_install.jpg?raw=true)

  If you got this error when trying to run the ```pub global activate slidy```, then you will have to set the environment variables manually:

* In windows search, write:  ```Edit System Variables```

  ![Folder example](https://github.com/Flutterando/slidy/blob/master/screenshots/step1.png?raw=true)

* Then click at ```Environment Variables```

  ![Folder example](https://github.com/Flutterando/slidy/blob/master/screenshots/step2.png?raw=true)

* Go to ```Path```

  ![Folder example](https://github.com/Flutterando/slidy/blob/master/screenshots/step3.png?raw=true)

* Then click in New and add the path that appeared on your console.

  ![Folder example](https://github.com/Flutterando/slidy/blob/master/screenshots/step4.png?raw=true)

If you have any doubt about setting up the system variables, watch [this](https://www.youtube.com/watch?v=bEroNNzqlF4) video.

For more details join our [Telegram Group Flutterando](https://t.me/flutterando)
