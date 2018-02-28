---
title: "類別設計工具中的 Visual C++ 列舉 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Class Designer [Visual Studio], enumerations
ms.assetid: 11e90ba1-18cd-44f8-9e26-e3746a7a19d1
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ad55c68e16fcd340d69178dc24a4b92cada9e2f3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="visual-c-enumerations-in-class-designer"></a>類別設計工具中的 Visual C++ 列舉類型
類別設計工具支援 C++ `enum` 和範圍 `enum class` 類型。 以下是一個範例：  
  
```cpp
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
  
如需使用 `enum` 類型的詳細資訊，請參閱[列舉](/cpp/cpp/enumerations-cpp)。  
  
## <a name="see-also"></a>另請參閱
[使用 Visual C++ 程式碼](working-with-visual-cpp-code.md)   
[列舉](/cpp/cpp/enumerations-cpp)