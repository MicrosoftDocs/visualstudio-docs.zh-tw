---
title: 使用交易儲存資料 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- saving data, using transactions
- System.Transactions namespace
- transactions, saving data
- data [Visual Studio], saving
ms.assetid: 8b835e8f-34a3-413d-9bb5-ebaeb87f1198
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 85f3584073523e748168faf569aa918ba912fbf8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652839"
---
# <a name="save-data-by-using-a-transaction"></a>使用異動儲存資料
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以使用 <xref:System.Transactions> 命名空間，將資料儲存在交易中。 使用 <xref:System.Transactions.TransactionScope> 物件來參與自動為您管理的交易。

 不會使用對 System.object 元件的參考來建立專案，因此您必須手動加入使用交易之專案的參考。

> [!NOTE]
> Windows 2000 或更新版本中支援 <xref:System.Transactions> 命名空間。

 執行交易最簡單的方式，就是在 `using` 語句中具現化 <xref:System.Transactions.TransactionScope> 物件。 （如需詳細資訊，請參閱[Using 語句](https://msdn.microsoft.com/library/665d1580-dd54-4e96-a9a9-6be2a68948f1)和[using](https://msdn.microsoft.com/library/afc355e6-f0b9-4240-94dd-0d93f17d9fc3)語句）。在 `using` 語句內執行的程式碼會參與交易。

 若要認可交易，請呼叫 <xref:System.Transactions.TransactionScope.Complete%2A> 方法做為 using 區塊中的最後一個語句。

 若要復原交易，請在呼叫 <xref:System.Transactions.TransactionScope.Complete%2A> 方法之前擲回例外狀況。

 如需詳細資訊，請參閱[在交易中儲存資料](../data-tools/save-data-in-a-transaction.md)。

### <a name="to-add-a-reference-to-the-systemtransactions-dll"></a>若要加入對 system.string dll 的參考

1. 在 [**專案**] 功能表上，選取 [**加入參考**]。

2. 在  **.net**  索引標籤（SQL Server 專案的**SQL Server**  索引標籤）上，選取 **系統**，然後選取**確定**。

     系統會將 System.object 的參考加入至專案。

### <a name="to-save-data-in-a-transaction"></a>若要將資料儲存在交易中

- 加入程式碼，以在包含交易的 using 語句中儲存資料。 下列程式碼示範如何在 using 語句中建立和具現化 <xref:System.Transactions.TransactionScope> 物件：

     [!code-csharp[VbRaddataSaving#11](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#11)]
     [!code-vb[VbRaddataSaving#11](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#11)]

## <a name="see-also"></a>請參閱
 [將資料儲存回資料庫](../data-tools/save-data-back-to-the-database.md)
