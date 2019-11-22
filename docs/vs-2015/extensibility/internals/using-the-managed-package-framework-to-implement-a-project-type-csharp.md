---
title: 使用 Managed 封裝架構來執行專案類型（C#） |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], creating with MPF
- MPF projects
- managed package framework, creating projects
ms.assetid: 926de536-eead-415b-9451-f1ddc8c44630
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 066695c6d94603d0a0474243ed05dece4cc0bd1f
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2019
ms.locfileid: "74300364"
---
# <a name="using-the-managed-package-framework-to-implement-a-project-type-c"></a>使用受控套件架構實作專案類型 (C#)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Managed Package Framework （MPF）提供C#您可以使用或繼承自的類別，以執行您自己的專案類型。 MPF 會執行許多介面，Visual Studio 預期會提供專案類型，讓您自由專注于實作為專案類型的細節。  
  
## <a name="using-the-mpf-project-source-code"></a>使用 MPF 專案原始程式碼  
 適用于專案的 Managed 封裝架構（MPFProj）會提供 helper 類別來建立和管理新的專案系統。 不同于 MPF 中的其他類別，專案類別不會包含在 Visual Studio 隨附的元件中。 相反地，專案類別是以[適用于專案2013之 MPF](https://archive.codeplex.com/?p=mpfproj12)的原始程式碼提供。  
  
 若要將此專案新增至您的 VSPackage 方案，請執行下列動作：  
  
1. 將 MPFProj 檔案下載到*MPFProjectDir*。  
  
2. 在 [ *MPFProjectDir*] \Dev10\Src\CSharp\ProjectBase.file 中，變更下列區塊：  
  
```  
<!-- Provide a default value for $(ProjectBasePath) -->  
  <PropertyGroup>  
    <ProjectBasePath >MPFProjDir\Dev10\Src\CSharp</ProjectBasePath>  
  </PropertyGroup>  
```  
  
1. 建立 VSPackage 專案。  
  
2. 卸載 VSPackage 專案。  
  
3. 在其他 `<Import>` 區塊之前新增下列區塊，以編輯 VSPackage .csproj 檔案：  
  
```  
<Import Project="MPFProjectDir\Dev10\Src\CSharp\ProjectBase.files" />  
  <PropertyGroup>  
    <!--To specify a different registry root to register your package, uncomment the TargetRegistryRoot tag and specify a registry root in it.  
    <TargetRegistryRoot></TargetRegistryRoot>-->  
    <RegisterOutputPackage>true</RegisterOutputPackage>  
    <RegisterWithCodebase>true</RegisterWithCodebase>  
  </PropertyGroup>  
```  
  
1. 儲存專案。  
  
2. 關閉並重新開啟 VSPackage 方案。  
  
3. 重新開啟 VSPackage 專案。 您應該會看到名為 ProjectBase 的新目錄。  
  
4. 將下列參考新增至 VSPackage 專案：  
  
     Microsoft Build. Tasks 4。0  
  
5. 建置專案。  
  
## <a name="hierarchy-classes"></a>階層類別  
 下表摘要說明 MPFProj 中支援專案階層的類別。 如需詳細資訊，請參閱階層[和選取範圍](../../extensibility/internals/hierarchies-and-selection.md)。  
  
|類別名稱|  
|----------------|  
|`Microsoft.VisualStudio.Package.HierarchyNode`|  
|`Microsoft.VisualStudio.Package.ProjectNode`|  
|`Microsoft.VisualStudio.Package.ProjectContainerNode`|  
|`Microsoft.VisualStudio.Package.FileNode`|  
|`Microsoft.VisualStudio.Package.FolderNode`|  
|`Microsoft.VisualStudio.Package.ReferenceContainerNode`|  
|`Microsoft.VisualStudio.Package.ReferenceNode`|  
|`Microsoft.VisualStudio.Package.ProjectReferenceNode`|  
|`Microsoft.VisualStudio.Package.ComReferenceNode`|  
|`Microsoft.VisualStudio.Package.AssemblyReferenceNode`|  
|`Microsoft.VisualStudio.Package.BuildDependency`|  
  
## <a name="document-handling-classes"></a>檔處理類別  
 下表列出支援檔處理之 MPF 中的類別。 如需詳細資訊，請參閱[開啟和儲存專案專案](../../extensibility/internals/opening-and-saving-project-items.md)。  
  
|類別名稱|  
|----------------|  
|`Microsoft.VisualStudio.Package.DocumentManager`|  
|`Microsoft.VisualStudio.Package.FileDocumentManager`|  
  
## <a name="configuration-and-output-classes"></a>設定和輸出類別  
 下表列出 MPF 中可讓專案類型支援多個設定（例如，debug 和 release）和專案輸出集合的類別。 如需詳細資訊，請參閱[管理設定選項](../../extensibility/internals/managing-configuration-options.md)。  
  
|類別名稱|  
|----------------|  
|`Microsoft.VisualStudio.Package.ConfigProvider`|  
|`Microsoft.VisualStudio.Package.ProjectConfig`|  
|`Microsoft.VisualStudio.Package.BuildableProjectConfig`|  
|`Microsoft.VisualStudio.Package.OutputGroup`|  
|`Microsoft.VisualStudio.Package.ProjectElement`|  
  
## <a name="automation-support-classes"></a>自動化-支援類別  
 下表列出支援自動化之 MPF 中的類別，讓專案類型的使用者可以撰寫增益集。  
  
|類別名稱|  
|----------------|  
|`Microsoft.VisualStudio.Package.Automation.OAProject`|  
|`Microsoft.VisualStudio.Package.Automation.OANavigableProjectItems`|  
|`Microsoft.VisualStudio.Package.Automation.OAProjectItems`|  
|`Microsoft.VisualStudio.Package.Automation.OAProjectItem`|  
|`Microsoft.VisualStudio.Package.Automation.OANestedProjectItem`|  
  
## <a name="properties-classes"></a>屬性類別  
 下表列出 MPF 中的類別，可讓專案類型加入使用者可以在屬性瀏覽器中流覽和修改的屬性。  
  
|類別名稱|  
|----------------|  
|`Microsoft.VisualStudio.Package.LocalizableProperties`|  
|`Microsoft.VisualStudio.Package.NodeProperties`|  
|`Microsoft.VisualStudio.Package.FileNodeProperties`|  
|`Microsoft.VisualStudio.Package.ProjectNodeProperties`|  
|`Microsoft.VisualStudio.Package.FolderNodeProperties`|  
|`Microsoft.VisualStudio.Package.ReferenceNodeProperties`|
