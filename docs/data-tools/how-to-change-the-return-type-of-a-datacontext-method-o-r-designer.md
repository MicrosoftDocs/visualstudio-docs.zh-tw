---
title: 變更 DataCoNtext 方法的傳回類型
description: 當您在物件關聯式設計工具 (O/R 設計工具) 中卸載預存程式或函數時，請瞭解如何變更 DataCoNtext 方法的傳回型別。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: c5b66bff-6dbb-43c0-bffa-317133ca5b9e
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 4226be60f91fb1b9d55e279be2a697861c3f9566
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99858796"
---
# <a name="how-to-change-the-return-type-of-a-datacontext-method-or-designer"></a>如何：變更 DataContext 方法的傳回型別 (O/R 設計工具)
根據 <xref:System.Data.Linq.DataContext> 預存程式或函數所建立 (方法的傳回型別，) 會根據您在 **O/R 設計** 工具中卸載預存程式或函數的位置而有所不同。 如果將項目直接放入現有的實體類別，且預存程序或函式所傳回資料的結構描述符合實體類別的型態，則建立的 <xref:System.Data.Linq.DataContext> 方法會具有該實體類別的傳回型別。 如果您將專案放到 **O/R 設計** 工具的空白區域， <xref:System.Data.Linq.DataContext> 則會建立傳回自動產生之類型的方法。 您可以在將 <xref:System.Data.Linq.DataContext> 方法加入至方法窗格後，變更方法的傳回型別。 若要檢查或變更 <xref:System.Data.Linq.DataContext> 方法的傳回型別，請選取該方法，然後按一下 [屬性] 視窗中的 [傳回型別] 屬性。

> [!NOTE]
> 您無法使用 [屬性] 視窗，將傳回型別設定為實體類別的 <xref:System.Data.Linq.DataContext> 方法還原成傳回自動產生的型別。 若要還原 <xref:System.Data.Linq.DataContext> 方法以傳回自動產生的型別，您必須再次將原始資料庫物件拖曳到 **O/R 設計** 工具上。

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="to-change-the-return-type-of-a-datacontext-method-from-the-auto-generated-type-to-an-entity-class"></a>若要將 DataContext 方法的傳回型別從自動產生的型別變更為實體類別

1. 選取方法窗格中的 <xref:System.Data.Linq.DataContext> 方法。

2. 選取 [屬性] 視窗中的 [傳回型別]，然後在 [傳回型別] 清單中選取可用的實體類別。 如果所需的實體類別不在清單中，請將它加入至 **O/R 設計工具，或在 O/R 設計** 工具中加以建立，以將其新增至清單。

3. 儲存 *.dbml* 檔。

## <a name="to-change-the-return-type-of-a-datacontext-method-from-an-entity-class-back-to-the-auto-generated-type"></a>若要將 DataContext 方法的傳回型別從實體類別變更為自動產生的型別

1. <xref:System.Data.Linq.DataContext>在 [**方法**] 窗格中選取方法，並將其刪除。

2. 從 **伺服器總管** 或 **資料庫總管** 將資料庫物件拖曳到 **O/R 設計** 工具的空白區域。

3. 儲存 *.dbml* 檔。

## <a name="see-also"></a>另請參閱

- [Visual Studio 中的 LINQ to SQL 工具](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [DataCoNtext 方法 (O/R 設計工具) ](../data-tools/datacontext-methods-o-r-designer.md)
- [如何：建立對應至預存程序和函式的 DataContext 方法 (O/R 設計工具)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)
