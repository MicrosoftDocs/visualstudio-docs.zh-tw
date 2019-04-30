---
title: HOW TO：使用功能表項目隱藏警告 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- warnings, suppressing
- code analysis, suppressing warnings
ms.assetid: 36bd1850-dcde-4ed0-9bc3-0b83df434362
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 5097ecb0f7458e739def275d616eb344a2a6db0d
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63426560"
---
# <a name="how-to-suppress-warnings-by-using-the-menu-item"></a>HOW TO：使用功能表項目隱藏警告
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

注意]
> 在來源中隱藏項目不支援適用於網站專案。  
  
 若要隱藏程式碼分析警告，您可以使用 [程式碼分析] 視窗。 隱藏警告不同時停用它。 當您隱藏警告時，它只適用於特定的執行個體的違規。 在 [錯誤清單] 視窗中仍會報告相同的警告的其他違規。  
  
 執行程式碼分析之後，您可能決定一或多個程式碼分析 視窗中會顯示程式碼分析警告並不適用於您的應用程式。 例如，您可能會判斷程式碼是正確無誤。 或者，它可能是某些違規是低優先順序，並不會在目前開發週期中修正的情況。 不論原因，就表示警告不適用，可讓您知道程式碼已經過檢閱，以及它已決定，可以隱藏警告的小組成員通常很有用。 在來源中隱藏項目是很有用，因為它可讓您將會產生警告接近隱藏項目。  
  
 您可以選擇隱藏項目是否會出現在原始程式碼中，或在全域隱藏項目檔中。 有些隱藏項目必須放在全域隱藏項目檔案。 如果此情況下，**在原始程式檔**選項將會停用。  
  
### <a name="to-suppress-a-warning-by-using-menu-item"></a>使用功能表項目隱藏警告  
  
1. 在 **分析**功能表上，選擇**Windows** ，然後選擇 **程式碼分析**。  
  
2. 在 [**程式碼分析**] 視窗中，選取警告隱藏。  
  
3. 選擇 動作，然後選擇**隱藏訊息**，然後選擇 **在原始程式檔**或是**專案隱藏項目檔中的流程範本**。  
  
     隱藏特定警告，並加上刪除線的 [程式碼分析] 視窗中出現的警告。  
  
> [!NOTE]
> 沒有為目標的隱藏項目會出現在全域隱藏項目檔案。
