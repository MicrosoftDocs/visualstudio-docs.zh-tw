---
title: 如何： 使用異動儲存資料 |Microsoft 文件
ms.custom: ''
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
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: f830884763e30cdcb915b2c940051e7c5858cebf
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-save-data-by-using-a-transaction"></a>如何： 使用異動儲存資料
將資料儲存在交易中的使用<xref:System.Transactions>命名空間。 使用<xref:System.Transactions.TransactionScope>物件能夠參與的交易，為您自動管理。  
  
因此您必須手動將參考加入至使用交易之專案的專案不會建立使用 System.Transactions 組件的參考。  
  
最簡單的方式實作交易是具現化<xref:System.Transactions.TransactionScope>物件存放至`using`陳述式。 (如需詳細資訊，請參閱[Using 陳述式](/dotnet/visual-basic/language-reference/statements/using-statement)，和[使用陳述式](/dotnet/csharp/language-reference/keywords/using-statement)。)執行內的程式碼`using`參與交易的陳述式。  
  
若要認可的交易，呼叫<xref:System.Transactions.TransactionScope.Complete%2A>方法中使用的最後一個陳述式區塊。  
  
若要回復交易，會擲回例外狀況之前呼叫<xref:System.Transactions.TransactionScope.Complete%2A>方法。  
  
## <a name="to-add-a-reference-to-the-systemtransactionsdll"></a>若要加入的參考 system.transactions.dll  
  
1.  在**專案**功能表上，選取**加入參考**。  
  
2.  上**.NET**  索引標籤 (**SQL Server**  索引標籤的 SQL Server 專案)，選取**System.Transactions**，然後選取**確定**。  
  
     System.transactions.dll 的參考會加入至專案。  
  
## <a name="to-save-data-in-a-transaction"></a>若要在交易中儲存資料  
  
-   加入程式碼中所使用的儲存資料以包含交易的陳述式。 下列程式碼會示範如何建立及具現化<xref:System.Transactions.TransactionScope>物件中使用陳述式：  
  
     [!code-vb[VbRaddataSaving#11](../data-tools/codesnippet/VisualBasic/save-data-by-using-a-transaction_1.vb)]
     [!code-csharp[VbRaddataSaving#11](../data-tools/codesnippet/CSharp/save-data-by-using-a-transaction_1.cs)]  
  
## <a name="see-also"></a>另請參閱
[將資料儲存回資料庫](../data-tools/save-data-back-to-the-database.md)  
[逐步解說：儲存異動中的資料](../data-tools/save-data-in-a-transaction.md)  