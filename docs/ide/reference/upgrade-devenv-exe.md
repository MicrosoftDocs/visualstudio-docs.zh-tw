---
title: -Upgrade (devenv.exe)
description: 瞭解如何使用 Upgrade devenv 命令列參數，將方案檔和其所有專案檔或指定的專案檔更新為這些檔案目前的 Visual Studio 格式。
ms.custom: SEO-VS-2020
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- /upgrade Devenv switch
- Devenv, /upgrade switch
- upgrade Devenv switch
ms.assetid: 3468045c-5cc9-4157-9a9d-622452145d27
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e7dc759cefae4ae262362265daf67ee5b1cb50f2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99960555"
---
# <a name="upgrade-devenvexe"></a>/Upgrade (devenv.exe)

將方案檔及其所有專案檔或指定的專案檔更新為這些檔案的目前 Visual Studio 格式。

## <a name="syntax"></a>語法

```shell
devenv {SolutionFile|ProjectFile} /Upgrade [/Out OutputFilename]
```

## <a name="arguments"></a>引數

- *解決方案檔*

  如果您要升級整個方案及其專案，則為必要項。 方案檔的路徑和名稱。 您可以只輸入方案檔的名稱，或是方案檔的完整路徑和名稱。 如果指定的資料夾或檔案尚未存在，則會予以建立。

- *專案檔*

  如果您要升級單一專案，則為必要項。 方案中專案檔的路徑和名稱。 您可以只輸入專案檔的名稱，或是專案檔的完整路徑和名稱。 如果指定的資料夾或檔案尚未存在，則會予以建立。

- `/Out`*OutputFilename*

  選擇性。 您要將工具的輸出傳送到其中的檔案名稱。 如果檔案已經存在，工具就會將輸出附加至檔案結尾。

## <a name="remarks"></a>備註

備份會自動建立並複製到已在目前目錄中建立且名為 Backup 的目錄。

必須先簽出原始檔控制的方案或專案，才能進行升級。

使用 `/Upgrade` 參數不會開啟 Visual Studio。 在方案或專案之開發語言的升級報表中可以看到升級結果。 不會傳回任何錯誤或使用方式資訊。 如需在 Visual Studio 中升級專案的詳細資訊，請參閱[移植、移轉及升級 Visual Studio 專案](../../porting/port-migrate-and-upgrade-visual-studio-projects.md)。

## <a name="example"></a>範例

這個範例會升級名為 "MyProject.sln" 的方案檔。

```shell
devenv "%USERPROFILE%\source\repos\MyProject\MyProject.sln" /upgrade
```

## <a name="see-also"></a>另請參閱

- [Devenv 命令列參數](../../ide/reference/devenv-command-line-switches.md)
