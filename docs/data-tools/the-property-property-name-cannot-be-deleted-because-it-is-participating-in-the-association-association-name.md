---
title: 無法刪除屬性，因為它正參與關聯
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 389873cc-92dd-48da-bfca-0f6c8e0ae3c2
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 6ed6b14f64d16d1f18d4b358761169c3d424cee8
ms.sourcegitcommit: f37affbc1b885dfe246d4b2c295a6538b383a0ca
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2018
ms.locfileid: "37174058"
---
# <a name="the-property-ltproperty-namegt-cannot-be-deleted-because-it-is-participating-in-the-association-ltassociation-namegt"></a>屬性&lt;屬性名稱&gt;無法刪除，因為它正參與關聯&lt;關聯名稱&gt;

選取的屬性設定為**關聯屬性**錯誤訊息中所指出的類別之間的關聯。 如果屬性已參與資料類別之間的關聯，就無法刪除屬性。

設定**關聯屬性**不同的屬性，可以成功刪除要刪的屬性資料類別。

## <a name="to-correct-this-error"></a>更正這個錯誤

1. 在 選取關聯線**O/R Designer**連接錯誤訊息中指出的資料類別。

2. 若要開啟的該行上按兩下**關聯編輯器** 對話方塊。

3. 從中移除屬性**關聯屬性**。

4. 試著再次刪除屬性。

## <a name="see-also"></a>另請參閱

- [O/R 設計工具訊息](../data-tools/o-r-designer-messages.md)
- [LINQ to SQL 工具，在 Visual Studio 中](../data-tools/linq-to-sql-tools-in-visual-studio2.md)