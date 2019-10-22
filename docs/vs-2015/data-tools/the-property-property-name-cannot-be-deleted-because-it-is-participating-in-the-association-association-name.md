---
title: 無法刪除屬性 &lt;property 名稱 &gt;，因為它正在參與關聯 &lt;association 名稱 &gt; |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 389873cc-92dd-48da-bfca-0f6c8e0ae3c2
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 53bf12a84a705ddca0cacffc36028698cb08443a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667266"
---
# <a name="the-property-ltproperty-namegt-cannot-be-deleted-because-it-is-participating-in-the-association-ltassociation-namegt"></a>無法刪除屬性&lt;屬性名稱&gt;，因為其正在參與關聯&lt;關聯名稱&gt;
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

選取的屬性，已設定為在錯誤訊息指出之類別 (Class) 之間進行關聯時所需的**關聯屬性**。 如果屬性已參與資料類別之間的關聯，就無法刪除屬性。

 將**關聯屬性**設定為資料類別的不同屬性，就可以成功刪除需要刪除的屬性。

### <a name="to-correct-this-error"></a>更正這個錯誤

1. 在 O/R Designer 上，選取在錯誤訊息指出的資料類別之間連接的關聯線。

2. 按兩下這條線以開啟 [關聯編輯器] 對話方塊。

3. 從 [關聯屬性] 中移除屬性。

4. 試著再次刪除屬性。

## <a name="see-also"></a>請參閱
 [LINQ to SQL 工具 Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [如何：在 LINQ to SQL 類別之間建立關聯（關聯性）（o/R 設計工具）](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md) [逐步解說：建立 LINQ to SQL 類別（o-r 設計工具）](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)
