---
title: Commande dotnet tool install - CLI .NET Core
description: La commande dotnet tool install permet d’installer l’outil global .NET Core spécifié sur votre machine.
author: mairaw
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: aad5a3e815936749d90f40975a8b13d34e89386c
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43512193"
---
# <a name="dotnet-tool-install"></a>dotnet tool install

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="name"></a>Name

`dotnet tool install` - Installe l’[outil global .NET Core](global-tools.md) spécifié sur votre machine.

## <a name="synopsis"></a>Résumé

```console
dotnet tool install <PACKAGE_NAME> <-g|--global> [--add-source] [--configfile] [--framework] [-v|--verbosity] [--version]
dotnet tool install <PACKAGE_NAME> <--tool-path> [--add-source] [--configfile] [--framework] [-v|--verbosity] [--version]
dotnet tool install <-h|--help>
```

## <a name="description"></a>Description

La commande `dotnet tool install` vous offre un moyen d’installer des outils globaux .NET Core sur votre machine. Pour utiliser la commande, vous devez spécifier que vous voulez une installation à l’échelle de l’utilisateur à l’aide de l’option `--global` ou vous spécifiez un chemin d’installation à l’aide de l’option `--tool-path`.

Les outils globaux sont installés par défaut dans les répertoires suivants quand vous spécifiez l’option `-g` (ou `--global`) :

| Système d’exploitation          | Chemin d’accès                          |
|-------------|-------------------------------|
| Linux/macOS | `$HOME/.dotnet/tools`         |
| Windows     | `%USERPROFILE%\.dotnet\tools` |

## <a name="arguments"></a>Arguments

`PACKAGE_NAME`

Nom/ID du package NuGet qui contient l’outil global .NET Core à installer.

## <a name="options"></a>Options

`--add-source <SOURCE>`

Ajoute une source de package NuGet supplémentaire à utiliser pendant l’installation.

`--configfile <FILE>`

Fichier de configuration NuGet (*nuget.config*) à utiliser.

`--framework <FRAMEWORK>`

Spécifie le [framework cible](../../standard/frameworks.md) pour lequel installer l’outil. Par défaut, le SDK .NET Core essaie de choisir le framework cible le plus approprié.

`-g|--global`

Spécifie que l’installation est à l’échelle de l’utilisateur. Non combinable avec l’option `--tool-path`. Si vous ne spécifiez pas cette option, vous devez spécifier l’option `--tool-path`.

`-h|--help`

Affiche une aide brève pour la commande.

`--tool-path <PATH>`

Spécifie l’emplacement d’installation de l’outil global. Le chemin peut être absolu ou relatif. Si le chemin n’existe pas, la commande essaie de le créer. Non combinable avec l’option `--global`. Si vous ne spécifiez pas cette option, vous devez spécifier l’option `--global`.

`-v|--verbosity <LEVEL>`

Définit le niveau de détail de la commande. Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`.

`--version <VERSION_NUMBER>`

Version de l’outil à installer. Par défaut, la dernière version stable du package est installée. Utilisez cette option pour installer la préversion ou des versions antérieures de l’outil.

## <a name="examples"></a>Exemples

Installe l’outil global [dotnetsay](https://www.nuget.org/packages/dotnetsay/) à l’emplacement par défaut :

`dotnet tool install -g dotnetsay`

Installe l’outil global [dotnetsay](https://www.nuget.org/packages/dotnetsay/) dans un dossier Windows spécifique :

`dotnet tool install dotnetsay --tool-path c:\global-tools`

Installe l’outil global [dotnetsay](https://www.nuget.org/packages/dotnetsay/) dans un dossier Linux/macOS spécifique :

`dotnet tool install dotnetsay --tool-path ~/bin`

Installe la version 2.0.0 de l’outil global [dotnetsay](https://www.nuget.org/packages/dotnetsay/) :

`dotnet tool install -g dotnetsay --version 2.0.0`

## <a name="see-also"></a>Voir aussi

* [Outils globaux .NET Core](global-tools.md)