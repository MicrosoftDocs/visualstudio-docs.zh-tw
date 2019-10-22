---
title: 無法刪除屬性 &lt;property 名稱 &gt; |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 55873f74-7834-4ec1-8815-eeeb65618d87
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: aca36919cb4c82d6ca76e0f3eecbbacd48cde768
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667247"
---
# <a name="the-property-ltproperty-namegt-cannot-be-deleted"></a>無法刪除屬性 &lt;property 名稱 &gt;
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

無法刪除屬性 \<property 名稱 >，因為它已設定為 \<class 名稱 > 和 \<class 名稱之間繼承的鑒別子屬性 >

 選取的屬性已為在錯誤訊息指出的類別 (Class) 之間的繼承設定為**鑑別子屬性**。 如果屬性已參與資料類別之間的繼承組態，就無法刪除屬性。

 將**鑑別子屬性**設定為資料類別的不同屬性，就可以成功刪除要刪的屬性。

### <a name="to-correct-this-error"></a>更正這個錯誤

1. 在 O/R Designer 中，選取在錯誤訊息指出的資料類別之間連接的繼承關聯線。

2. 將 [鑑別子屬性] 設定為不同屬性。

3. 試著再次刪除屬性。

## <a name="see-also"></a>請參閱
 [如何：使用 O/r 設計工具來設定繼承的](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md)[資料類別繼承（O/r 設計工具）](../data-tools/data-class-inheritance-o-r-designer.md)逐步解說[：使用單一資料表繼承建立 LINQ to SQL 類別（o/r 設計工具）](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)
