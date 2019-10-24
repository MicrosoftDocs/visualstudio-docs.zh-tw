---
title: 指定套用註釋的時機和位置
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- _Group_
- _At_
- _When_
- _At_buffer_
ms.assetid: 8e4f4f9c-5dfa-4835-87df-ecd1698fc650
author: mikeblome
ms.author: mblome
manager: markl
ms.workload:
- multiple
ms.openlocfilehash: 8ccf20ab4348a8abed4b052f512477c8b2a8cd0b
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745892"
---
# <a name="specifying-when-and-where-an-annotation-applies"></a>指定套用註釋的時機和位置
當注釋是條件式時，它可能需要其他注釋來指定分析器的批註。  例如，如果函式有可以是同步或非同步變數，函式的行為會如下所示：在同步的情況下，它一律會成功，但在非同步情況下，它會在無法立即成功時報告錯誤。 以同步方式呼叫函式時，檢查結果值不會對程式碼分析器提供任何值，因為它不會傳回。  不過，當以非同步方式呼叫函式，但未檢查函數結果時，可能會發生嚴重的錯誤。 這個範例說明您可以使用 `_When_` 注釋的情況（如本文稍後所述）來啟用檢查。

## <a name="structural-annotations"></a>結構化注釋
若要控制批註的套用時機和位置，請使用下列結構化注釋。

|註釋|描述|
|----------------|-----------------|
|`_At_(expr, anno-list)`|`expr` 是產生左值的運算式。 @No__t_0 中的批註會套用至 `expr` 所命名的物件。 針對 `anno-list` 中的每個批註，如果批註是在前置條件中轉譯，則會在前置條件中解讀 `expr`; 如果批註是在後置條件中轉譯，則會在後置條件中轉譯。|
|`_At_buffer_(expr, iter, elem-count, anno-list)`|`expr` 是產生左值的運算式。 @No__t_0 中的批註會套用至 `expr` 所命名的物件。 針對 `anno-list` 中的每個批註，如果批註在前置條件中被解讀，則會在預先條件中解讀 `expr`; 如果批註是在後置條件中轉譯，則會在後置條件中轉譯。<br /><br /> `iter` 是以注釋為範圍的變數名稱（包含 `anno-list`）。 `iter` 的隱含類型 `long`。 任何封閉範圍中的名稱相同的變數都會從評估中隱藏出來。<br /><br /> `elem-count` 是評估為整數的運算式。|
|`_Group_(anno-list)`|@No__t_0 中的注釋全都視為具有套用至每個注釋之群組批註的任何限定詞。|
|`_When_(expr, anno-list)`|`expr` 是可以轉換成 `bool` 的運算式。 若為非零（`true`），則會將 `anno-list` 中指定的注釋視為適用。<br /><br /> 根據預設，針對 `anno-list` 中的每個批註，如果注釋是前置條件，則 `expr` 會解讀為使用輸入值，而如果注釋為後置條件，則會使用輸出值。 若要覆寫預設值，您可以在評估後置條件時使用 `_Old_` 內建，以指出應該使用輸入值。 **注意：** 如果牽涉到可變動的值（例如 `*pLength`），則可能會 `_When_` 啟用不同的注釋，因為前置條件中 `expr` 的評估結果可能與在後置條件中的評估結果不同。|

## <a name="see-also"></a>請參閱

- [使用 SAL 註釋減少 C/C++ 程式碼的缺失](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)
- [了解 SAL](../code-quality/understanding-sal.md)
- [註釋函式參數和傳回值](../code-quality/annotating-function-parameters-and-return-values.md)
- [註釋函式行為](../code-quality/annotating-function-behavior.md)
- [註釋結構和類別](../code-quality/annotating-structs-and-classes.md)
- [註釋鎖定行為](../code-quality/annotating-locking-behavior.md)
- [內建函式](../code-quality/intrinsic-functions.md)
- [最佳做法和範例](../code-quality/best-practices-and-examples-sal.md)
