---
title: 如何：使用交易儲存資料
description: 請參閱 Visual Studio 中的資料集工具，以瞭解如何使用交易來儲存資料。 您可以使用「系統交易」命名空間，將資料儲存在交易中。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: c22a0cc9b0b9d37a4d725aa8ce494646e7779f0f
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2021
ms.locfileid: "106216068"
---
# <a name="how-to-save-data-by-using-a-transaction"></a>如何：使用交易儲存資料

您可以使用命名空間將資料儲存在交易中 <xref:System.Transactions> 。 <xref:System.Transactions.TransactionScope>您可以使用物件來參與自動為您管理的交易。

*系統* 不會使用對 system.string 元件的參考來建立專案，因此您需要手動加入使用交易之專案的參考。

若要執行交易，最簡單的方式就是 <xref:System.Transactions.TransactionScope> 在語句中具現化物件 `using` 。  (如需詳細資訊，請參閱 [using 語句](/dotnet/visual-basic/language-reference/statements/using-statement)和 [using 語句](/dotnet/csharp/language-reference/keywords/using-statement)。 ) 在語句中執行的程式碼會 `using` 參與交易。

若要認可交易，請呼叫 <xref:System.Transactions.TransactionScope.Complete%2A> 方法做為 using 區塊中的最後一個語句。

若要回復交易，請在呼叫方法之前擲回例外狀況 <xref:System.Transactions.TransactionScope.Complete%2A> 。

## <a name="to-add-a-reference-to-the-systemtransactionsdll"></a>若要加入 System.Transactions.dll 的參考

1. 在 [專案] 功能表上，選取 [新增參考]。

2. 在 [ **.net** (] 索引標籤上，) SQL Server 專案的 **SQL Server** ] 索引標籤中，選取 [ **系統交易**]，然後選取 **[確定]**。

     *System.Transactions.dll* 的參考會加入至專案。

## <a name="to-save-data-in-a-transaction"></a>若要將資料儲存在交易中

- 加入程式碼，以在包含交易的 using 語句內儲存資料。 下列程式碼示範如何在 using 語句中建立和具現化 <xref:System.Transactions.TransactionScope> 物件：

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb" id="Snippet11":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs" id="Snippet11":::

## <a name="see-also"></a>另請參閱

- [將資料儲存回資料庫](../data-tools/save-data-back-to-the-database.md)
- [逐步解說：儲存異動中的資料](../data-tools/save-data-in-a-transaction.md)
