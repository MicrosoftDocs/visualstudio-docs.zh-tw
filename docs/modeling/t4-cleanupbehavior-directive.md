---
title: "T4 CleanUpBehavior 指示詞 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 7df9fb0c4d567e6af4a0ac1ea3d8ab4832ffe5a7
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/09/2018
---
# <a name="t4-cleanupbehavior-directive"></a>T4 CleanUpBehavior 指示詞
若要在處理文字範本後刪除 appDomain，請加入下列幾行：  
  
```  
<#@ CleanupBehavior processor="T4VSHost" CleanupAfterProcessingtemplate="true" #>  
```  
  
 文字範本是在與主機處理序不同的 appDomain 中處理。 大部分情況下，若已處理一個文字範本，則會再次使用 appdomain 處理下一個範本。 但是，如果指定 CleanupBehavior，則會刪除 appDomain，並且會在新的 appDomain 中處理下一個範本。  
  
 這會減緩文字處理的速度，不過，其有助於確保處置資源。  
  
 這個指示詞只能在 Visual Studio 主機中起作用。