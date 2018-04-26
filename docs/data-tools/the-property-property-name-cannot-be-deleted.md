---
title: 無法刪除屬性
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 55873f74-7834-4ec1-8815-eeeb65618d87
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 80b5e40900cd8912b727270a46ebcf119c324f53
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="the-property-property-name-cannot-be-deleted"></a>屬性\<屬性名稱 > 無法刪除

屬性\<屬性名稱 > 無法刪除，因為它會設定為**鑑別子屬性**間之繼承\<類別名稱 > 和\<類別名稱 >

選取的屬性設定為**鑑別子屬性**錯誤訊息中所指出的類別之間的繼承。 如果屬性已參與資料類別之間的繼承組態，就無法刪除屬性。

設定**鑑別子屬性**不同的屬性，為資料類別，以啟用成功刪除的所需的屬性。

## <a name="to-correct-this-error"></a>更正這個錯誤

1. 在 O/R Designer 中，選取在錯誤訊息指出的資料類別之間連接的繼承關聯線。

2. 設定**鑑別子**的不同屬性的屬性。

3. 試著再次刪除屬性。

## <a name="see-also"></a>另請參閱

- [O/R 設計工具訊息](../data-tools/o-r-designer-messages.md)
- [LINQ to SQL 工具，Visual Studio 中](../data-tools/linq-to-sql-tools-in-visual-studio2.md)