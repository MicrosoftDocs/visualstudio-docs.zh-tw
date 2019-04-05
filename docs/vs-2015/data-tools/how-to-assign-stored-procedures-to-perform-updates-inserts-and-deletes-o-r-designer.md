---
title: HOW TO：指定預存程序，以執行更新、 插入和刪除 （O-R 設計工具） |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: e88224ab-ff61-4a3a-b6b8-6f3694546cac
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 957c1fe49d222a691160eadc4b2cf08f8a20a65a
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58942928"
---
# <a name="how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-or-designer"></a>HOW TO：指派用來執行更新、插入和刪除的預存程序 (O/R 設計工具)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
預存程序 (Stored Procedure) 可以加入至 O/R 設計工具，而且可以當成一般 <xref:System.Data.Linq.DataContext> 方法來執行。 它們也可用來覆寫預設值[!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)]執行插入、 更新和刪除時的變更儲存至資料庫的實體類別的執行階段行為 (例如，在呼叫時，才<xref:System.Data.Linq.DataContext.SubmitChanges%2A>方法)。  
  
> [!NOTE]
>  如果預存程序傳回的值需要送回給用戶端 (例如，在預存程序中計算的值)，請在預存程序中建立輸出參數。 如果您無法使用輸出參數，請撰寫部分方法實作 (Implementation)，而不要依賴 O/R 設計工具產生的覆寫作業。 與資料庫產生的值對應的成員，必須在 INSERT 或 UPDATE 作業成功完成之後設定為適當值。 如需詳細資訊，請參閱 <<c0> [ 開發人員在覆寫預設行為的責任](http://msdn.microsoft.com/library/c6909ddd-e053-46a8-980c-0e12a9797be1)。  
  
> [!NOTE]
>  [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] 會自動針對識別 (自動遞增)、rowguidcol (資料庫產生的 GUID) 和時間戳記資料行處理資料庫產生的值。 其他資料行型別的資料庫產生值將非預期地產生 null 值。 若要傳回資料庫產生的值，您應該手動將 <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> 設定為 `true`，並將 <xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A> 設定為下列其中一項：<xref:System.Data.Linq.Mapping.AutoSync>、<xref:System.Data.Linq.Mapping.AutoSync> 或 <xref:System.Data.Linq.Mapping.AutoSync>。  
  
## <a name="configuring-the-update-behavior-of-an-entity-class"></a>設定實體類別的更新行為  
 利用 [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] 實體類別中的資料變更來更新資料庫 (插入、更新和刪除) 的邏輯，預設是由 [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] 執行階段所提供。 執行階段會建立預設資料表 （資料行和主索引鍵資訊） 的結構描述為基礎的 Insert、 Update 和 Delete 命令。 當不需要的預設行為時，您可以設定更新行為，指派特定的預存程序來執行所需的插入、 更新和刪除作業來操作您的資料表中的資料。 未產生預設行為時 (例如，實體類別是對應至檢視時)，同樣可以這樣做。 最後，在資料庫需要透過預存程序進行資料表存取時，也可以覆寫預設更新行為。  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
#### <a name="to-assign-stored-procedures-to-override-the-default-behavior-of-an-entity-class"></a>若要指派預存程序以覆寫實體類別的預設行為  
  
1.  在設計工具中開啟 **LINQ to SQL** 檔案。 (按兩下中的.dbml 檔案**方案總管 中**。)  
  
2.  在 **伺服器總管**/**資料庫總管**，依序展開**預存程序**並找出您想要用於 Insert、 Update、 預存程序和/或刪除的實體類別的命令。  
  
3.  將預存程序拖曳至 O/R 設計工具。  
  
     預存程序會加入至方法窗格做為 <xref:System.Data.Linq.DataContext> 方法。 如需詳細資訊，請參閱 < [DataContext 方法 （O/R 設計工具）](../data-tools/datacontext-methods-o-r-designer.md)。  
  
4.  選取想要使用預存程序執行更新的實體類別。  
  
5.  在 [屬性] 視窗中，選取要覆寫的命令 (**Insert**、**Update** 或 **Delete**)。  
  
6.  按一下 [使用執行階段] 字組旁邊的省略符號 (...)，以開啟 [設定行為] 對話方塊。  
  
7.  選取 [自訂]。  
  
8.  在 [自訂] 清單中，選取所需的預存程序。  
  
9. 檢查 [方法引數] 和 [類別屬性] 清單，以確認 [方法引數] 對應至適當的 [類別屬性]。 對應的原始方法引數 (Original_*ArgumentName*) 至原始屬性 (*PropertyName* (Original)) 的 Update 和 Delete 命令。  
  
    > [!NOTE]
    >  根據預設，方法引數會對應至同名的類別屬性。 如果屬性名稱變更，使得資料表與實體類別之間不再對應，則您可能需要選取當 O/R 設計工具無法判斷正確的對應時，所要對應的對等類別屬性。  
  
10. 按一下 [確定] 或 [套用]。  
  
    > [!NOTE]
    >  完成每一項變更後按一下 [套用]，即可繼續設定每個類別/行為組合的行為。 如果您變更了類別或行為再按一下 **套用**、 提供讓您套用任何變更將會出現警告對話方塊。  
  
     若要還原為使用預設執行階段邏輯進行更新，請按一下 Insert、 Update、 旁邊的省略符號或 Delete 命令中的**屬性** 視窗，然後選取**使用執行階段**在**設定行為** 對話方塊。  
  
## <a name="see-also"></a>另請參閱  
 [LINQ to SQL 工具，在 Visual Studio 中](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [DataContext 方法 （O/R 設計工具）](../data-tools/datacontext-methods-o-r-designer.md)   
 [逐步解說：建立 LINQ to SQL 類別 （O-R 設計工具）](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)   
 [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)   
 [插入、更新和刪除作業](http://msdn.microsoft.com/library/26a43a4f-83c9-4732-806d-bb23aad0ff6b)
