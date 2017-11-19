---
title: "如何： 使用功能表項目隱藏警告 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- warnings, suppressing
- code analysis, suppressing warnings
ms.assetid: 36bd1850-dcde-4ed0-9bc3-0b83df434362
caps.latest.revision: "24"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a197170285a8f8a9d3f0cc01638557f30fd1f126
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-suppress-warnings-by-using-the-menu-item"></a>如何：使用功能表項目隱藏警告
> [!NOTE]
>  在來源中隱藏項目不支援的網站專案。  
  
 您可以使用 [程式碼分析] 視窗來隱藏程式碼分析警告。 隱藏警告不相同於停用它。 當您隱藏警告時，它只適用於特定違規的執行個體。 在 [錯誤清單] 視窗中，還是會回報其他違規的相同警告。  
  
 執行程式碼分析之後，您可能決定一或多個程式碼分析 視窗中會顯示程式碼分析警告不適用您的應用程式。 例如，您可能會判斷程式碼不正確無誤。 或者，它可能會有些違規是低優先順序，並將不會在目前的開發週期中修正的情況。 因此，不論是表示警告不適用，可讓您知道此程式碼已檢閱，以及它所決定，無法隱藏警告的小組成員通常很有用。 來源中隱藏項目是很有用，因為它可讓您將會產生警告接近隱藏項目。  
  
 您可以選擇是否隱藏項目會出現在原始碼或全域隱藏項目檔中。 有些隱藏項目必須放入全域隱藏項目檔案。 如果這種情況，**在原始程式檔**選項將停用。  
  
### <a name="to-suppress-a-warning-by-using-menu-item"></a>使用功能表項目隱藏警告  
  
1.  在**分析**功能表上，選擇**Windows** ，然後選擇 **程式碼分析**。  
  
2.  在**程式碼分析**視窗中，選取警告隱藏。  
  
3.  選擇的動作，然後選擇 **隱藏訊息**，然後選擇 **在原始程式檔**或**專案隱藏項目檔中**。  
  
     隱藏特定的警告時，並加上刪除線的 [程式碼分析] 視窗中出現的警告。  
  
> [!NOTE]
>  不需要為目標的隱藏項目會出現在全域隱藏項目檔案。