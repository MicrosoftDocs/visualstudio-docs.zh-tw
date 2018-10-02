---
title: T4 CleanUpBehavior 指示詞 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9e5a211f-a3bf-4229-bff0-7d2e45b71c64
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 9b9138ab564c7597715537216333f1efd0f3fc5a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47491089"
---
# <a name="t4-cleanupbehavior-directive"></a>T4 CleanUpBehavior 指示詞
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[T4 CleanUpBehavior 指示詞](https://docs.microsoft.com/visualstudio/modeling/t4-cleanupbehavior-directive)。  
  
若要在處理文字範本後刪除 appDomain，請加入下列幾行：  
  
```  
<#@ CleanupBehavior processor="T4VSHost" CleanupAfterProcessingtemplate="true" #>  
```  
  
 文字範本是在與主機處理序不同的 appDomain 中處理。 大部分情況下，若已處理一個文字範本，則會再次使用 appdomain 處理下一個範本。 但是，如果指定 CleanupBehavior，則會刪除 appDomain，並且會在新的 appDomain 中處理下一個範本。  
  
 這會減緩文字處理的速度，不過，其有助於確保處置資源。  
  
 這個指示詞只能在 Visual Studio 主機中起作用。



