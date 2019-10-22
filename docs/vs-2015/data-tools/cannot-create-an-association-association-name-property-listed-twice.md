---
title: 無法建立關聯 &lt;association 名稱 &gt;-屬性列出了兩次 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 3ced8bda-210e-4caf-9d8f-96cdbba19251
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9e4a1d20b5c341c1643836ae30e5de6243f35454
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662551"
---
# <a name="cannot-create-an-association-ltassociation-namegt---property-listed-twice"></a>無法建立關聯&lt;關聯名稱&gt;：屬性已列出兩次
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

無法建立關聯 \<關聯名稱>。 相同的屬性已列出超過一次：\<屬性名稱>。

 關聯是以 [關聯編輯器] 對話方塊中選取的**關聯屬性**建立。 一次只能列出關聯中之一個類別 (Class) 的屬性。

 訊息中的屬性，在父類別或子類別的 [關聯屬性] 中出現多次。

### <a name="to-resolve-this-condition"></a>若要解決這種狀況

- 檢查訊息，並記下訊息中指定的屬性。

- 按一下 [確定] 來解除訊息方塊。

- 檢查 [關聯屬性]，並移除重複項目。

- 按一下 [確定]。

## <a name="see-also"></a>請參閱
 [LINQ to SQL 工具 Visual Studio](https://msdn.microsoft.com/library/a57e82d5-f7e4-4894-8add-3d9ba4fce186) [如何：在 LINQ to SQL 類別之間建立關聯（關聯性）（o/R 設計工具）](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md) [逐步解說：建立 LINQ to SQL 類別（o-r 設計工具）](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)
