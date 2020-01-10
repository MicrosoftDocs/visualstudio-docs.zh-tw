---
title: 如何：使用交易儲存資料
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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: beadb43d7eed78f04fc60ce1307045e9badac205
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/01/2020
ms.locfileid: "75586272"
---
# <a name="how-to-save-data-by-using-a-transaction"></a>如何：使用交易儲存資料

您可以使用 <xref:System.Transactions> 命名空間，將資料儲存在交易中。 使用 <xref:System.Transactions.TransactionScope> 物件來參與自動為您管理的交易。

不會使用對*system.object*元件的參考來建立專案，因此您必須手動加入使用交易之專案的參考。

執行交易最簡單的方式，就是在 `using` 語句中具現化 <xref:System.Transactions.TransactionScope> 物件。 （如需詳細資訊，請參閱[using 語句](/dotnet/visual-basic/language-reference/statements/using-statement)和[using](/dotnet/csharp/language-reference/keywords/using-statement)語句）。在 `using` 語句內執行的程式碼會參與交易。

若要認可交易，請呼叫 <xref:System.Transactions.TransactionScope.Complete%2A> 方法做為 using 區塊中的最後一個語句。

若要復原交易，請在呼叫 <xref:System.Transactions.TransactionScope.Complete%2A> 方法之前擲回例外狀況。

## <a name="to-add-a-reference-to-the-systemtransactionsdll"></a>若要加入對 System.web 的參考

1. 在 [專案] 功能表上，選取 [新增參考]。

2. 在  **.net**  索引標籤（SQL Server 專案的**SQL Server**  索引標籤）上，選取 **系統**，然後選取**確定**。

     系統會將*system.object*的參考加入至專案。

## <a name="to-save-data-in-a-transaction"></a>若要將資料儲存在交易中

- 加入程式碼，以在包含交易的 using 語句中儲存資料。 下列程式碼示範如何在 using 語句中建立和具現化 <xref:System.Transactions.TransactionScope> 物件：

     [!code-vb[VbRaddataSaving#11](../data-tools/codesnippet/VisualBasic/save-data-by-using-a-transaction_1.vb)]
     [!code-csharp[VbRaddataSaving#11](../data-tools/codesnippet/CSharp/save-data-by-using-a-transaction_1.cs)]

## <a name="see-also"></a>請參閱

- [將資料儲存回資料庫](../data-tools/save-data-back-to-the-database.md)
- [逐步解說：儲存異動中的資料](../data-tools/save-data-in-a-transaction.md)
