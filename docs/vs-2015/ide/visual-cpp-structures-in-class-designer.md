---
title: 類別設計工具中的 Visual C++ 結構 | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Class Designer [Visual Studio], structures
ms.assetid: bad18ab6-d956-47a6-a413-811cc26db5f5
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a701aae6e9c504d24d149dd5941a0f9623111ce2
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47486816"
---
# <a name="visual-c-structures-in-class-designer"></a>類別設計工具中的 Visual C++ 結構
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[類別設計工具中的 Visual c + + 結構](https://docs.microsoft.com/visualstudio/ide/visual-cpp-structures-in-class-designer)。  
  
類別設計工具支援 C++ 結構，其使用 `struct` 關鍵字所宣告。 以下是一個範例：  
  
```  
struct MyStructure  
{  
   char a;  
   int i;  
   long j;  
};  
```  
  
 如需使用 `struct` 類型的詳細資訊，請參閱 [struct](http://msdn.microsoft.com/library/3c6ba273-e248-4ff1-8c69-d2abcf1263c6)。  
  
 類別圖表中的 C++ 結構圖形外觀和運作方式類似類別圖形，不同之處在於標籤會讀為 **Struct**，而且有方角而非圓角。  
  
|Code 項目|類別設計工具檢視|  
|------------------|-------------------------|  
|`struct StructureName {};`|**StructureName**<br /><br /> 結構|  
  
## <a name="see-also"></a>另請參閱  
 [使用 Visual C++ 程式碼 (類別設計工具)](../ide/working-with-visual-cpp-code-class-designer.md)   
 [類別和結構](http://msdn.microsoft.com/library/516dd496-13fb-4f17-845a-e9ca45437873)   
 [struct](http://msdn.microsoft.com/library/3c6ba273-e248-4ff1-8c69-d2abcf1263c6)



