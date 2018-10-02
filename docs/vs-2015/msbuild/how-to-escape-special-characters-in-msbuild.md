---
title: 如何：在 MSBuild 中逸出特殊字元 | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- special characters, escaping
- characters, escapes
- escape characters
- MSBuild, escaping special characters
ms.assetid: 1aa3669c-1647-4960-b770-752e2532102f
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a900ebe49e95b512c0f53a5542f0ba8ee238a83f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47498624"
---
# <a name="how-to-escape-special-characters-in-msbuild"></a>如何：在 MSBuild 中逸出特殊字元
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[如何： 在 MSBuild 中逸出特殊字元](https://docs.microsoft.com/visualstudio/msbuild/how-to-escape-special-characters-in-msbuild)。  
  
  
某些字元在 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 專案檔中具有特殊意義。 這些字元範例包括分號 (;) 和星號 (*)。 如需這些特殊字元的完整清單，請參閱 [MSBuild 特殊字元](../msbuild/msbuild-special-characters.md)。  
  
 若要使用這些特殊字元做為專案檔中的常值，就必須使用 %*xx* 語法來指定它們，其中 *xx* 代表字元的 ASCII 十六進位值。  
  
## <a name="msbuild-special-characters"></a>MSBuild 特殊字元  
 使用特殊字元的範例之一是在項目清單的 `Include` 屬性中。 例如，下列項目清單會宣告兩個項目：`MyFile.cs` 和 `MyClass.cs`。  
  
```  
<Compile Include="MyFile.cs;MyClass.cs"/>  
```  
  
 如果您想要宣告名稱中包含分號的項目，就必須使用 %*xx* 語法來逸出分號，並防止 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 宣告兩個個別的項目。 例如，下列項目會逸出分號，並宣告一個名為 `MyFile.cs;MyClass.cs` 的項目。  
  
```  
<Compile Include="MyFile.cs%3BMyClass.cs"/>  
```  
  
#### <a name="to-use-an-msbuild-special-character-as-a-literal-character"></a>使用 MSBuild 特殊字元做為常值字元  
  
-   請使用標記 %*xx* 取代特殊字元，其中 *xx* 代表 ASCII 字元的十六進位值。 例如，若要使用星號 (*) 做為常值字元，請使用值 `%2A`。  
  
## <a name="see-also"></a>另請參閱  
 [MSBuild 概念](../msbuild/msbuild-concepts.md)   
 [MSBuild](msbuild.md) [項目](../msbuild/msbuild-items.md)


