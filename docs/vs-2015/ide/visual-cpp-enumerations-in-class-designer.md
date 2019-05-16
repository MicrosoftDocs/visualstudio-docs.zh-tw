---
title: 類別設計工具中的 Visual C++ 列舉 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Class Designer [Visual Studio], enumerations
ms.assetid: 11e90ba1-18cd-44f8-9e26-e3746a7a19d1
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: b38d36c1fdc0033115f1d7a4cf18265dc1f2a3ab
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65696355"
---
# <a name="visual-c-enumerations-in-class-designer"></a>類別設計工具中的 Visual C++ 列舉類型
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

類別設計工具支援 C++ `enum` 和範圍 `enum class` 類型。 以下是一個範例：  
  
```  
enum CardSuit {  
   Diamonds = 1,  
   Hearts = 2,  
   Clubs = 3,  
   Spades = 4  
};  
  
// or...  
enum class CardSuit {  
   Diamonds = 1,  
   Hearts = 2,  
   Clubs = 3,  
   Spades = 4  
};  
  
```  
  
 類別圖表中的 C++ 列舉圖形外觀和運作方式與結構圖形類似，不同之處在於標籤為「列舉」或「列舉類別」、它是粉紅色而不是藍色，而且它的左和上邊界具有有色框線。 列舉圖形和結構圖形都有方角。  
  
 如需使用 `enum` 類型的詳細資訊，請參閱[列舉](https://msdn.microsoft.com/library/081829db-5dca-411e-a53c-bffef315bcb3)。  
  
## <a name="see-also"></a>請參閱  
 [使用 Visual C++ 程式碼 (類別設計工具)](../ide/working-with-visual-cpp-code-class-designer.md)   
 [列舉](https://msdn.microsoft.com/library/081829db-5dca-411e-a53c-bffef315bcb3)
