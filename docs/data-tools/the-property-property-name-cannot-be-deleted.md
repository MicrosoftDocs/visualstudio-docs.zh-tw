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
ms.openlocfilehash: 7e85860de7494ae7d93ad37bd0a115fa786f0a87
ms.sourcegitcommit: f37affbc1b885dfe246d4b2c295a6538b383a0ca
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2018
ms.locfileid: "37174009"
---
# <a name="the-property-property-name-cannot-be-deleted"></a>屬性\<屬性名稱 > 不能刪除

屬性\<屬性名稱 > 不能刪除，因為它設定為**鑑別子屬性**間之繼承\<類別名稱 > 和\<類別名稱 >

選取的屬性設定為**鑑別子屬性**類別間之繼承所示的錯誤訊息。 如果屬性已參與資料類別之間的繼承組態，就無法刪除屬性。

設定**鑑別子屬性**不同的屬性，可以成功刪除要刪的屬性資料類別。

## <a name="to-correct-this-error"></a>更正這個錯誤

1. 在  **O/R Designer**，選取連接的資料類別的繼承關聯線所示的錯誤訊息。

2. 設定**鑑別子**的不同屬性的屬性。

3. 試著再次刪除屬性。

## <a name="see-also"></a>另請參閱

- [O/R 設計工具訊息](../data-tools/o-r-designer-messages.md)
- [LINQ to SQL 工具，在 Visual Studio 中](../data-tools/linq-to-sql-tools-in-visual-studio2.md)