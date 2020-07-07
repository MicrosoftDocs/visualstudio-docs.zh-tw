---
title: 使用 MSBuild 工作建立 SharePoint 方案套件
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packages
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c59a38e1153a57c1bd886121eeac244075045a42
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: zh-TW
ms.lasthandoff: 07/06/2020
ms.locfileid: "86017015"
---
# <a name="how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks"></a>如何：使用 MSBuild 工作建立 SharePoint 方案套件
  您可以在開發電腦上使用命令列 MSBuild 工作來建立、清理和驗證 SharePoint 封裝（*.wsp*）。 您也可以使用這些命令，在組建電腦上使用 Team Foundation Server，將組建程式自動化。

## <a name="build-a-sharepoint-package"></a>建立 SharePoint 封裝

#### <a name="to-build-a-sharepoint-package"></a>若要建立 SharePoint 封裝

1. 在 Windows [**開始**] 功能表上，選擇 [**所有程式**] [附屬專案]  >  **Accessories**  >  **命令提示**字元。

2. 切換至 SharePoint 專案所在的目錄。

3. 輸入下列命令來建立專案的封裝。 以專案的名稱取代*ProjectFileName* 。

    ```cmd
    msbuild /t:Package ProjectFileName
    ```

     例如，您可以執行下列其中一個命令來封裝名為 ListDefinition1 的 SharePoint 專案。

    ```cmd
    msbuild /t:Package ListDefinition1.vbproj
    msbuild /t:Package ListDefinition1.csproj
    ```

## <a name="clean-a-sharepoint-package"></a>清除 SharePoint 封裝

#### <a name="to-clean-a-sharepoint-package"></a>若要清除 SharePoint 封裝

1. 開啟 [命令提示字元] 視窗。

2. 切換至 SharePoint 專案所在的目錄。

3. 輸入下列命令以清除專案的封裝。 以專案的名稱取代*ProjectFileName* 。

    ```cmd
    msbuild /t:CleanPackage ProjectFileName
    ```

     例如，您可以執行下列其中一個命令，以清除名為 ListDefinition1 的 SharePoint 專案。

    ```cmd
    msbuild /t:CleanPackage ListDefinition1.vbproj
    msbuild /t:CleanPackage ListDefinition1.csproj
    ```

## <a name="validate-a-sharepoint-package"></a>驗證 SharePoint 封裝

#### <a name="to-validate-a-sharepoint-package"></a>若要驗證 SharePoint 封裝

1. 開啟 [命令提示字元] 視窗。

2. 切換至 SharePoint 專案所在的目錄。

3. 輸入下列命令以驗證專案的封裝。 以專案的名稱取代*ProjectFileName* 。

    ```cmd
    msbuild /t:ValidatePackage ProjectFileName
    ```

     例如，您可以執行下列其中一個命令來驗證名為 ListDefinition1 的 SharePoint 專案。

    ```cmd
    msbuild /t:ValidatePackage ListDefinition1.vbproj
    msbuild /t:ValidatePackage ListDefinition1.csproj
    ```

## <a name="set-properties-in-a-sharepoint-package"></a>設定 SharePoint 封裝中的屬性

#### <a name="to-set-a-property-in-a-sharepoint-package"></a>若要設定 SharePoint 封裝中的屬性

1. 開啟 [命令提示字元] 視窗。

2. 切換至 SharePoint 專案所在的目錄。

3. 輸入下列命令，在專案的封裝中設定屬性。 將*PropertyName*取代為您要設定的屬性。

    ```cmd
    msbuild /property:PropertyName=Value
    ```

     例如，您可以執行下列命令來設定警告層級。

    ```cmd
    msbuild /property:WarningLevel = 2
    ```

## <a name="see-also"></a>另請參閱
- [建立 SharePoint 功能](../sharepoint/creating-sharepoint-features.md)
- [如何：自訂 SharePoint 功能](../sharepoint/how-to-customize-a-sharepoint-feature.md)
- [如何：在 SharePoint 功能中加入和移除專案](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)
