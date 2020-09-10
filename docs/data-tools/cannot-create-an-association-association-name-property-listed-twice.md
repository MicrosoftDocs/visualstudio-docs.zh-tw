---
title: 屬性列出了兩次
description: 無法建立關聯：屬性已列出兩次
ms.date: 11/04/2016
ms.topic: error-reference
ms.technology: vs-data-tools
ms.assetid: 3ced8bda-210e-4caf-9d8f-96cdbba19251
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 3c496a25b093c88cca68d31bd22ccc6deca9a33a
ms.sourcegitcommit: 2a201c93ed526b0f7e5848657500f1111b08ac2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2020
ms.locfileid: "89743200"
---
# <a name="cannot-create-an-association-ltassociation-namegt---property-listed-twice"></a>無法建立關聯&lt;關聯名稱&gt;：屬性已列出兩次

無法建立關聯 \<association name> 。 相同的屬性已列出一次以上： \<property name> 。

關聯由 [關聯編輯器]**** 對話方塊中選取的 [關聯屬性]**** 所定義。 一次只能列出關聯中之一個類別 (Class) 的屬性。

訊息中的屬性，在父類別或子類別的 [關聯屬性]**** 中出現多次。

## <a name="to-resolve-this-condition"></a>若要解決這種狀況

- 檢查訊息，並記下訊息中指定的屬性。

- 按一下 [確定]**** 來解除訊息方塊。

- 檢查 [關聯屬性]****，並移除重複項目。

- 按一下 [確定]。

## <a name="see-also"></a>另請參閱

- [Visual Studio 中的 LINQ to SQL 工具](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [如何：建立 LINQ to SQL 類別之間的關聯 (O/R 設計工具) ](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md)