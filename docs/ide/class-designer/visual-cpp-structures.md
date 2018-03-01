---
title: "類別設計工具中的 Visual C++ 結構 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Class Designer [Visual Studio], structures
ms.assetid: bad18ab6-d956-47a6-a413-811cc26db5f5
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d6f2aa3893a230abd52dd5cf19ed9d751e56e50c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="visual-c-structures-in-class-designer"></a>類別設計工具中的 Visual C++ 結構
類別設計工具支援 C++ 結構，其使用 `struct` 關鍵字所宣告。 以下是一個範例：  
  
```cpp
struct MyStructure  
{  
   char a;  
   int i;  
   long j;  
};  
```  
  
如需使用 `struct` 類型的詳細資訊，請參閱 [struct](/cpp/cpp/struct-cpp)。  
  
類別圖表中的 C++ 結構圖形外觀和運作方式類似類別圖形，不同之處在於標籤會讀為 **Struct**，而且有方角而非圓角。  
  
|Code 項目|類別設計工具檢視|  
|------------------|-------------------------|  
|`struct StructureName {};`|**StructureName**<br /><br /> 結構|  
  
## <a name="see-also"></a>另請參閱
[使用 Visual C++ 程式碼](working-with-visual-cpp-code.md)   
[類別和結構](/cpp/cpp/classes-and-structs-cpp)   
[struct](/cpp/cpp/struct-cpp)