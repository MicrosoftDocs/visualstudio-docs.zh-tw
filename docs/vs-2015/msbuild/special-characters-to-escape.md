---
title: 要逸出的特殊字元 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- special characters to escape
- msbuild, special characters to escape
ms.assetid: 5b5172c3-41e4-4f38-a16f-2aeac831a5fc
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: beeed84db240ecf57ca18dd9aef08622f14b06fc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68161346"
---
# <a name="special-characters-to-escape"></a>要逸出的特殊字元
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

只有正在使用特殊字元的內容中，特殊字元具有特殊意義時，才必須逸出。 例如，星號 (*) 只有在項目定義的 "Include" 和 "Exclude" 屬性中，或是呼叫  <xref:Microsoft.Build.Tasks.CreateItem> 時，才是特殊字元。 在其他情況下，星號會視為星號常值。 雖然您不需要逸出專案檔中的所有星號，但要這麼做也無妨。  
  
 請使用標記 %*xx* 取代特殊字元，其中 *xx* 代表 ASCII 字元的十六進位值。 例如，若要使用星號 (*) 做為常值字元，請使用值 `%2A`。  
  
 要逸出的特殊字元完整清單如下：  
  
|字元|描述|  
|---------------|-----------------|  
|%|百分比符號，用以參考中繼資料。|  
|$|錢幣符號，用以參考屬性。|  
|@|@ 記號，用以參考項目清單。|  
|(|左括號，用於清單中。|  
|)|右括號，用於清單中。|  
|`|所有格符號 (或刻度標記)，用於條件運算式和其他運算式。|  
|;|分號，清單分隔字元。|  
|?|問號，在項目的 Include/Exclude 區段中描述檔案規格時為萬用字元。|  
|*|星號，在項目的 Include/Exclude 區段中描述檔案規格時為萬用字元。|  
  
## <a name="see-also"></a>另請參閱  
 [如何：在 MSBuild 中 Escape 特殊字元](../msbuild/how-to-escape-special-characters-in-msbuild.md)   
 [MSBuild 參考](../msbuild/msbuild-reference.md)
