---
title: 如何： 開啟和關閉 （O-R 設計工具） 的複數表示
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 9b693bc3-303a-40a9-97ee-9cef5ca3ae81
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 0a2d2e44efc284c38cfc450833839776effb9936
ms.sourcegitcommit: e9d1018a01af62c3dc5aeb6b325faba7e20bd496
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/28/2018
ms.locfileid: "37089379"
---
# <a name="how-to-turn-pluralization-on-and-off-or-designer"></a>如何： 開啟和關閉 （O/R 設計工具） 的複數表示
根據預設，當您將資料庫物件具有名稱結尾為 s 或 ies 從拖曳**伺服器總管**或**資料庫總管**拖曳至[Visual Studio 中的 LINQ to SQL 工具](../data-tools/linq-to-sql-tools-in-visual-studio2.md)，產生的實體類別的名稱會從複數變更變為單數。 這是為了更正確地呈現具現化 (Instantiated) 的實體類別對應至單一筆記錄的情況。 例如，新增`Customers`資料表**O/R Designer**產生實體類別`Customer`因為類別會保留單一客戶的資料。

> [!NOTE]
>  只有在英文版的 Visual Studio 中，才會啟用複數表示。

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-turn-pluralization-on-and-off"></a>若要開啟和關閉複數表示

1.  在 [ **工具** ] 功能表上按一下 [ **選項**]。

2.  在 **選項**對話方塊方塊中，展開**Database**。

    > [!NOTE]
    >  選取 **顯示所有設定**如果**Database**看不到節點。

3.  按一下  **O/R Designer**。

4.  設定**名稱的複數表示**要**已啟用** = **False**設**O/R Designer** ，讓它不會變更類別名稱.

5.  設定**名稱的複數表示**要**已啟用** = **True**將複數表示規則套用至類別物件的名稱新增至**O/R設計工具**。

## <a name="see-also"></a>另請參閱

- [LINQ to SQL 工具，在 Visual Studio 中](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [存取 Visual Studio 中的資料](../data-tools/accessing-data-in-visual-studio.md)