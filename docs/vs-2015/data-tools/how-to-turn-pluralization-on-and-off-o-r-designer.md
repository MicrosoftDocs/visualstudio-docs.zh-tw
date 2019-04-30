---
title: HOW TO：將複數表示開啟和關閉 （O-R 設計工具） |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 9b693bc3-303a-40a9-97ee-9cef5ca3ae81
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: a446e91095d9498a6182d1f80d046382b64e876e
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63384287"
---
# <a name="how-to-turn-pluralization-on-and-off-or-designer"></a>HOW TO：開啟和關閉複數表示 (O/R 設計工具)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

根據預設，當您將資料庫物件具有名稱結尾為 s 或 ies 從拖曳**伺服器總管**/**資料庫總管**拖曳至[LINQ to SQL 工具，在 Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)，產生的實體類別的名稱會從複數變更為單數。 這是為了更正確地呈現具現化 (Instantiated) 的實體類別對應至單一筆記錄的情況。 例如，將名為 Customers 的資料表加入至 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]會產生實體類別 Customer，原因是這個類別只會保留單一客戶的資料。  
  
> [!NOTE]
> 只有在英文版的 Visual Studio 中，才會啟用複數表示。  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
### <a name="to-turn-pluralization-on-and-off"></a>若要開啟和關閉複數表示  
  
1. 在 [ **工具** ] 功能表上按一下 [ **選項**]。  
  
2. 展開 [選項] 對話方塊中的 [資料庫工具]。  
  
> [!NOTE]
> 如果看不到 [資料庫工具] 節點，請選取 [顯示所有設定]。  
  
1. 按一下 [O/R 設計工具]。  
  
2. 設定**名稱的複數表示**要**已啟用** = **False**設[!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]，讓它不會變更類別名稱。  
  
3. 設定**名稱的複數表示**要**已啟用** = **True**將複數表示規則套用至類別物件的名稱新增至[!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]。  
  
## <a name="see-also"></a>另請參閱  
 [LINQ to SQL 工具，在 Visual Studio 中](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)   
 [存取 Visual Studio 中的資料](../data-tools/accessing-data-in-visual-studio.md)
