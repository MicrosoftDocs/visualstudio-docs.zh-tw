---
title: 如何：開啟和關閉複數表示 (O-R 設計工具)
description: 瞭解如何在物件關聯式設計工具 (O/R 設計工具) 中開啟和關閉複數表示。 預設設定會將複數名稱轉換成單數。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 9b693bc3-303a-40a9-97ee-9cef5ca3ae81
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 609af4ef71a6ed73bd1d9599d76d8eb64073efd8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99858692"
---
# <a name="how-to-turn-pluralization-on-and-off-or-designer"></a>如何：開啟和關閉複數表示 (O/R 設計工具)
依預設，當您將名稱結尾為或 **伺服器總管** 或 **資料庫總管** 的資料庫物件拖曳至 [Visual Studio 中的 LINQ to SQL 工具](../data-tools/linq-to-sql-tools-in-visual-studio2.md)時，所產生之實體類別的名稱會從複數變更為單數。 這是為了更正確地呈現具現化 (Instantiated) 的實體類別對應至單一筆記錄的情況。 例如，將資料表加入 `Customers` 至 **O/R 設計** 工具會產生名為的實體類別 `Customer` ，因為類別只會保留單一客戶的資料。

> [!NOTE]
> 只有在英文版的 Visual Studio 中，才會啟用複數表示。

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-turn-pluralization-on-and-off"></a>若要開啟和關閉複數表示

1. 在 **[工具]** 功能表上，按一下 **[選項]** 。

2. 展開 [選項] 對話方塊中的 [資料庫工具]。

    > [!NOTE]
    > 如果看不到 [資料庫工具] 節點，請選取 [顯示所有設定]。

3. 按一下 [O/R 設計工具]。

4. 將 [**名稱的複數表示**] 設定為 [**啟用**  =  **False** ]，以設定 **O/R 設計** 工具，讓它不會變更類別名稱。

5. 將 [**名稱的複數表示**]**設定為 [**  =  **True** ]，將複數表示規則套用至已加入至 **O/R 設計** 工具之物件的類別名稱。

## <a name="see-also"></a>另請參閱

- [Visual Studio 中的 LINQ to SQL 工具](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [存取 Visual Studio 中的資料](../data-tools/accessing-data-in-visual-studio.md)
