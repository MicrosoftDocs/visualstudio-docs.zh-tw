---
title: T4 CleanUpBehavior 指示詞 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 9e5a211f-a3bf-4229-bff0-7d2e45b71c64
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: f964f37b347d588b1f7e590d918018c50e9f41c0
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58943308"
---
# <a name="t4-cleanupbehavior-directive"></a>T4 CleanUpBehavior 指示詞
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

若要在處理文字範本後刪除 appDomain，請加入下列幾行：  
  
```  
<#@ CleanupBehavior processor="T4VSHost" CleanupAfterProcessingtemplate="true" #>  
```  
  
 文字範本是在與主機處理序不同的 appDomain 中處理。 大部分情況下，若已處理一個文字範本，則會再次使用 appdomain 處理下一個範本。 但是，如果指定 CleanupBehavior，則會刪除 appDomain，並且會在新的 appDomain 中處理下一個範本。  
  
 這會減緩文字處理的速度，不過，其有助於確保處置資源。  
  
 這個指示詞只能在 Visual Studio 主機中起作用。
