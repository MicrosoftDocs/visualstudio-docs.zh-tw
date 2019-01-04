---
title: HOW TO：使用 MSBuild 工作建立 SharePoint 方案套件 |Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packages
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: a9a954c00c616ff156d786386c92d41dcbe85c13
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53818322"
---
# <a name="how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks"></a>HOW TO：使用 MSBuild 工作建立 SharePoint 方案套件
  您可以建置、 清理及驗證 SharePoint 套件 (*.wsp*) 在開發電腦上使用命令列的 MSBuild 工作。 您也可以使用這些命令，來自動化建置程序使用 Team Foundation Server 組建電腦上。  
  
## <a name="build-a-sharepoint-package"></a>建置 SharePoint 封裝  
  
#### <a name="to-build-a-sharepoint-package"></a>若要建置 SharePoint 套件  
  
1.  在 Windows 上**開始**功能表上，選擇**所有程式** > **附屬應用程式** > **命令提示字元**。  
  
2.  切換至您的 SharePoint 專案所在的目錄。  
  
3.  輸入下列命令來建立專案的套件。 取代*ProjectFileName*專案的名稱。  
  
    ```cmd  
    msbuild /t:Package ProjectFileName  
    ```  
  
     例如，您可以執行下列命令來封裝 SharePoint 專案，稱為 ListDefinition1 的其中一個。  
  
    ```cmd  
    msbuild /t:Package ListDefinition1.vbproj  
    msbuild /t:Package ListDefinition1.csproj  
    ```  
  
## <a name="clean-a-sharepoint-package"></a>清除 SharePoint 封裝  
  
#### <a name="to-clean-a-sharepoint-package"></a>清除 SharePoint 封裝  
  
1.  開啟 [命令提示字元] 視窗。  
  
2.  切換至您的 SharePoint 專案所在的目錄。  
  
3.  輸入下列命令以清除專案的套件。 取代*ProjectFileName*專案的名稱。  
  
    ```cmd  
    msbuild /t:CleanPackage ProjectFileName  
    ```  
  
     例如，您可以執行下列命令來清除呼叫 ListDefinition1 SharePoint 專案的其中一個。  
  
    ```cmd  
    msbuild /t:CleanPackage ListDefinition1.vbproj  
    msbuild /t:CleanPackage ListDefinition1.csproj  
    ```  
  
## <a name="validate-a-sharepoint-package"></a>驗證 SharePoint 套件  
  
#### <a name="to-validate-a-sharepoint-package"></a>若要驗證 SharePoint 套件  
  
1.  開啟 [命令提示字元] 視窗。  
  
2.  切換至您的 SharePoint 專案所在的目錄。  
  
3.  輸入下列命令來驗證專案的套件。 取代*ProjectFileName*專案的名稱。  
  
    ```cmd  
    msbuild /t:ValidatePackage ProjectFileName  
    ```  
  
     例如，您可以執行下列命令來驗證呼叫 ListDefinition1 SharePoint 專案的其中一個。  
  
    ```cmd  
    msbuild /t:ValidatePackage ListDefinition1.vbproj  
    msbuild /t:ValidatePackage ListDefinition1.csproj  
    ```  
  
## <a name="set-properties-in-a-sharepoint-package"></a>在 SharePoint 封裝中設定屬性  
  
#### <a name="to-set-a-property-in-a-sharepoint-package"></a>在 SharePoint 封裝中設定屬性  
  
1.  開啟 [命令提示字元] 視窗。  
  
2.  切換至您的 SharePoint 專案所在的目錄。  
  
3.  輸入下列命令來設定專案的套件中的屬性。 取代*PropertyName*與您想要設定的屬性。  
  
    ```cmd  
    msbuild /property:PropertyName=Value  
    ```  
  
     例如，您可以執行下列命令來設定警告層級。  
  
    ```cmd  
    msbuild /property:WarningLevel = 2  
    ```  
  
## <a name="see-also"></a>另請參閱
 [建立 SharePoint 功能](../sharepoint/creating-sharepoint-features.md)   
 [如何：自訂 SharePoint 功能](../sharepoint/how-to-customize-a-sharepoint-feature.md)   
 [如何：新增和移除 SharePoint 功能的項目](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)  
