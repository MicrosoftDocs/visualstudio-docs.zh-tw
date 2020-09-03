---
title: '&lt;無法刪除屬性屬性名稱 &gt; |Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667247"
---
# <a name="the-property-ltproperty-namegt-cannot-be-deleted"></a>&lt;無法刪除屬性屬性名稱 &gt;
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

\<property name>無法刪除屬性，因為它設定為和之間繼承的鑒別子屬性 \<class name>\<class name>

 選取的屬性已為在錯誤訊息指出的類別 (Class) 之間的繼承設定為**鑑別子屬性**。 如果屬性已參與資料類別之間的繼承組態，就無法刪除屬性。

 將**鑑別子屬性**設定為資料類別的不同屬性，就可以成功刪除要刪的屬性。

### <a name="to-correct-this-error"></a>更正這個錯誤

1. 在 O/R Designer 中，選取在錯誤訊息指出的資料類別之間連接的繼承關聯線。

2. 將 [鑑別子屬性]**** 設定為不同屬性。

3. 試著再次刪除屬性。

## <a name="see-also"></a>另請參閱
 [如何：使用 o/r 設計](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md)工具 [資料類別繼承設定繼承 (o/r 設計工具) ](../data-tools/data-class-inheritance-o-r-designer.md) [逐步解說：使用單一資料表繼承 (O/r 設計工具建立 LINQ to SQL 類別) ](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)
