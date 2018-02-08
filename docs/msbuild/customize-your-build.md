---
title: "自訂組建 | Microsoft Docs"
ms.custom: 
ms.date: 06/14/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MSBuild, transforms
- transforms [MSBuild]
ms.assetid: d0bceb3b-14fb-455c-805a-63acefa4b3ed
caps.latest.revision: 
author: kempb
ms.author: kempb
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 82b7503b937babd81a41136656d75c95e844b94c
ms.sourcegitcommit: 062795f922e7b59fe00d3d95a01a9a8a28840017
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2018
---
# <a name="customize-your-build"></a>自訂組建
在版本 15 之前的 MSBuild 版本中，如果您想要將新的自訂屬性提供給方案中的專案，則必須手動將該屬性的參考新增至方案中的每個專案檔。 或者，除此之外，您必須在 *.props* 檔案中定義屬性，然後明確地匯入方案之每個專案中的 *.props* 檔案。

不過，您現在可以使用一個步驟將新的屬性新增至每個專案，方法是將它定義在存放庫根目錄中稱為 *Directory.Build.props* 的單一檔案中。 執行 MSBuild 時，*Microsoft.Common.props* 會搜尋您的目錄結構中是否有 *Directory.Build.props* 檔案 (而且 *Microsoft.Common.targets* 會尋找 *Directory.Build.targets*)。 如果找到，則會匯入屬性。 *Directory.Build.props* 是使用者定義的檔案，可讓您自訂目錄下的專案。

## <a name="directorybuildprops-example"></a>Directory.Build.props 範例
例如，如果您想要讓所有專案存取新的 Roslyn **/deterministic** 功能 (透過 `$(Deterministic)` 屬性公開於 Roslyn `CoreCompile` 目標中)，則可以執行下列動作。

1. 在存放庫根目錄中建立稱為 *Directory.Build.props* 的新檔案。
2. 將下列 XML 新增至檔案。

  ```xml
  <Project>
    <PropertyGroup>
      <Deterministic>true</Deterministic>
    </PropertyGroup>
  </Project>
  ```
3. 執行 MSBuild。 您專案之 *Microsoft.Common.props* 和 *Microsoft.Common.targets* 的現有匯入會找到檔案，並將它匯入。

## <a name="search-scope"></a>搜尋範圍
搜尋 *Directory.Build.props* 檔案時，MSBuild 會從專案位置 (`$(MSBuildProjectFullPath)`) 往上逐步瀏覽目錄結構，並在找到 *Directory.Build.props* 檔案之後停止。 例如，如果您的 `$(MSBuildProjectFullPath)` 是 *c:\users\username\code\test\case1*，則 MSBuild 會在該處開始搜尋，然後往上搜尋目錄結構，直到找到下列目錄結構中的 *Directory.Build.props* 檔案。

```
c:\users\username\code\test\case1
c:\users\username\code\test
c:\users\username\code
c:\users\username
c:\users
c:\
```
方案檔的位置與 *Directory.Build.props* 無關。

## <a name="import-order"></a>匯入順序

在 *Microsoft.Common.props* 中，因為 *Directory.Build.props* 很早就會被匯入，所以它無法使用較晚才定義的屬性。 因此，請避免參考尚未定義的屬性 (因此會評估為空的)。

從 NuGet 套件匯入 *.targets* 檔案之後，會從 *Microsoft.Common.targets* 匯入 *Directory.Build.targets*。 因此，它可以用來覆寫大部分組建邏輯中所定義的屬性和目標，但有時可能需要在最後匯入之後於專案檔內執行自訂。

## <a name="use-case-multi-level-merging"></a>使用案例：多層級合併

假設您有這種標準方案結構：

````
\
  MySolution.sln
  Directory.Build.props     (1)
  \src
    Directory.Build.props   (2-src)
    \Project1
    \Project2
  \test
    Directory.Build.props   (2-test)
    \Project1Tests
    \Project2Tests
````

使用者可能需要所有專案 *(1)* 的通用屬性、*src* 專案 *(2-src)* 的通用屬性和 *test* 專案 *(2-test)* 的通用屬性。

若要讓 MSBuild 正確合併「內部」檔案 (*2-src* 和 *2-test*) 與「外部」檔案 (*1*)，您必須注意，一旦 MSBuild 找到 *Directory.Build.props* 檔案，就會停止進一步掃描。 若要繼續掃描並合併至外部檔案，請將此項目放入這兩個內部檔案中：

`<Import Project="$([MSBuild]::GetPathOfFileAbove('Directory.Build.props', '$(MSBuildThisFileDirectory)../'))" />`

MSBuild 的一般方法摘要如下：

- 針對任何指定的專案，MSBuild 會在方案結構中向上尋找第一個 *Directory.Build.props*，再將它與預設值合併，然後停止進一步掃描
- 如果您想要找到多個層級並加以合併，請從「內部」檔案對「外部」檔案進行 [`<Import...>`](../msbuild/property-functions.md#msbuild-getpathoffileabove) 作業 (如上所示)
- 如果「外部」檔案本身不會在其上匯入任何項目，掃描就會到此停止
- 若要控制掃描/合併程序，請使用 `$(DirectoryBuildPropsPath)` 和 `$(ImportDirectoryBuildProps)`

或更簡單的做法：第一個不會匯入任何項目的 *Directory.Build.props*，則為 MSBuild 停止的位置。

## <a name="see-also"></a>請參閱  
 [MSBuild 概念](../msbuild/msbuild-concepts.md)   
 [MSBuild 參考](../msbuild/msbuild-reference.md)   
