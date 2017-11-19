---
title: "使用預存程序來執行更新、 插入和刪除 Linq to SQL O/R 設計工具中 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e88224ab-ff61-4a3a-b6b8-6f3694546cac
caps.latest.revision: "2"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: f0d6910d2bf449172bac86a3ecd18be8169ef244
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/09/2017
---
# <a name="how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-or-designer"></a>如何： 指派預存程序來執行更新、 插入和刪除 （O/R 設計工具）
預存程序 (Stored Procedure) 可以加入至 O/R 設計工具，而且可以當成一般 <xref:System.Data.Linq.DataContext> 方法來執行。 也可以使用覆寫預設[!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)]執行插入、 更新和刪除時變更儲存至資料庫的實體類別的執行階段行為 (例如，當呼叫<xref:System.Data.Linq.DataContext.SubmitChanges%2A>方法)。  
  
> [!NOTE]
>  如果預存程序傳回的值需要送回給用戶端 (例如，在預存程序中計算的值)，請在預存程序中建立輸出參數。 如果您無法使用輸出參數，請撰寫部分方法實作 (Implementation)，而不要依賴 O/R 設計工具產生的覆寫作業。 與資料庫產生的值對應的成員，必須在 INSERT 或 UPDATE 作業成功完成之後設定為適當值。 如需詳細資訊，請參閱[開發人員覆寫預設行為的責任](/dotnet/framework/data/adonet/sql/linq/responsibilities-of-the-developer-in-overriding-default-behavior)。  
  
> [!NOTE]
>  [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] 會自動針對識別 (自動遞增)、rowguidcol (資料庫產生的 GUID) 和時間戳記資料行處理資料庫產生的值。 其他資料行型別的資料庫產生值將非預期地產生 null 值。 若要傳回資料庫產生的值，您應該手動將 <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> 設定為 `true`，並將 <xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A> 設定為下列其中一項：<xref:System.Data.Linq.Mapping.AutoSync>、<xref:System.Data.Linq.Mapping.AutoSync> 或 <xref:System.Data.Linq.Mapping.AutoSync>。  
  
## <a name="configuring-the-update-behavior-of-an-entity-class"></a>設定實體類別的更新行為  
 根據預設，更新中的資料所做的變更 （插入、 更新和刪除） 資料庫的邏輯[!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)]實體類別由提供[!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)]執行階段。 執行階段建立預設 INSERT、 UPDATE 和 DELETE 命令為基礎的資料表 （資料行和主索引鍵資訊） 的結構描述。 預設行為不需要時，您可以藉由指派特定的預存程序執行所需的插入、 更新和刪除操作您的資料表中的資料所需的設定更新行為。 未產生預設行為時 (例如，實體類別是對應至檢視時)，同樣可以這樣做。 最後，在資料庫需要透過預存程序進行資料表存取時，也可以覆寫預設更新行為。  
  
[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
#### <a name="to-assign-stored-procedures-to-override-the-default-behavior-of-an-entity-class"></a>若要指派預存程序以覆寫實體類別的預設行為  
  
1.  開啟**LINQ to SQL**設計工具中的檔案。 (按兩下中的.dbml 檔案**方案總管 中**。)  
  
2.  在**伺服器總管**/**資料庫總管**，依序展開**預存程序**並找出您想要用於 Insert、 Update、 預存程序和 （或) Delete 命令的實體類別。  
  
3.  將預存程序拖曳至 O/R 設計工具。  
  
     預存程序會加入至方法窗格做為 <xref:System.Data.Linq.DataContext> 方法。 如需詳細資訊，請參閱[DataContext 方法 （O/R 設計工具）](../data-tools/datacontext-methods-o-r-designer.md)。  
  
4.  選取想要使用預存程序執行更新的實體類別。  
  
5.  在**屬性**視窗中，選取要覆寫的命令 (**插入**，**更新**，或**刪除**)。  
  
6.  按一下文字旁邊的省略符號 （...）**使用執行階段**開啟**設定行為** 對話方塊。  
  
7.  選取**自訂**。  
  
8.  選取所要的預存程序中**自訂**清單。  
  
9. 檢查清單**方法引數**和**類別屬性**可讓您確認**方法引數**對應至適當**類別屬性**. 對應的原始方法引數 (Original_*引數名稱*) 至原始屬性 (*PropertyName* (Original)) 的 Update 和 Delete 命令。  
  
    > [!NOTE]
    >  根據預設，方法引數會對應至同名的類別屬性。 如果屬性名稱變更，使得資料表與實體類別之間不再對應，則您可能需要選取當 O/R 設計工具無法判斷正確的對應時，所要對應的對等類別屬性。  
  
10. 按一下**確定**或**套用**。  
  
    > [!NOTE]
    >  您可以繼續設定每個類別/行為組合的行為，當您按一下**套用**每一項變更之後。 如果您變更了類別或行為後，才按一下**套用**，提供可以套用任何變更將會出現警告對話方塊。  
  
若要還原為使用預設的執行階段邏輯進行更新，請按一下 Insert、 Update、 旁邊的省略符號或刪除命令中的**屬性**視窗，然後選取**使用執行階段**中**設定行為** 對話方塊。  
  
## <a name="see-also"></a>請參閱
[LINQ to SQL 工具，Visual Studio 中](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
[DataContext 方法](../data-tools/datacontext-methods-o-r-designer.md)   
[LINQ to SQL (.NET Framework)](/dotnet/framework/data/adonet/sql/linq/index)   
[插入、 更新和刪除作業 (.NET Framework)](/dotnet/framework/data/adonet/sql/linq/insert-update-and-delete-operations)