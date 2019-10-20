---
title: 如何：建立對應至預存程式和函式的 DataCoNtext 方法（O-R 設計工具） |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: e7ca32f1-50b3-48af-ad92-ceafd749296a
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 70053b74a4dd2ad569e1e8195f4c9b2e7b214440
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72665971"
---
# <a name="how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-or-designer"></a>如何：建立對應至預存程序和函式的 DataContext 方法 (O/R 設計工具)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

預存程式和函式可以當做 <xref:System.Data.Linq.DataContext> 方法加入至 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]。 只要呼叫這個方法並傳入必要參數，就會在資料庫上執行預存程序或函式，並以 <xref:System.Data.Linq.DataContext> 方法的傳回型別傳回資料。 如需 <xref:System.Data.Linq.DataContext> 方法的詳細資訊，請參閱[DataCoNtext 方法（O/R 設計工具）](../data-tools/datacontext-methods-o-r-designer.md)。

> [!NOTE]
> 預存程序也可以用來覆寫當儲存實體類別 (Class) 的變更至資料庫時，用於執行插入、更新和刪除作業的預設 [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] 執行階段行為。 如需詳細資訊，請參閱[如何：指派預存程式來執行更新、插入和刪除（O/R 設計工具）](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)。

## <a name="creating-datacontext-methods"></a>建立 DataContext 方法
 您可以將預存程式或函式從**伺服器總管/資料庫總管**拖曳至 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]，以建立 <xref:System.Data.Linq.DataContext> 方法。

> [!NOTE]
> 所產生 <xref:System.Data.Linq.DataContext> 方法的傳回型別，會根據預存程序或函式在 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]上的置放位置而不同。 如果將項目直接置放入現有的實體類別，則建立的 <xref:System.Data.Linq.DataContext> 方法會具有該實體類別的傳回型別。 如果將項目放入 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]的空白區域，則建立的 <xref:System.Data.Linq.DataContext> 方法會傳回自動產生的型別。 將 <xref:System.Data.Linq.DataContext> 方法的傳回型別加入至 [方法] 窗格之後，您就可以將它變更。 若要檢查或變更 <xref:System.Data.Linq.DataContext> 方法的傳回型別，請選取該方法，然後檢查 [屬性] 視窗中的 [傳回型別] 屬性。 如需詳細資訊，請參閱[如何：變更 DataCoNtext 方法的傳回型別（O/R 設計工具）](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md)。

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

#### <a name="to-create-datacontext-methods-that-return-automatically-generated-types"></a>若要建立可傳回自動產生型別的 DataContext 方法

1. 在**伺服器總管**/**資料庫總管**中，展開您要使用之資料庫的 [**預存程式**] 節點。

2. 尋找所要的預存程序，並將它拖曳至 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]的空白區域。

     <xref:System.Data.Linq.DataContext> 方法會以自動產生的傳回型別建立，並出現在 [方法] 窗格中。

#### <a name="to-create-datacontext-methods-that-have-the-return-type-of-an-entity-class"></a>若要建立具有實體類別之傳回型別的 DataContext 方法

1. 在**伺服器總管**/**資料庫總管**中，展開您要使用之資料庫的 [**預存程式**] 節點。

2. 尋找所要的預存程序，並將它拖曳至 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]的現有實體類別。

     <xref:System.Data.Linq.DataContext> 方法會以所選取實體類別的傳回型別建立，並出現在 [方法] 窗格中。

> [!NOTE]
> 如需變更現有 <xref:System.Data.Linq.DataContext> 方法之傳回型別的詳細資訊，請參閱[如何：變更 DataCoNtext 方法的傳回型別（O/R 設計工具）](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md)。

## <a name="see-also"></a>請參閱
 [Visual Studio DataCoNtext 方法中的 LINQ to SQL 工具](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [（O/R 設計工具）](../data-tools/datacontext-methods-o-r-designer.md) [逐步解說：建立 LINQ to SQL 類別（o-r 設計工具）](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) [Visual Basic 中的 linq 簡介](https://msdn.microsoft.com/library/3047d86e-0d49-40e2-928b-dc02e46c7984)[如何：在中C#](https://msdn.microsoft.com/library/45e47fcc-cfa1-4b72-b161-d038ae87bd23)
