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
caps.latest.revision: 13
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 3fb5627d2cc92c36e9dcf34f4b94796b6620321f
ms.openlocfilehash: 86f7fef0365a47e8ea88bc3fc46cb0016efd4628
ms.contentlocale: zh-tw
ms.lasthandoff: 06/15/2017

---
# <a name="customize-your-build"></a>自訂組建
在版本 15 之前的 MSBuild 版本中，如果您想要將新的自訂屬性提供給方案中的專案，則必須手動將該屬性的參考新增至方案中的每個專案檔。 或者，除此之外，您必須在 .props 檔案中定義屬性，然後明確地匯入方案之每個專案中的 .props 檔案。

不過，您現在可以使用一個步驟將新的屬性新增至每個專案，方法是在存放庫根目錄中稱為 Directory.Build.props 的單一檔案中定義它。 執行 MSBuild 時，Microsoft.Common.props 會搜尋您的目錄結構中是否有 Directory.Build.props 檔案 (而且 Microsoft.Common.targets 會尋找 Directory.Build.targets)。 如果找到，則會匯入屬性。 Directory.Build.props 是使用者定義的檔案，可讓您自訂目錄下的專案。

## <a name="directorybuildprops-example"></a>Directory.Build.props 範例
例如，如果您想要讓所有專案存取新的 Roslyn **/deterministic** 功能 (透過 `$(Deterministic)` 屬性公開於 Roslyn CoreCompile 目標中)，則可以執行下列動作。

1. 在存放庫根目錄中建立稱為 Directory.Build.props 的新檔案。
2. 將下列 XML 新增至檔案。

  ```xml
  <Project>
    <PropertyGroup>
      <Deterministic>true</Deterministic>
    </PropertyGroup>
  </Project>
  ```
3. 執行 MSBuild。 您專案之 Microsoft.Common.props 和 Microsoft.Common.targets 的現有匯入會找到檔案，並將其匯入。

## <a name="search-scope"></a>搜尋範圍
搜尋 Directory.Build.props 檔案時，MSBuild 會從專案位置 ($(MSBuildProjectFullPath)) 往上逐步瀏覽目錄結構，並在找到 Directory.Build.props 檔案之後停止。 例如，如果您的 $(MSBuildProjectFullPath) 是 c:\users\username\code\test\case1，則 MSBuild 會在該處開始搜尋，然後往上搜尋目錄結構，直到找到下列目錄結構中的 Directory.Build.props 檔案。

```
c:\users\username\code\test\case1
c:\users\username\code\test
c:\users\username\code
c:\users\username
c:\users
c:\
```
方案檔的位置與 Directory.Build.props 無關。

## <a name="import-order"></a>匯入順序

在 Microsoft.Common.props 中，會極早匯入 Directory.Build.props，因此它無法使用稍後定義的屬性。 因此，請避免參考尚未定義的屬性 (因此會評估為空的)。

從 NuGet 套件匯入 .targets 檔案之後，會從 Microsoft.Common.targets 匯入 Directory.Build.targets。 因此，它可以用來覆寫大部分組建邏輯中所定義的屬性和目標，但有時可能需要在最後匯入之後於專案檔內執行自訂。

## <a name="see-also"></a>另請參閱  
 [MSBuild 概念](../msbuild/msbuild-concepts.md)   
 [MSBuild 參考](../msbuild/msbuild-reference.md)   

