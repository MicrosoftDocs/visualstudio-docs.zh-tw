---
title: 類別設計工具中的 Visual C++ 結構
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Class Designer [Visual Studio], structures
ms.assetid: bad18ab6-d956-47a6-a413-811cc26db5f5
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: da786e6f598b4b28aeb7758df41f54ea23c4185d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72647599"
---
# <a name="visual-c-structures-in-class-designer"></a>類別設計工具中的 Visual C++ 結構

[類別設計工具] 支援 C++ 結構，其使用 `struct` 關鍵字所宣告。 以下是一個範例：

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

|程式碼項目|類別設計工具檢視|
|------------------| - |
|`struct StructureName {};`|**StructureName**<br /><br /> 結構|

## <a name="see-also"></a>請參閱

- [使用 Visual C++ 程式碼](working-with-visual-cpp-code.md)
- [類別和結構](/cpp/cpp/classes-and-structs-cpp)
- [struct](/cpp/cpp/struct-cpp)