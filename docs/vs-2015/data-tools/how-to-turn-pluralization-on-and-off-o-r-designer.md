---
title: 如何：開啟和關閉複數表示（O-R 設計工具） |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 9b693bc3-303a-40a9-97ee-9cef5ca3ae81
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: afe8c8a4429efb83c09d80a5dd00dfe08b0d63e3
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72665939"
---
# <a name="how-to-turn-pluralization-on-and-off-or-designer"></a>如何：開啟和關閉複數表示 (O/R 設計工具)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

根據預設，當您將名稱結尾為 s 或 from 的資料庫物件從**伺服器總管**/**資料庫總管**拖曳至[Visual Studio 中的 LINQ to SQL 工具](../data-tools/linq-to-sql-tools-in-visual-studio2.md)時，所產生之實體類別的名稱會從複數變更為單. 這是為了更正確地呈現具現化 (Instantiated) 的實體類別對應至單一筆記錄的情況。 例如，將名為 Customers 的資料表加入至 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]會產生實體類別 Customer，原因是這個類別只會保留單一客戶的資料。

> [!NOTE]
> 只有在英文版的 Visual Studio 中，才會啟用複數表示。

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

### <a name="to-turn-pluralization-on-and-off"></a>若要開啟和關閉複數表示

1. 在 [ **工具** ] 功能表上按一下 [ **選項**]。

2. 展開 [選項] 對話方塊中的 [資料庫工具]。

> [!NOTE]
> 如果看不到 [資料庫工具] 節點，請選取 [顯示所有設定]。

1. 按一下 [O/R 設計工具]。

2. 將**名稱的複數表示**設定為**Enabled**  = **False**以設定 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]，使其不會變更類別名稱。

3. 將 [**名稱複數表示**] 設定為 [**已啟用** = **True** ]，將複數表示規則套用至新增至 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] 之物件的類別名稱。

## <a name="see-also"></a>請參閱
 [Visual Studio 中的 LINQ to SQL 工具](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) [存取 Visual Studio 中的資料](../data-tools/accessing-data-in-visual-studio.md)
