---
title: 類別設計工具中的 Visual C++ 結構
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Class Designer [Visual Studio], structures
ms.assetid: bad18ab6-d956-47a6-a413-811cc26db5f5
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: 36d9e78a1944817d9384d0c55b9584e58a758ccc
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
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

|Code 項目|類別設計工具檢視|
|------------------|-------------------------|
|`struct StructureName {};`|**StructureName**<br /><br /> 結構|

## <a name="see-also"></a>另請參閱

- [使用 Visual C++ 程式碼](working-with-visual-cpp-code.md)
- [類別和結構](/cpp/cpp/classes-and-structs-cpp)
- [struct](/cpp/cpp/struct-cpp)