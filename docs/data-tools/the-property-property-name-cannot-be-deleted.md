---
title: 無法刪除屬性
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 55873f74-7834-4ec1-8815-eeeb65618d87
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 4b1e0652d19b10b1d1ede7b1b950d89ca1bf670c
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2019
ms.locfileid: "55939641"
---
# <a name="the-property-property-name-cannot-be-deleted"></a>無法刪除屬性 \<屬性名稱>

無法刪除屬性 \<屬性名稱>，因為它設定為 \<類別名稱> 與 \<類別名稱> 間之繼承的**鑑別子屬性**

選取的屬性已為在錯誤訊息指出的類別 (Class) 之間的繼承設定為**鑑別子屬性**。 如果屬性已參與資料類別之間的繼承組態，就無法刪除屬性。

將**鑑別子屬性**設定為資料類別的不同屬性，就可以成功刪除要刪的屬性。

## <a name="to-correct-this-error"></a>更正這個錯誤

1. 在 **O/R 設計工具** 中，選取在錯誤訊息指出的資料類別之間連線的繼承線。

2. 將 [鑑別子屬性] 設定為不同屬性。

3. 試著再次刪除屬性。

## <a name="see-also"></a>另請參閱

- [O/R 設計工具訊息](../data-tools/o-r-designer-messages.md)
- [Visual Studio 中的 LINQ to SQL 工具](../data-tools/linq-to-sql-tools-in-visual-studio2.md)