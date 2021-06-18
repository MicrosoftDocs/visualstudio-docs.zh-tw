---
title: 以 Visual Studio 2022 Preview 建立延伸模組時的目標 Visual Studio 2019
description: 瞭解如何在使用 Visual Studio 2022 Preview 建立專案時，讓您的 Visual Studio 擴充功能可搭配 Visual Studio 2019 使用。
ms.date: 06/08/2021
ms.topic: conceptual
author: leslierichardson95
ms.author: lerich
manager: jmartens
monikerRange: vs-2022
ms.workload:
- vssdk
ms.openlocfilehash: dcf556e271e6a805110eac0c978a845f2195e28f
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/17/2021
ms.locfileid: "112308706"
---
# <a name="target-a-previous-version-when-creating-an-extension-in-visual-studio-2022-preview"></a>在 Visual Studio 2022 預覽版中建立延伸模組時以先前的版本為目標

[!INCLUDE [preview-note](../includes/preview-note.md)]

當您使用 Visual Studio 2022 Preview 建立新的 VSIX 專案時，會從以 Visual Studio 2022 為目標的範本建立專案。 如果您想要以 Visual Studio 2019 或更舊版本為目標，則必須修改已建立的專案。

請考慮使用 [共用專案](update-visual-studio-extension.md#use-shared-projects-for-multi-targeting) 來鎖定 Visual Studio 2019 和 Visual Studio 2022，同時在您的延伸模組中共用大部分或所有程式碼。

請在應以 Visual Studio 2019 為目標的 VSIX 專案上遵循下列步驟：

1. 編輯檔案 `source.extension.vsixmanifest` 以移除 `ProductArchitecture` 元素和版本範圍：

    ```diff
    -<InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[17.0,18.0)">
    +<InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[16.0,17.0)">
    -  <ProductArchitecture>amd64</ProductArchitecture>
     </InstallationTarget>
    ```

   也請更新必要條件：

    ```diff
    -<Prerequisite Id="Microsoft.VisualStudio.Component.CoreEditor" Version="[17.0,18.0)" DisplayName="Visual Studio core editor" />
    +<Prerequisite Id="Microsoft.VisualStudio.Component.CoreEditor" Version="[16.0,17.0)" DisplayName="Visual Studio core editor" />
    ```

    請參閱檔案，以取得可能需要的任何其他更新。

1. 變更您在專案檔中參考的 VS SDK 套件版本：

    ```diff
    -<PackageReference Include="Microsoft.VisualStudio.SDK" Version="17.0.0-preview.1" />
    +<PackageReference Include="Microsoft.VisualStudio.SDK" Version="16.0.206" />
    -<PackageReference Include="Microsoft.VSSDK.BuildTools" Version="17.0.63-preview.1" />
    +<PackageReference Include="Microsoft.VSSDK.BuildTools" Version="16.10.32" />
    ```
