---
title: 註釋結構和類別
ms.date: 06/28/2019
ms.topic: conceptual
f1_keywords:
- _Field_size_bytes_part_
- _Field_size_bytes_full_opt_
- _Field_size_bytes_
- _Field_size_opt_
- _Field_size_part_
- _Field_size_bytes_part_opt_
- _Field_range_
- _Field_size_part_opt_
- _Field_size_
- _Field_size_bytes_opt_
- _Struct_size_bytes_
- _Field_size_bytes_full_
- _Field_size_full_
- _Field_size_full_opt_
- _Field_z_
ms.assetid: b8278a4a-c86e-4845-aa2a-70da21a1dd52
author: mikeblome
ms.author: mblome
manager: markl
ms.workload:
- multiple
ms.openlocfilehash: 1cff36760a84821a33dcdb1ee4cc6842cd40aee0
ms.sourcegitcommit: 535ef05b1e553f0fc66082cd2e0998817eb2a56a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2019
ms.locfileid: "72015975"
---
# <a name="annotating-structs-and-classes"></a>註釋結構和類別

您可以使用作用類似非變異項目的註釋為結構和類別加上附註，在包含封入結構做為參數或結果值的任何函式呼叫或函式進入/結束點，會假定這些註釋為真。

## <a name="struct-and-class-annotations"></a>結構和類別注釋

- `_Field_range_(low, high)`

     欄位位於 `low` 到 `high` 的範圍內（含）。  相當於使用適當的前置或後置條件套用至已標註物件的 `_Satisfies_(_Curr_ >= low && _Curr_ <= high)`。

- `_Field_size_(size)`, `_Field_size_opt_(size)`, `_Field_size_bytes_(size)`, `_Field_size_bytes_opt_(size)`

     欄位，其可寫入的大小是由 `size` 以項目 (或位元組) 為單位指定。

- `_Field_size_part_(size, count)`, `_Field_size_part_opt_(size, count)`,         `_Field_size_bytes_part_(size, count)`, `_Field_size_bytes_part_opt_(size, count)`

     欄位，其可寫入的大小是由 `size` 以項目 (或位元組) 為單位指定，而且可以讀取這些項目 (位元組) 的 `count`。

- `_Field_size_full_(size)`, `_Field_size_full_opt_(size)`, `_Field_size_bytes_full_(size)`, `_Field_size_bytes_full_opt_(size)`

     具有可讀取及可寫入大小的欄位，其大小是以 `size` 所指定的項目 (或位元組) 為單位表示。

- `_Field_z_`

     具有以 null 終止之字串的欄位。

- `_Struct_size_bytes_(size)`

     適用于結構或類別宣告。  指出該類型的有效物件可能大於所宣告的類型，其位元組數目是由 `size` 所指定。  例如:

    ```cpp

    typedef _Struct_size_bytes_(nSize)
    struct MyStruct {
        size_t nSize;
        ...
    };

    ```

     @No__t-1 類型 `pM` 的緩衝區大小（以位元組為單位）會被視為：

    ```cpp
    min(pM->nSize, sizeof(MyStruct))
    ```

## <a name="example"></a>範例

```cpp
#include <sal.h>
// For FIELD_OFFSET macro
#include <windows.h>

// This _Struct_size_bytes_ is equivalent to what below _Field_size_ means.
_Struct_size_bytes_(FIELD_OFFSET(MyBuffer, buffer) + bufferSize * sizeof(int))
struct MyBuffer
{
    static int MaxBufferSize;
    
    _Field_z_
    const char* name;
    
    int firstField;

    // ... other fields

    _Field_range_(1, MaxBufferSize)
    int bufferSize;
    _Field_size_(bufferSize)        // Prefered way - easier to read and maintain.
    int buffer[0];
};
```

此範例的附注：

- `_Field_z_` 相當於 `_Null_terminated_`。  [名稱] 欄位 `_Field_z_` 指定 [名稱] 欄位是以 null 結束的字串。
- @no__t 的 `_Field_range_`-1 指定 `bufferSize` 的值應該在1和 `MaxBufferSize` （兩者皆包含）中。
- @No__t-0 和 @no__t 1 注釋的最終結果是相同的。 對於具有類似配置的結構或類別，`_Field_size_` 較容易閱讀和維護，因為它的參考和計算比對等的 `_Struct_size_bytes_` 注釋少。 `_Field_size_` 不需要轉換成位元組大小。 如果 [位元組大小] 是唯一的選項（例如，針對 void 指標欄位），則可以使用 `_Field_size_bytes_`。 如果 `_Struct_size_bytes_` 和 `_Field_size_` 都存在，則這兩個工具都可供使用。 如果這兩個批註不同意，該怎麼辦。

## <a name="see-also"></a>另請參閱

- [使用 SAL 註釋減少 C/C++ 程式碼的缺失](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)
- [了解 SAL](../code-quality/understanding-sal.md)
- [註釋函式參數和傳回值](../code-quality/annotating-function-parameters-and-return-values.md)
- [註釋函式行為](../code-quality/annotating-function-behavior.md)
- [註釋鎖定行為](../code-quality/annotating-locking-behavior.md)
- [指定套用註釋的時機和位置](../code-quality/specifying-when-and-where-an-annotation-applies.md)
- [內建函式](../code-quality/intrinsic-functions.md)
- [最佳做法和範例](../code-quality/best-practices-and-examples-sal.md)