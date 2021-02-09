---
title: 類別設計工具中的 c + + 結構
description: 瞭解類別設計工具如何支援使用關鍵字結構宣告的 c + + 結構。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Class Designer [Visual Studio], structures
ms.assetid: bad18ab6-d956-47a6-a413-811cc26db5f5
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- cplusplus
ms.openlocfilehash: 3ca35f9e1c3c1340330ddbbe36ede540fe1e547d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99879952"
---
# <a name="c-structures-in-class-designer"></a>類別設計工具中的 c + + 結構

[類別設計工具] 支援 C++ 結構，其使用 `struct` 關鍵字所宣告。 以下是範例：

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

## <a name="see-also"></a>另請參閱

- [使用 c + + 程式碼](working-with-visual-cpp-code.md)
- [類別和結構](/cpp/cpp/classes-and-structs-cpp)
- [結構](/cpp/cpp/struct-cpp)
