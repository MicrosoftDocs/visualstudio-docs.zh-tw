---
title: 作法：建立 LINQ to SQL 類別對應至資料表和檢視 （O-R 設計工具） |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 0fb78bbc-7a78-4ab4-b32f-85ece912e660
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: b9bff102fbf87149e3adc80029eea17132e9b1b7
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65697720"
---
# <a name="how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-or-designer"></a>作法：建立對應至資料表和檢視的 LINQ to SQL 類別 (O/R 設計工具)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
LINQ to SQL 類別對應至資料庫資料表和檢視表稱為*實體類別*。 實體類別對應至記錄，而實體類別的個別屬性對應至組成記錄的個別資料行。 建立實體類別為基礎的資料庫資料表或檢視表拖曳資料表或檢視表，從**伺服器總管**/**資料庫總管**拖曳至[LINQ to SQL 中的工具Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)。 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]產生的類別，並套用特定 [！要啟用 LINQ to SQL 屬性 [！LINQ to SQL 功能 (資料通訊和編輯功能<xref:System.Data.Linq.DataContext>)。 如需詳細資訊 [！LINQ to SQL 類別，請參閱[LINQ to SQL 物件模型](https://msdn.microsoft.com/library/81dd0c37-e2a4-4694-83b0-f2e49e693810)。

> [!NOTE]
> [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]是簡單的物件關聯式對應程式，因為它支援僅為 1:1 對應關聯性。 換句話說，實體類別與資料庫資料表或檢視之間只可以有一對一對應關聯性。 目前不支援複雜對應 (例如，將實體類別對應至多個資料表)。 不過，您可以將一個實體類別對應至一個將多個相關資料表聯結 (Join) 在一起的檢視。

## <a name="create-linq-to-sql-classes-that-are-mapped-to-database-tables-or-views"></a>建立會對應至資料庫資料表或檢視的 LINQ to SQL 類別
 將資料表或檢視從**伺服器總管**/**資料庫總管**拖曳至[!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]建立實體類別，除了<xref:System.Data.Linq.DataContext>所使用的方法執行更新。

 根據預設，[！LINQ 至 SQL 執行階段會建立邏輯，以從可更新的實體類別的變更儲存回資料庫。 這個邏輯是根據資料表的結構描述 (資料行定義和主索引鍵資訊)。 如果不想使用這種行為，您可以設定實體類別，以使用預存程序來執行插入、 更新和刪除而不是使用預設值 [！LINQ to SQL 的執行階段行為。 如需詳細資訊，請參閱[如何：指派用來執行更新、插入和刪除的預存程序 (O/R 設計工具)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)。

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

#### <a name="to-create-linq-to-sql-classes-that-are-mapped-to-database-tables-or-views"></a>若要建立會對應至資料庫資料表或檢視的 LINQ to SQL 類別

1. 在**伺服器**/**資料庫總管**，依序展開**資料表**或**檢視**並找出資料庫資料表或檢視您想要若要在您的應用程式中使用。

2. 將資料表或檢視拖曳至 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]。

     實體類別隨即建立並出現在設計介面上。 這個實體類別的屬性會對應至所選取資料表或檢視中的資料行。

## <a name="create-an-object-data-source-and-display-the-data-on-a-form"></a>建立物件資料來源並將資料顯示在表單上
 使用建立實體類別之後[!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]，您可以建立物件資料來源，並填入[資料來源視窗](https://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992)將實體類別。

#### <a name="to-create-an-object-data-source-based-on-linq-to-sql-entity-classes"></a>若要根據 LINQ to SQL 實體類別來建立物件資料來源

1. 按一下 [建置] 功能表上的 [建置方案] 來建置您的專案。

2. 按一下 [ **資料** ] 功能表上的 [ **顯示資料來源**]。

3. 在 [ **資料來源** ] 視窗中，按一下 [ **加入新資料來源**]。

4. 按一下 [選擇資料來源類型] 頁面上的 [物件]，然後按一下 [下一步]。

5. 展開節點，並尋找和選取類別。

    > [!NOTE]
    > 如果**客戶**類別無法使用，請取消精靈、建置專案，然後再次執行精靈。

6. 按一下 [完成] 以建立資料來源，然後將 [客戶] 實體類別新增至 [資料來源] 視窗。

7. 將項目從 [資料來源] 視窗拖曳至表單。

## <a name="see-also"></a>另請參閱

- [LINQ to SQL Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) (Visual Studio 中的 LINQ to SQL 工具)
- [逐步解說：建立 LINQ to SQL 類別 （O-R 設計工具）](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)
- [DataContext 方法 (O/R 設計工具)](../data-tools/datacontext-methods-o-r-designer.md)
- [如何：建立對應至預存程序和函式的 DataContext 方法 (O/R 設計工具)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)
- [LINQ to SQL 物件模型](https://msdn.microsoft.com/library/81dd0c37-e2a4-4694-83b0-f2e49e693810)
- [逐步解說：自訂實體類別的插入、更新和刪除行為](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md)
- [逐步解說：將驗證新增至實體類別](https://msdn.microsoft.com/library/85b06a02-b2e3-4534-95b8-d077c8d4c1d7)
- [如何：建立 LINQ to SQL 類別之間的關聯 (關聯性) (O/R 設計工具)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md)