---
title: HOW TO：在 MSBuild 中逸出特殊字元 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- special characters, escaping
- characters, escapes
- escape characters
- MSBuild, escaping special characters
ms.assetid: 1aa3669c-1647-4960-b770-752e2532102f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5e6af51127548b59646ec7243863491115b77e08
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53854616"
---
# <a name="how-to-escape-special-characters-in-msbuild"></a>HOW TO：在 MSBuild 中逸出特殊字元

某些字元在 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 專案檔中具有特殊意義。 這些字元的範例包括分號 (`;`) 和星號 (`*`)。 如需這些特殊字元的完整清單，請參閱 [MSBuild 特殊字元](../msbuild/msbuild-special-characters.md)。
  
若要使用這些特殊字元作為專案檔中的常值，就必須使用 `%<xx>` 語法來指定它們，其中 `<xx>` 代表字元的 ASCII 十六進位值。
  
## <a name="msbuild-special-characters"></a>MSBuild 特殊字元

 使用特殊字元的範例之一是在項目清單的 `Include` 屬性中。 例如，下列項目清單會宣告兩個項目：*MyFile.cs* 和 *MyClass.cs*。  
  
```xml  
<Compile Include="MyFile.cs;MyClass.cs"/>  
```  
  
如果您想要宣告名稱中包含分號的項目，就必須使用 `%<xx>` 語法來逸出分號，並防止 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 宣告兩個個別的項目。 例如，下列項目會逸出分號，並宣告一個名為 `MyFile.cs;MyClass.cs` 的項目。
  
```xml  
<Compile Include="MyFile.cs%3BMyClass.cs"/>  
```  

您也可以使用[屬性函式](../msbuild/property-functions.md)來逸出字串。 例如，這就相當於以上的範例。

```xml
<Compile Include="$([MSBuild]::Escape('MyFile.cs;MyClass.cs'))" />
```

### <a name="to-use-an-msbuild-special-character-as-a-literal-character"></a>使用 MSBuild 特殊字元做為常值字元

請使用標記 `%<xx>` 取代特殊字元，其中 `<xx>` 代表 ASCII 字元的十六進位值。 例如，若要使用星號 (`*`) 作為常值字元，請使用值 `%2A`。

 
## <a name="see-also"></a>另請參閱  
 [MSBuild 概念](../msbuild/msbuild-concepts.md)   
 [MSBuild](../msbuild/msbuild.md)   
 [項目](../msbuild/msbuild-items.md)   
