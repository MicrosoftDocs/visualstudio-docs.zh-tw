---
title: 使用預存程序，以執行更新、 插入和刪除 Linq to SQL O/R 設計工具中
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: e88224ab-ff61-4a3a-b6b8-6f3694546cac
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: b7fd690997b7d7b58f8d1c1f84ea7f471d4fe496
ms.sourcegitcommit: e9d1018a01af62c3dc5aeb6b325faba7e20bd496
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/28/2018
ms.locfileid: "37089772"
---
# <a name="how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-or-designer"></a>如何： 指派預存程序來執行更新、 插入和刪除 （O/R 設計工具）

預存程序可以加入至**O/R Designer**並執行與一般<xref:System.Data.Linq.DataContext>方法。 它們也可用來覆寫預設 LINQ to SQL 的執行階段行為，執行插入、 更新和刪除時儲存到資料庫的實體類別變更 (例如，在呼叫時，才<xref:System.Data.Linq.DataContext.SubmitChanges%2A>方法)。

> [!NOTE]
> 如果預存程序傳回的值需要送回給用戶端 (例如，在預存程序中計算的值)，請在預存程序中建立輸出參數。 如果您無法使用輸出參數，請撰寫部分方法實作 (Implementation)，而不要依賴 O/R 設計工具產生的覆寫作業。 與資料庫產生的值對應的成員，必須在 INSERT 或 UPDATE 作業成功完成之後設定為適當值。 如需詳細資訊，請參閱 <<c0> [ 開發人員在覆寫預設行為的責任](/dotnet/framework/data/adonet/sql/linq/responsibilities-of-the-developer-in-overriding-default-behavior)。

> [!NOTE]
> LINQ to SQL 會處理資料庫產生的值，會自動針對識別 （自動遞增）、 rowguidcol (資料庫產生的 GUID) 和時間戳記資料行。 其他資料行型別的資料庫產生值將非預期地產生 null 值。 若要傳回資料庫產生的值，您應該手動設定<xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>來 **，則為 true**並<xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A>的下列其中一個： [AutoSync.Always](<xref:System.Data.Linq.Mapping.AutoSync.Always>)， [AutoSync.OnInsert](<xref:System.Data.Linq.Mapping.AutoSync.OnInsert>)，或[AutoSync.OnUpdate](<xref:System.Data.Linq.Mapping.AutoSync.OnUpdate>)。

## <a name="configure-the-update-behavior-of-an-entity-class"></a>設定實體類別的更新行為

根據預設，更新在 LINQ to SQL 實體類別的資料所做的變更 （插入、 更新和刪除） 資料庫的邏輯是由 LINQ to SQL 執行階段提供。 執行階段會建立預設資料表 （資料行和主索引鍵資訊） 的結構描述為基礎的 INSERT、 UPDATE 和 DELETE 命令。 當不需要的預設行為時，您可以設定更新行為，指派特定的預存程序來執行所需的插入、 更新和刪除，才能管理您的資料表中的資料。 未產生預設行為時 (例如，實體類別是對應至檢視時)，同樣可以這樣做。 最後，在資料庫需要透過預存程序進行資料表存取時，也可以覆寫預設更新行為。

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-assign-stored-procedures-to-override-the-default-behavior-of-an-entity-class"></a>若要指派預存程序以覆寫實體類別的預設行為

1.  開啟**LINQ to SQL**設計工具中的檔案。 (按兩下 **.dbml**中的檔案**方案總管 中**。)

2.  在 **伺服器總管**或**資料庫總管**，展開**預存程序**並找出您想要用於 Insert、 Update 和/或刪除的預存程序實體類別的命令。

3.  拖曳到預存程序**O/R Designer**。

     預存程序會加入至方法窗格做為 <xref:System.Data.Linq.DataContext> 方法。 如需詳細資訊，請參閱 < [DataContext 方法 （O/R 設計工具）](../data-tools/datacontext-methods-o-r-designer.md)。

4.  選取想要使用預存程序執行更新的實體類別。

5.  在 [**屬性**] 視窗中，選取要覆寫的命令 (**插入**， **Update**，或**刪除**)。

6.  按一下省略符號 （...） 文字旁邊**使用執行階段**來開啟**設定行為** 對話方塊。

7.  選取 **來自訂**。

8.  選取所需的預存程序中**自訂**清單。

9. 檢查清單**方法引數**並**類別內容**確認**方法引數**對應至適當**類別內容**. 對應的原始方法引數 (`Original_<ArgumentName>`) 至原始屬性 (`<PropertyName> (Original)`) 的`Update`和`Delete`命令。

    > [!NOTE]
    > 根據預設，方法引數會對應至同名的類別屬性。 如果屬性名稱變更，使得資料表與實體類別之間不再對應，則您可能需要選取當 O/R 設計工具無法判斷正確的對應時，所要對應的對等類別屬性。

10. 按一下  **確定**或是**套用**。

    > [!NOTE]
    >  您可以繼續設定每個類別和行為組合的行為，只要您按**套用**每一項變更之後。 如果您變更了類別或行為再按一下 [**套用**，警告] 對話方塊隨即出現，並提供您的機會，以套用變更。

若要還原為使用預設執行階段邏輯進行更新，請按一下省略符號旁**插入**，**更新**，或**刪除**命令**屬性**  視窗，然後選取**使用執行階段**中**設定行為** 對話方塊。

## <a name="see-also"></a>另請參閱

- [LINQ to SQL 工具，在 Visual Studio 中](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [DataContext 方法](../data-tools/datacontext-methods-o-r-designer.md)
- [LINQ to SQL (.NET Framework)](/dotnet/framework/data/adonet/sql/linq/index)
- [插入、 更新和刪除作業 (.NET Framework)](/dotnet/framework/data/adonet/sql/linq/insert-update-and-delete-operations)