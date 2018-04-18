---
title: 如何： 開啟和關閉 （O R 設計工具） 的複數表示 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 9b693bc3-303a-40a9-97ee-9cef5ca3ae81
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 6340946491ebaa8fa6bec395632e7d7943b4935e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-turn-pluralization-on-and-off-or-designer"></a>如何： 開啟複數表示開啟和關閉 （O/R 設計工具）
根據預設，當您將資料庫物件名稱結尾 s 或從 ies**伺服器總管**/**資料庫總管**到[LINQ to SQL 工具，在 Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)，產生的實體類別的名稱會變成從複數單數。 這是為了更正確地呈現具現化 (Instantiated) 的實體類別對應至單一筆記錄的情況。 例如，將名為 Customers 的資料表加入至 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]會產生實體類別 Customer，原因是這個類別只會保留單一客戶的資料。  
  
> [!NOTE]
>  只有在英文版的 Visual Studio 中，才會啟用複數表示。  
  
[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
### <a name="to-turn-pluralization-on-and-off"></a>若要開啟和關閉複數表示  
  
1.  在 [ **工具** ] 功能表上按一下 [ **選項**]。  
  
2.  在**選項**對話方塊方塊中，展開 **資料庫工具**。  
  
    > [!NOTE]
    >  選取**顯示所有設定**如果**資料庫工具**看不到節點。  
  
3.  按一下**O/R Designer**。  
  
4.  設定**名稱的複數表示**至**啟用** = **False**設定[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]，讓它不會變更類別名稱。  
  
5.  設定**名稱的複數表示**至**啟用** = **True**將複數表示規則套用至類別名稱加入物件[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]。  
  
## <a name="see-also"></a>另請參閱  
[LINQ to SQL 工具，Visual Studio 中](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
[LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)   
[存取 Visual Studio 中的資料](../data-tools/accessing-data-in-visual-studio.md)