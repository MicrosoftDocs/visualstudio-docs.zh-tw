---
title: 對項目型態 (C#) 使用託管包框架 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], creating with MPF
- MPF projects
- managed package framework, creating projects
ms.assetid: 926de536-eead-415b-9451-f1ddc8c44630
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7ca9dda0b699e0f70b0c945ab9ecfe9f9f4dcda6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704114"
---
# <a name="using-the-managed-package-framework-to-implement-a-project-type-c"></a>使用受控套件架構實作專案類型 (C#)
託管包框架 (MPF) 提供可用於或繼承的 C# 類來實現您自己的項目類型。 MPF 實現了 Visual Studio 希望專案類型提供的許多介面,讓您可以自由地專注於實現專案類型的詳細資訊。

## <a name="using-the-mpf-project-source-code"></a>使用 MPF 專案原始碼
 專案管理套件框架 (MPFProj) 提供用於創建和管理新專案系統的幫助程式類。 與 MPF 中的其他類不同,專案類不包括在 Visual Studio 附帶的程式集中。 相反,專案類在[2013 年專案 MPF](https://github.com/tunnelvisionlabs/MPFProj10)中作為原始碼提供。

 要將此專案加入 VSPackage 解決方案,請執行以下操作:

1. 下載 MPFProj 檔案到*MPF 專案迪爾*。

2. 在*MPFProjectDir*[Dev10]Src_CSharp_ProjectBase.檔案中,更改以下塊:

```
<!-- Provide a default value for $(ProjectBasePath) -->
  <PropertyGroup>
    <ProjectBasePath >MPFProjDir\Dev10\Src\CSharp</ProjectBasePath>
  </PropertyGroup>
```

1. 建立 VSPackage 專案。

2. 卸載 VSPackage 專案。

3. 以在其他`<Import>`區塊之前加入以下區塊來編輯 VSPackage .csproj 檔:

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

2. 關閉並重新打開 VSPackage 解決方案。

3. 重新打開 VSPackage 專案。 您應該會看到一個名為 ProjectBase 的新目錄。

4. 新增以下對 VSPackage 專案的引用:

     微軟.生成.任務.4.0

5. 建置專案。

## <a name="hierarchy-classes"></a>層次結構類
 下表總結了 MPFProj 中支援專案層次結構的類。 有關詳細資訊,請參閱[層次結構和選擇](../../extensibility/internals/hierarchies-and-selection.md)。

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
 下表列出了支援文件處理的 MPF 中的類。 有關詳細資訊,請參閱[開啟和儲存項目專案](../../extensibility/internals/opening-and-saving-project-items.md)。

|類別名稱|
|----------------|
|`Microsoft.VisualStudio.Package.DocumentManager`|
|`Microsoft.VisualStudio.Package.FileDocumentManager`|

## <a name="configuration-and-output-classes"></a>設定與輸出類別
 下表列出了 MPF 中的類,這些類允許專案類型支援多種配置,如調試和發佈以及專案輸出集合。 關於詳細資訊,請參考[管理設定選項](../../extensibility/internals/managing-configuration-options.md)。

|類別名稱|
|----------------|
|`Microsoft.VisualStudio.Package.ConfigProvider`|
|`Microsoft.VisualStudio.Package.ProjectConfig`|
|`Microsoft.VisualStudio.Package.BuildableProjectConfig`|
|`Microsoft.VisualStudio.Package.OutputGroup`|
|`Microsoft.VisualStudio.Package.ProjectElement`|

## <a name="automation-support-classes"></a>自動化支援類
 下表列出了支援自動化的 MPF 中的類,以便專案類型的使用者可以編寫載入項。

|類別名稱|
|----------------|
|`Microsoft.VisualStudio.Package.Automation.OAProject`|
|`Microsoft.VisualStudio.Package.Automation.OANavigableProjectItems`|
|`Microsoft.VisualStudio.Package.Automation.OAProjectItems`|
|`Microsoft.VisualStudio.Package.Automation.OAProjectItem`|
|`Microsoft.VisualStudio.Package.Automation.OANestedProjectItem`|

## <a name="properties-classes"></a>屬性類
 下表列出了 MPF 中的類,這些類允許專案類型添加使用者可以在屬性流覽器中流覽和修改的屬性。

|類別名稱|
|----------------|
|`Microsoft.VisualStudio.Package.LocalizableProperties`|
|`Microsoft.VisualStudio.Package.NodeProperties`|
|`Microsoft.VisualStudio.Package.FileNodeProperties`|
|`Microsoft.VisualStudio.Package.ProjectNodeProperties`|
|`Microsoft.VisualStudio.Package.FolderNodeProperties`|
|`Microsoft.VisualStudio.Package.ReferenceNodeProperties`|
