---
title: 如何： 使用異動儲存資料
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- saving data, using transactions
- System.Transactions namespace
- transactions, saving data
- data [Visual Studio], saving
ms.assetid: 8b835e8f-34a3-413d-9bb5-ebaeb87f1198
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 1c5d8d9f961db7c6560f1dd7a73f2ea62a974bac
ms.sourcegitcommit: f37affbc1b885dfe246d4b2c295a6538b383a0ca
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2018
ms.locfileid: "37174207"
---
# <a name="how-to-save-data-by-using-a-transaction"></a>如何： 使用異動儲存資料
將資料儲存在交易中的使用<xref:System.Transactions>命名空間。 使用<xref:System.Transactions.TransactionScope>參與的交易，會自動為您管理的物件。

參考不會建立專案*System.Transactions*組件，因此您必須以手動方式將參考加入專案，使用交易。

最簡單的方式實作交易是具現化<xref:System.Transactions.TransactionScope>物件中`using`陳述式。 (如需詳細資訊，請參閱 < [Using 陳述式](/dotnet/visual-basic/language-reference/statements/using-statement)，並[Using 陳述式](/dotnet/csharp/language-reference/keywords/using-statement)。)執行內的程式碼`using`參與交易的陳述式。

若要認可交易，呼叫<xref:System.Transactions.TransactionScope.Complete%2A>方法中使用的最後一個陳述式區塊。

若要回復交易，會擲回例外狀況之前呼叫<xref:System.Transactions.TransactionScope.Complete%2A>方法。

## <a name="to-add-a-reference-to-the-systemtransactionsdll"></a>若要新增參考 system.transactions.dll，才能

1.  在 **專案**功能表上，選取**加入參考**。

2.  上 **.NET**  索引標籤 (**SQL Server** SQL Server 專案 索引標籤)，選取**System.Transactions**，然後選取**確定**。

     參考*System.Transactions.dll*加入至專案。

## <a name="to-save-data-in-a-transaction"></a>若要將資料儲存在交易中

-   加入程式碼來儲存內使用的資料包含交易的陳述式。 下列程式碼示範如何建立和具現化<xref:System.Transactions.TransactionScope>物件中的 using 陳述式：

     [!code-vb[VbRaddataSaving#11](../data-tools/codesnippet/VisualBasic/save-data-by-using-a-transaction_1.vb)]
     [!code-csharp[VbRaddataSaving#11](../data-tools/codesnippet/CSharp/save-data-by-using-a-transaction_1.cs)]

## <a name="see-also"></a>另請參閱

- [將資料儲存回資料庫](../data-tools/save-data-back-to-the-database.md)
- [逐步解說：儲存異動中的資料](../data-tools/save-data-in-a-transaction.md)