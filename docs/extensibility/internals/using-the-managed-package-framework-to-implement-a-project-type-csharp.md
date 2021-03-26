---
title: '使用 Managed Package Framework 作為專案類型 (c # ) '
description: 深入瞭解 Managed Package Framework，它會提供您可以使用或繼承自的 .NET 類別，以執行您自己的專案類型。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], creating with MPF
- MPF projects
- managed package framework, creating projects
ms.assetid: 926de536-eead-415b-9451-f1ddc8c44630
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: cb047c9ef8c5c47c6509a6a5947be77a488e22f5
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105060727"
---
# <a name="using-the-managed-package-framework-to-implement-a-project-type-c"></a>使用受控套件架構實作專案類型 (C#)
Managed Package Framework (MPF) 提供可供您使用或繼承的 c # 類別，以執行您自己的專案類型。 MPF 會實 Visual Studio 預期要提供專案類型的許多介面，讓您可以自由地專注于實現專案類型的各項細節。

## <a name="using-the-mpf-project-source-code"></a>使用 MPF 專案來源程式碼
 適用于專案的 Managed 封裝架構 (MPFProj) 提供協助程式類別來建立和管理新的專案系統。 與 MPF 中的其他類別不同的是，專案類別不包含在隨附于 Visual Studio 的元件中。 相反地，專案類別會在 [適用于專案2013的 MPF](https://github.com/tunnelvisionlabs/MPFProj10)上以原始程式碼的形式提供。

 若要將此專案新增至您的 VSPackage 方案，請執行下列動作：

1. 將 MPFProj 檔案下載至 *MPFProjectDir*。

2. 在 [ *MPFProjectDir*] \Dev10\Src\CSharp\ProjectBase.file 中，變更下列區塊：

```
<!-- Provide a default value for $(ProjectBasePath) -->
  <PropertyGroup>
    <ProjectBasePath >MPFProjDir\Dev10\Src\CSharp</ProjectBasePath>
  </PropertyGroup>
```

1. 建立 VSPackage 專案。

2. 卸載 VSPackage 專案。

3. 在其他區塊之前新增下列區塊，以編輯 VSPackage .csproj 檔案 `<Import>` ：

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

4. 將下列參考加入至 VSPackage 專案：

     Microsoft. v4。0

5. 建置專案。

## <a name="hierarchy-classes"></a>階層類別
 下表摘要說明 MPFProj 中支援專案階層的類別。 如需詳細資訊，請參閱階層 [和選取](../../extensibility/internals/hierarchies-and-selection.md)。

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

## <a name="document-handling-classes"></a>Document-Handling 類別
 下表列出支援檔處理的 MPF 中的類別。 如需詳細資訊，請參閱 [開啟和儲存專案專案](../../extensibility/internals/opening-and-saving-project-items.md)。

|類別名稱|
|----------------|
|`Microsoft.VisualStudio.Package.DocumentManager`|
|`Microsoft.VisualStudio.Package.FileDocumentManager`|

## <a name="configuration-and-output-classes"></a>設定和輸出類別
 下表列出 MPF 中的類別，可讓專案類型支援多個設定，例如，debug 和 release 和專案輸出集合。 如需詳細資訊，請參閱 [管理設定選項](../../extensibility/internals/managing-configuration-options.md)。

|類別名稱|
|----------------|
|`Microsoft.VisualStudio.Package.ConfigProvider`|
|`Microsoft.VisualStudio.Package.ProjectConfig`|
|`Microsoft.VisualStudio.Package.BuildableProjectConfig`|
|`Microsoft.VisualStudio.Package.OutputGroup`|
|`Microsoft.VisualStudio.Package.ProjectElement`|

## <a name="automation-support-classes"></a>Automation-Support 類別
 下表列出支援自動化的 MPF 中的類別，讓您專案類型的使用者可以撰寫增益集。

|類別名稱|
|----------------|
|`Microsoft.VisualStudio.Package.Automation.OAProject`|
|`Microsoft.VisualStudio.Package.Automation.OANavigableProjectItems`|
|`Microsoft.VisualStudio.Package.Automation.OAProjectItems`|
|`Microsoft.VisualStudio.Package.Automation.OAProjectItem`|
|`Microsoft.VisualStudio.Package.Automation.OANestedProjectItem`|

## <a name="properties-classes"></a>Properties 類別
 下表列出 MPF 中的類別，可讓專案類型新增使用者可以在屬性瀏覽器中流覽和修改的屬性。

|類別名稱|
|----------------|
|`Microsoft.VisualStudio.Package.LocalizableProperties`|
|`Microsoft.VisualStudio.Package.NodeProperties`|
|`Microsoft.VisualStudio.Package.FileNodeProperties`|
|`Microsoft.VisualStudio.Package.ProjectNodeProperties`|
|`Microsoft.VisualStudio.Package.FolderNodeProperties`|
|`Microsoft.VisualStudio.Package.ReferenceNodeProperties`|
