---
title: MSBuild 專案檔案結構描述參考 | Microsoft Docs
description: 查看資料表，其中列出所有 MSBuild XML 架構元素及其可用屬性和子項目。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, file schema
ms.assetid: d9a68146-1f43-4621-ac78-2c8c3f400936
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0f861fd9e5c10946c2bfee0235632c005822cbf1
ms.sourcegitcommit: 55bc9df751a21656de8cc5b6dbd8a2a1915ec690
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/05/2021
ms.locfileid: "99572937"
---
# <a name="msbuild-project-file-schema-reference"></a>MSBuild 專案檔案結構描述參考

提供所有 MSBuild XML 架構元素的資料表及其可用屬性和子項目。

 MSBuild 會使用專案檔來指示組建引擎要建立哪些專案，以及如何建立它。 MSBuild 專案檔案是符合 MSBuild XML 架構的 XML 檔案。 本節說明 MSBuild) 檔案的 XML 架構定義 (*。*

Visual Studio 2017 和更新版本中不需要 MSBuild 專案檔中的架構連結。 如果有的話，則不論 Visual Studio 的版本為何，都應該如此 ` http://schemas.microsoft.com/developer/msbuild/2003` 。

## <a name="msbuild-xml-schema-elements"></a>MSBuild XML 結構描述項目

 下表列出所有的 MSBuild XML 架構元素，以及其子項目和屬性。

|元素|子元素|屬性|
|-------------|--------------------|----------------|
|[Choose 項目 (MSBuild)](../msbuild/choose-element-msbuild.md)|Otherwise<br /><br /> 當|--|
|[Import 項目 (MSBuild)](../msbuild/import-element-msbuild.md)|--|條件<br /><br /> Project|
|[ImportGroup 項目](../msbuild/importgroup-element.md)|匯入|條件|
|[Item 項目 (MSBuild)](../msbuild/item-element-msbuild.md)|*ItemMetaData*|條件<br /><br /> 排除<br /><br /> 包含<br /><br /> 移除|
|[MSBuild)  (ItemDefinitionGroup 元素 ](../msbuild/itemdefinitiongroup-element-msbuild.md)|*Item*|條件|
|[ItemGroup 項目 (MSBuild)](../msbuild/itemgroup-element-msbuild.md)|*Item*|條件|
|[ItemMetadata 項目 (MSBuild)](../msbuild/itemmetadata-element-msbuild.md)|*Item*|條件|
|[ (MSBuild) 的 OnError 元素 ](../msbuild/onerror-element-msbuild.md)|--|條件<br /><br /> ExecuteTargets|
|[Otherwise 元素 (MSBuild)](../msbuild/otherwise-element-msbuild.md)|Choose<br /><br /> ItemGroup<br /><br /> PropertyGroup|--|
|[ (MSBuild) 的 Output 元素 ](../msbuild/output-element-msbuild.md)|--|條件<br /><br /> ItemName<br /><br /> PropertyName<br /><br /> TaskParameter|
|[Parameter 元素](../msbuild/parameter-element.md)|--|輸出<br /><br /> ParameterType<br /><br /> 必要|
|[ParameterGroup 元素](../msbuild/parametergroup-element.md)|*參數*|--|
|[ (MSBuild) 的專案元素 ](../msbuild/project-element-msbuild.md)|Choose<br /><br /> 匯入<br /><br /> ItemGroup<br /><br /> ProjectExtensions<br /><br /> PropertyGroup<br /><br /> 目標<br /><br /> UsingTask|DefaultTargets<br /><br /> InitialTargets<br /><br /> Sdk<br /><br /> ToolsVersion<br /><br /> TreatAsLocalProperty<br /><br /> xmlns|
|[MSBuild)  (ProjectExtensions 元素 ](../msbuild/projectextensions-element-msbuild.md)|--|--|
|[MSBuild)  (Property 元素 ](../msbuild/property-element-msbuild.md)|--|條件|
|[MSBuild)  (PropertyGroup 元素 ](../msbuild/propertygroup-element-msbuild.md)|*屬性*|條件|
|[MSBuild)  (Sdk 元素 ](../msbuild/sdk-element-msbuild.md)|--|名稱<br /><br /> 版本|
|[MSBuild)  (目標元素 ](../msbuild/target-element-msbuild.md)|OnError<br /><br /> *Task*|AfterTargets<br /><br /> BeforeTargets<br /><br /> 條件<br /><br /> DependsOnTargets<br /><br /> 輸入<br /><br /> KeepDuplicateOutputs<br /><br /> Name<br /><br /> 輸出<br /><br /> 傳回|
|[目標 (MSBuild) 的 Task 元素 ](../msbuild/task-element-msbuild.md)|輸出|條件<br /><br /> ContinueOnError<br /><br /> *參數*|
|[UsingTask (MSBuild) 的 Task 元素 ](../msbuild/taskbody-element-msbuild.md)|*資料*|評估|
|[MSBuild)  (UsingTask 元素 ](../msbuild/usingtask-element-msbuild.md)|ParameterGroup<br /><br /> Task|AssemblyFile<br /><br /> AssemblyName<br /><br /> 條件<br /><br /> TaskFactory<br /><br /> TaskName|
|[當元素 (MSBuild 時) ](../msbuild/when-element-msbuild.md)|Choose<br /><br /> ItemGroup<br /><br /> PropertyGroup|條件|

## <a name="see-also"></a>另請參閱

- [工作參考](../msbuild/msbuild-task-reference.md)
- [條件](../msbuild/msbuild-conditions.md)
- [MSBuild 參考](../msbuild/msbuild-reference.md)
- [MSBuild](../msbuild/msbuild.md)
