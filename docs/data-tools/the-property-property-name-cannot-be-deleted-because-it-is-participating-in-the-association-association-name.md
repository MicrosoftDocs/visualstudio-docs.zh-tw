---
title: 無法刪除屬性，因為其正在參與關聯
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 389873cc-92dd-48da-bfca-0f6c8e0ae3c2
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: d277919229316768cde27efdc9b2797d0351e9fe
ms.sourcegitcommit: 50f0c3f2763a05de8482b3579026d9c76c0e226c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/09/2019
ms.locfileid: "65458496"
---
# <a name="the-property-ltproperty-namegt-cannot-be-deleted-because-it-is-participating-in-the-association-ltassociation-namegt"></a>無法刪除屬性&lt;屬性名稱&gt;，因為其正在參與關聯&lt;關聯名稱&gt;

選取的屬性，已設定為在錯誤訊息指出之類別 (Class) 之間進行關聯時所需的**關聯屬性**。 如果屬性已參與資料類別之間的關聯，就無法刪除屬性。

將**關聯屬性**設定為資料類別的不同屬性，就可以成功刪除需要刪除的屬性。

## <a name="to-correct-this-error"></a>更正這個錯誤

1. 在 **O/R 設計工具**上，選取在錯誤訊息指出的資料類別之間連接的關聯線。

2. 按兩下這條線以開啟 [關聯編輯器] 對話方塊。

3. 從 [關聯屬性] 中移除屬性。

4. 試著再次刪除屬性。

## <a name="see-also"></a>另請參閱

- [Visual Studio 中的 LINQ to SQL 工具](../data-tools/linq-to-sql-tools-in-visual-studio2.md)