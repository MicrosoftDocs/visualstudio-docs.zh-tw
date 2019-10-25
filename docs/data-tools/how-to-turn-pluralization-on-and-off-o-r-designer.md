---
title: 作法：開啟和關閉複數表示 (O/R 設計工具)
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 9b693bc3-303a-40a9-97ee-9cef5ca3ae81
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 578a6333d1206553db50ce81f2f499da0481456d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72648336"
---
# <a name="how-to-turn-pluralization-on-and-off-or-designer"></a>作法：開啟和關閉複數表示 (O/R 設計工具)
根據預設，當您將名稱結尾為 s 或 from 的資料庫物件從**伺服器總管**或**資料庫總管**拖曳到[Visual Studio 中的 LINQ to SQL 工具](../data-tools/linq-to-sql-tools-in-visual-studio2.md)時，所產生之實體類別的名稱會從複數變更為單. 這是為了更正確地呈現具現化 (Instantiated) 的實體類別對應至單一筆記錄的情況。 例如，將 `Customers` 資料表加入至**O/R 設計**工具會產生名為 `Customer` 的實體類別，因為該類別只會保存單一客戶的資料。

> [!NOTE]
> 只有在英文版的 Visual Studio 中，才會啟用複數表示。

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-turn-pluralization-on-and-off"></a>若要開啟和關閉複數表示

1. 在 [ **工具** ] 功能表上按一下 [ **選項**]。

2. 展開 [選項] 對話方塊中的 [資料庫工具]。

    > [!NOTE]
    > 如果看不到 [資料庫工具] 節點，請選取 [顯示所有設定]。

3. 按一下 [O/R 設計工具]。

4. 將**名稱的複數表示**設定為**Enabled**  = **False**以設定**O/R 設計**工具，使其不會變更類別名稱。

5. 將 [**名稱的複數表示**] 設定為 [**已啟用** = **True** ]，將複數表示規則套用至新增至**O/R 設計**工具之物件的類別名稱。

## <a name="see-also"></a>另請參閱

- [Visual Studio 中的 LINQ to SQL 工具](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [存取 Visual Studio 中的資料](../data-tools/accessing-data-in-visual-studio.md)