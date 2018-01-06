---
title: "如何： 使用 MSBuild 工作建立 SharePoint 方案套件 |Microsoft 文件"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords: SharePoint development in Visual Studio, packages
ms.assetid: c3880bdd-f0a1-4d53-9a97-5767cb3f7b8e
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 827566ddf888b430a1e46c26633dfe6fbf919af8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks"></a>如何：使用 MSBuild 工作建立 SharePoint 方案套件
  您可以建置、 清除及驗證 SharePoint 套件 (.wsp) 的開發電腦上使用命令列的 MSBuild 工作。 您也可以使用這些命令來自動化組建電腦上使用 Team Foundation Server 的建置程序。  
  
## <a name="building-a-sharepoint-package"></a>建立 SharePoint 封裝  
  
#### <a name="to-build-a-sharepoint-package"></a>若要建置 SharePoint 套件  
  
1.  在 Windows**啟動**功能表上，選擇**所有程式**，**附屬應用程式**，**命令提示字元**。  
  
2.  切換至您的 SharePoint 專案所在的目錄。  
  
3.  輸入下列命令以建立專案的封裝。 取代*ProjectFileName*與專案的名稱。  
  
    ```  
    msbuild /t:Package ProjectFileName  
    ```  
  
     比方說，您可以執行下列命令之一來封裝呼叫 ListDefinition1 SharePoint 專案。  
  
    ```  
    msbuild /t:Package ListDefinition1.vbproj  
    msbuild /t:Package ListDefinition1.csproj  
    ```  
  
## <a name="cleaning-a-sharepoint-package"></a>清除 SharePoint 套件  
  
#### <a name="to-clean-a-sharepoint-package"></a>若要清理 SharePoint 套件  
  
1.  開啟 [命令提示字元] 視窗。  
  
2.  切換至您的 SharePoint 專案所在的目錄。  
  
3.  輸入下列命令，以清理專案的封裝。 取代*ProjectFileName*與專案的名稱。  
  
    ```  
    msbuild /t:CleanPackage ProjectFileName  
    ```  
  
     例如，您可以執行下列命令來清除呼叫 ListDefinition1 SharePoint 專案的其中一個。  
  
    ```  
    msbuild /t:CleanPackage ListDefinition1.vbproj  
    msbuild /t:CleanPackage ListDefinition1.csproj  
    ```  
  
## <a name="validating-a-sharepoint-package"></a>驗證 SharePoint 封裝  
  
#### <a name="to-validate-a-sharepoint-package"></a>若要驗證 SharePoint 封裝  
  
1.  開啟 [命令提示字元] 視窗。  
  
2.  切換至您的 SharePoint 專案所在的目錄。  
  
3.  輸入下列命令來驗證專案的封裝。 取代*ProjectFileName*與專案的名稱。  
  
    ```  
    msbuild /t:ValidatePackage ProjectFileName  
    ```  
  
     例如，您可以執行下列命令之一來驗證呼叫 ListDefinition1 SharePoint 專案。  
  
    ```  
    msbuild /t:ValidatePackage ListDefinition1.vbproj  
    msbuild /t:ValidatePackage ListDefinition1.csproj  
    ```  
  
## <a name="setting-properties-in-a-sharepoint-package"></a>設定 SharePoint 封裝的屬性  
  
#### <a name="to-set-a-property-in-a-sharepoint-package"></a>若要設定 SharePoint 套件中的屬性  
  
1.  開啟 [命令提示字元] 視窗。  
  
2.  切換至您的 SharePoint 專案所在的目錄。  
  
3.  輸入下列命令以設定專案的封裝中的屬性。 取代*PropertyName*與您想要設定的屬性。  
  
    ```  
    msbuild /property:PropertyName=Value  
    ```  
  
     例如，您可以執行下列命令以設定警告層級。  
  
    ```  
    msbuild /property:WarningLevel = 2  
    ```  
  
## <a name="see-also"></a>請參閱  
 [建立 SharePoint 功能](../sharepoint/creating-sharepoint-features.md)   
 [如何： 自訂 SharePoint 功能](../sharepoint/how-to-customize-a-sharepoint-feature.md)   
 [如何：新增與移除 SharePoint 功能中的項目](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)  
  
  