---
title: MSBuild 專案檔案結構描述參考 | Microsoft Docs
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
ms.openlocfilehash: 824a6f562638edb04854431c437289f2741c46d9
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "78263082"
---
# <a name="msbuild-project-file-schema-reference"></a>MSBuild 專案檔案結構描述參考

提供包含可用屬性和子項目的所有 MSBuild XML 架構元素的表。

 MSBuild 使用專案檔案來指示生成引擎要構建什麼以及如何生成它。 MSBuild 專案檔案是符合 MSBuild XML 架構的 XML 檔。 本節記錄 MSBuild 的 XML 架構定義 （*.xsd*） 檔。

Visual Studio 2017 及更高版本不需要 MSBuild 專案檔案中的架構連結。 如果存在，它應該` http://schemas.microsoft.com/developer/msbuild/2003`是不管視覺工作室的版本。

## <a name="msbuild-xml-schema-elements"></a>MSBuild XML 結構描述項目

 下表列出了所有 MSBuild XML 架構元素及其子項目和屬性。

|元素|子元素|屬性|
|-------------|--------------------|----------------|
|[Choose 項目 (MSBuild)](../msbuild/choose-element-msbuild.md)|Otherwise<br /><br /> 當|--|
|[Import 項目 (MSBuild)](../msbuild/import-element-msbuild.md)|--|條件<br /><br /> 隨附此逐步解說的專案|
|[導入組元素](../msbuild/importgroup-element.md)|匯入|條件|
|[Item 項目 (MSBuild)](../msbuild/item-element-msbuild.md)|*ItemMetaData*|條件<br /><br /> 排除<br /><br /> 包含<br /><br /> 移除|
|[專案定義組元素（MSBuild）](../msbuild/itemdefinitiongroup-element-msbuild.md)|*專案*|條件|
|[ItemGroup 項目 (MSBuild)](../msbuild/itemgroup-element-msbuild.md)|*專案*|條件|
|[ItemMetadata 項目 (MSBuild)](../msbuild/itemmetadata-element-msbuild.md)|*專案*|條件|
|[OnError 元素 （MSBuild）](../msbuild/onerror-element-msbuild.md)|--|條件<br /><br /> ExecuteTargets|
|[Otherwise 元素 (MSBuild)](../msbuild/otherwise-element-msbuild.md)|Choose<br /><br /> ItemGroup<br /><br /> PropertyGroup|--|
|[輸出元素 （MSBuild）](../msbuild/output-element-msbuild.md)|--|條件<br /><br /> ItemName<br /><br /> PropertyName<br /><br /> TaskParameter|
|[參數元素](../msbuild/parameter-element.md)|--|輸出<br /><br /> ParameterType<br /><br /> 必要|
|[參陣列元素](../msbuild/parametergroup-element.md)|*參數*|--|
|[專案元素（MSBuild）](../msbuild/project-element-msbuild.md)|Choose<br /><br /> 匯入<br /><br /> ItemGroup<br /><br /> ProjectExtensions<br /><br /> PropertyGroup<br /><br /> 目標<br /><br /> UsingTask|DefaultTargets<br /><br /> InitialTargets<br /><br /> ToolsVersion<br /><br /> TreatAsLocalProperty<br /><br /> xmlns|
|[專案擴展元素 （MSBuild）](../msbuild/projectextensions-element-msbuild.md)|--|--|
|[屬性元素 （MSBuild）](../msbuild/property-element-msbuild.md)|--|條件|
|[屬性組元素 （MSBuild）](../msbuild/propertygroup-element-msbuild.md)|*屬性*|條件|
|[Sdk 元素 （MSBuild）](../msbuild/sdk-element-msbuild.md)|--|名稱<br /><br /> 版本|
|[目標元素 （MSBuild）](../msbuild/target-element-msbuild.md)|OnError<br /><br /> *任務*|AfterTargets<br /><br /> BeforeTargets<br /><br /> 條件<br /><br /> DependsOnTargets<br /><br /> 輸入<br /><br /> KeepDuplicateOutputs<br /><br /> 名稱<br /><br /> 輸出<br /><br /> 傳回值|
|[目標的任務元素 （MSBuild）](../msbuild/task-element-msbuild.md)|輸出|條件<br /><br /> ContinueOnError<br /><br /> *參數*|
|[使用任務的任務元素 （MSBuild）](../msbuild/taskbody-element-msbuild.md)|*資料*|評估|
|[使用任務元素 （MSBuild）](../msbuild/usingtask-element-msbuild.md)|ParameterGroup<br /><br /> Task|AssemblyFile<br /><br /> AssemblyName<br /><br /> 條件<br /><br /> TaskFactory<br /><br /> TaskName|
|[當元素（MSBuild）](../msbuild/when-element-msbuild.md)|Choose<br /><br /> ItemGroup<br /><br /> PropertyGroup|條件|

## <a name="see-also"></a>另請參閱

- [任務引用](../msbuild/msbuild-task-reference.md)
- [條件](../msbuild/msbuild-conditions.md)
- [MSBuild 參考](../msbuild/msbuild-reference.md)
- [MSBuild](../msbuild/msbuild.md)
