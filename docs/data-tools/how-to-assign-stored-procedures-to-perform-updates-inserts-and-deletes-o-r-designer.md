---
title: 在 LINQ to SQL 中使用預存程式來更新資料
description: 使用 LINQ to SQL 物件關聯式設計工具 (O/R 設計工具) 中的預存程式來執行更新、插入和刪除資料。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: e88224ab-ff61-4a3a-b6b8-6f3694546cac
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: f0b7ab161a252e1d3a89ef856325963bddffdc56
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99866849"
---
# <a name="how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-or-designer"></a>如何：指派用來執行更新、插入和刪除的預存程序 (O/R 設計工具)

預存程序可以新增至 **O/R 設計工具**，而且可以作為一般 <xref:System.Data.Linq.DataContext> 方法來執行。 它們也可以用來覆寫預設的 LINQ to SQL 執行時間行為，此行為會在將變更從實體類別儲存至資料庫時執行插入、更新和刪除 (例如，在呼叫 <xref:System.Data.Linq.DataContext.SubmitChanges%2A>) 的方法時。

> [!NOTE]
> 如果預存程序傳回的值需要送回給用戶端 (例如，在預存程序中計算的值)，請在預存程序中建立輸出參數。 如果您無法使用輸出參數，請撰寫部分方法實作 (Implementation)，而不要依賴 O/R 設計工具產生的覆寫作業。 與資料庫產生的值對應的成員，必須在 INSERT 或 UPDATE 作業成功完成之後設定為適當值。 如需詳細資訊，請參閱 [開發人員覆寫預設行為的責任](/dotnet/framework/data/adonet/sql/linq/responsibilities-of-the-developer-in-overriding-default-behavior)。

> [!NOTE]
> LINQ to SQL 會自動為身分識別 (自動遞增) 、rowguidcol (資料庫產生的 GUID) 和時間戳記資料行，自動處理資料庫產生的值。 其他資料行型別的資料庫產生值將非預期地產生 null 值。 若要傳回資料庫產生的值，您應該手動將 <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> 設定為 **true** ，並將設定為 <xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A> 下列其中一項： [自動同步. Always](<xref:System.Data.Linq.Mapping.AutoSync.Always>)、 [自動同步](<xref:System.Data.Linq.Mapping.AutoSync.OnInsert>)或 [自動同步. OnUpdate](<xref:System.Data.Linq.Mapping.AutoSync.OnUpdate>)。

## <a name="configure-the-update-behavior-of-an-entity-class"></a>設定實體類別的更新行為

根據預設，更新資料庫 (的邏輯會在 LINQ to SQL 執行時間提供 LINQ to SQL 實體類別中對資料所做的變更時，插入、更新和刪除) 。 執行階段會根據資料表的結構描述 (資料行和主索引鍵資訊)，建立預設的 INSERT、UPDATE 和 DELETE 命令。 如果不需要預設行為，您可以藉由指派特定的預存程式來執行運算元據表中資料所需的插入、更新和刪除動作，來設定更新行為。 未產生預設行為時 (例如，實體類別是對應至檢視時)，同樣可以這樣做。 最後，在資料庫需要透過預存程序進行資料表存取時，也可以覆寫預設更新行為。

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-assign-stored-procedures-to-override-the-default-behavior-of-an-entity-class"></a>若要指派預存程序以覆寫實體類別的預設行為

1. 在設計工具中開啟 **LINQ to SQL** 檔案。 (按兩下 [方案總管] 中的 **.dbml** 檔案。)

2. 展開 [伺服器總管] 或 [資料庫總管] 中的 [預存程序]，尋找您希望當成實體類別之 Insert、Update 和 (或) Delete 命令使用的預存程序。

3. 將預存程序拖曳至 **O/R 設計工具**。

     預存程序會加入至方法窗格做為 <xref:System.Data.Linq.DataContext> 方法。 如需詳細資訊，請參閱 [DataCoNtext 方法 (O/R 設計工具) ](../data-tools/datacontext-methods-o-r-designer.md)。

4. 選取想要使用預存程序執行更新的實體類別。

5. 在 [屬性] 視窗中，選取要覆寫的命令 (**Insert**、**Update** 或 **Delete**)。

6. 按一下 [使用執行階段] 字組旁邊的省略符號 (...)，以開啟 [設定行為] 對話方塊。

7. 選取 [自訂]。

8. 在 [自訂] 清單中，選取所需的預存程序。

9. 檢查 [方法引數] 和 [類別屬性] 清單，以確認 [方法引數] 對應至適當的 [類別屬性]。 將原始方法引數 (`Original_<ArgumentName>`) 對應至 `<PropertyName> (Original)` 和命令 () 的原始 `Update` 屬性 `Delete` 。

    > [!NOTE]
    > 根據預設，方法引數會對應至同名的類別屬性。 如果屬性名稱變更，使得資料表與實體類別之間不再對應，則您可能需要選取當 O/R 設計工具無法判斷正確的對應時，所要對應的對等類別屬性。

10. 按一下 [確定] 或 [套用]。

    > [!NOTE]
    > 您可以繼續設定每個類別和行為組合的行為，只要在進行每項 **變更之後按一下** [套用] 即可。 如果您在按一下 [套用] 之前變更了類別或行為，則會出現警告 **對話方塊，並** 讓您有機會套用您的變更。

若要還原成使用預設執行階段邏輯來進行更新，請在 [屬性] 視窗中按一下 [Insert]、[Update] 或 [Delete] 命令旁邊的省略符號，然後選取 [設定行為] 對話方塊中的 [使用執行階段]。

## <a name="see-also"></a>另請參閱

- [Visual Studio 中的 LINQ to SQL 工具](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [DataContext 方法](../data-tools/datacontext-methods-o-r-designer.md)
- [LINQ to SQL ( .NET Framework) ](/dotnet/framework/data/adonet/sql/linq/index)
- [插入、更新和刪除作業 ( .NET Framework) ](/dotnet/framework/data/adonet/sql/linq/insert-update-and-delete-operations)
