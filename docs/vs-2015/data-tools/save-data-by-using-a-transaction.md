---
title: 使用異動儲存資料 |Microsoft Docs
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: ba83cf7db6415eefcb989f678bc4149d495016e4
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/17/2019
ms.locfileid: "59658340"
---
# <a name="save-data-by-using-a-transaction"></a>使用異動儲存資料
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

將資料儲存在交易中的使用<xref:System.Transactions>命名空間。 使用<xref:System.Transactions.TransactionScope>參與的交易，會自動為您管理的物件。  
  
 因此您必須以手動方式將參考加入專案，使用交易，則專案不會建立使用 System.Transactions 組件的參考。  
  
> [!NOTE]
>  <xref:System.Transactions>命名空間支援在 Windows 2000 或更新版本。  
  
 最簡單的方式實作交易是具現化<xref:System.Transactions.TransactionScope>物件中`using`陳述式。 (如需詳細資訊，請參閱 < [Using 陳述式](http://msdn.microsoft.com/library/665d1580-dd54-4e96-a9a9-6be2a68948f1)，並[using 陳述式](http://msdn.microsoft.com/library/afc355e6-f0b9-4240-94dd-0d93f17d9fc3)。)執行內的程式碼`using`參與交易的陳述式。  
  
 若要認可交易，呼叫<xref:System.Transactions.TransactionScope.Complete%2A>方法中使用的最後一個陳述式區塊。  
  
 若要回復交易，會擲回例外狀況之前呼叫<xref:System.Transactions.TransactionScope.Complete%2A>方法。  
  
 如需詳細資訊，請參閱 <<c0> [ 將資料儲存在交易中](../data-tools/save-data-in-a-transaction.md)。  
  
### <a name="to-add-a-reference-to-the-systemtransactions-dll"></a>若要加入 System.Transactions dll 的參考  
  
1.  在 **專案**功能表上，選取**加入參考**。  
  
2.  上 **.NET**  索引標籤 (**SQL Server** SQL Server 專案 索引標籤)，選取**System.Transactions**，然後選取**確定**。  
  
     參考 system.transactions.dll，才能為加入至專案。  
  
### <a name="to-save-data-in-a-transaction"></a>若要將資料儲存在交易中  
  
-   加入程式碼來儲存內使用的資料包含交易的陳述式。 下列程式碼示範如何建立和具現化<xref:System.Transactions.TransactionScope>物件中的 using 陳述式：  
  
     [!code-csharp[VbRaddataSaving#11](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#11)]
     [!code-vb[VbRaddataSaving#11](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#11)]  
  
## <a name="see-also"></a>另請參閱  
 [將資料儲存回資料庫](../data-tools/save-data-back-to-the-database.md)
