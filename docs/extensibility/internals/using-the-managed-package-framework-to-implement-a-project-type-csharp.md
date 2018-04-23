---
title: 使用 Managed 的封裝架構的專案類型 (C#) |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], creating with MPF
- MPF projects
- managed package framework, creating projects
ms.assetid: 926de536-eead-415b-9451-f1ddc8c44630
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 112988f28728d40509a3af0360246a6bb4caef1a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="using-the-managed-package-framework-to-implement-a-project-type-c"></a>使用 Managed 的封裝架構實作專案型別 (C#)
Managed Package Framework (MPF) 提供的 C# 類別可以使用或來實作您自己的專案類型繼承。 MPF 實作許多介面 Visual Studio 必須是專案類型提供，讓您自由地專注於實作您的專案類型的軟體。  
  
## <a name="using-the-mpf-project-source-code"></a>使用 MPF 專案的原始程式碼  
 Managed Package Framework 的專案 (MPFProj) 提供建立和管理新的專案系統的 helper 類別。 不同於其他 MPF 類別時，專案類別不包含在 Visual Studio 隨附的組件中。 相反地，提供在原始碼專案類別[2013 專案的 MPF](http://mpfproj12.codeplex.com)。  
  
 若要將這個專案加入 VSPackage 方案中，執行下列作業：  
  
1.  下載 MPFProj 檔案， *MPFProjectDir*。  
  
2.  在*MPFProjectDir*\Dev10\Src\CSharp\ProjectBase.file，變更下列區塊：  
  
```  
<!-- Provide a default value for $(ProjectBasePath) -->  
  <PropertyGroup>  
    <ProjectBasePath >MPFProjDir\Dev10\Src\CSharp</ProjectBasePath>  
  </PropertyGroup>  
```  
  
1.  建立 VSPackage 專案。  
  
2.  卸載 VSPackage 專案。  
  
3.  藉由新增下列區塊之前的其他編輯 VSPackage.csproj 檔案`<Import>`區塊：  
  
```  
<Import Project="MPFProjectDir\Dev10\Src\CSharp\ProjectBase.files" />  
  <PropertyGroup>  
    <!--To specify a different registry root to register your package, uncomment the TargetRegistryRoot tag and specify a registry root in it.  
    <TargetRegistryRoot></TargetRegistryRoot>-->  
    <RegisterOutputPackage>true</RegisterOutputPackage>  
    <RegisterWithCodebase>true</RegisterWithCodebase>  
  </PropertyGroup>  
```  
  
1.  儲存專案。  
  
2.  關閉並重新開啟 VSPackage 方案。  
  
3.  重新開啟 VSPackage 專案。 您應該會看到一個名為 ProjectBase 的新目錄。  
  
4.  加入 VSPackage 專案的下列參考：  
  
     Microsoft.Build.Tasks.4.0  
  
5.  建置專案。  
  
## <a name="hierarchy-classes"></a>階層架構類別  
 下表摘要說明 MPFProj 支援專案階層架構的類別。 如需詳細資訊，請參閱[階層和選取範圍](../../extensibility/internals/hierarchies-and-selection.md)。  
  
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
  
## <a name="document-handling-classes"></a>文件處理類別  
 下表列出在 MPF 類別，可支援文件處理。 如需詳細資訊，請參閱[開啟和儲存的專案項目](../../extensibility/internals/opening-and-saving-project-items.md)。  
  
|類別名稱|  
|----------------|  
|`Microsoft.VisualStudio.Package.DocumentManager`|  
|`Microsoft.VisualStudio.Package.FileDocumentManager`|  
  
## <a name="configuration-and-output-classes"></a>組態和輸出類別  
 下表列出 MPF 可讓專案類型支援多個組態，例如偵錯和發行版本，以及專案輸出的集合中的類別。 如需詳細資訊，請參閱[管理組態選項](../../extensibility/internals/managing-configuration-options.md)。  
  
|類別名稱|  
|----------------|  
|`Microsoft.VisualStudio.Package.ConfigProvider`|  
|`Microsoft.VisualStudio.Package.ProjectConfig`|  
|`Microsoft.VisualStudio.Package.BuildableProjectConfig`|  
|`Microsoft.VisualStudio.Package.OutputGroup`|  
|`Microsoft.VisualStudio.Package.ProjectElement`|  
  
## <a name="automation-support-classes"></a>自動化支援類別  
 下表列出 MPF 支援自動化，以便您的專案類型的使用者可以撰寫增益集的類別。  
  
|類別名稱|  
|----------------|  
|`Microsoft.VisualStudio.Package.Automation.OAProject`|  
|`Microsoft.VisualStudio.Package.Automation.OANavigableProjectItems`|  
|`Microsoft.VisualStudio.Package.Automation.OAProjectItems`|  
|`Microsoft.VisualStudio.Package.Automation.OAProjectItem`|  
|`Microsoft.VisualStudio.Package.Automation.OANestedProjectItem`|  
  
## <a name="properties-classes"></a>屬性類別  
 下表列出 MPF 可讓專案類型中的類別加入的使用者可以瀏覽並修改屬性瀏覽器中的屬性。  
  
|類別名稱|  
|----------------|  
|`Microsoft.VisualStudio.Package.LocalizableProperties`|  
|`Microsoft.VisualStudio.Package.NodeProperties`|  
|`Microsoft.VisualStudio.Package.FileNodeProperties`|  
|`Microsoft.VisualStudio.Package.ProjectNodeProperties`|  
|`Microsoft.VisualStudio.Package.FolderNodeProperties`|  
|`Microsoft.VisualStudio.Package.ReferenceNodeProperties`|