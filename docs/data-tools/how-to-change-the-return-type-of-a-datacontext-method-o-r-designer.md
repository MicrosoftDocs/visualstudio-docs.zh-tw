---
title: 如何： 變更 DataContext 方法 （O R 設計工具） 的傳回型別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c5b66bff-6dbb-43c0-bffa-317133ca5b9e
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 0b9660433b357d6ec1ddead86611387e0cb5c11a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-change-the-return-type-of-a-datacontext-method-or-designer"></a>如何： 變更 DataContext 方法 （O/R 設計工具） 的傳回型別
<xref:System.Data.Linq.DataContext> 方法 (根據預存程序 (Stored Procedure) 或函式所建立) 的傳回型別，會隨預存程序或函式在 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]中的置放位置而不同。 如果將項目直接放入現有的實體類別，且預存程序或函式所傳回資料的結構描述符合實體類別的型態，則建立的 <xref:System.Data.Linq.DataContext> 方法會具有該實體類別的傳回型別。 如果您將項目放入 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]的空白區域，則建立的 <xref:System.Data.Linq.DataContext> 方法會傳回自動產生的型別。 您可以在將 <xref:System.Data.Linq.DataContext> 方法加入至方法窗格後，變更方法的傳回型別。 若要檢查或變更的傳回型別<xref:System.Data.Linq.DataContext>方法中，選取它，然後按一下 **傳回型別**屬性**屬性**視窗。  
  
> [!NOTE]
>  您也無法還原<xref:System.Data.Linq.DataContext>方法，藉由傳回自動產生的型別設定為實體類別的傳回型別**屬性**視窗。 若要將 <xref:System.Data.Linq.DataContext> 方法還原成傳回自動產生的型別，則必須再次將原始資料庫物件拖曳至 O/R 設計工具。  
  
[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## <a name="to-change-the-return-type-of-a-datacontext-method-from-the-auto-generated-type-to-an-entity-class"></a>若要將 DataContext 方法的傳回型別從自動產生的型別變更為實體類別  
  
1.  選取方法窗格中的 <xref:System.Data.Linq.DataContext> 方法。  
  
2.  選取**傳回型別**中**屬性**視窗，然後選取可用的實體類別中**傳回型別**清單。 如果所要的實體類別不在清單中，將它加入或建立在[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]將它加入至清單。  
  
3.  儲存 .dbml 檔案。  
  
## <a name="to-change-the-return-type-of-a-datacontext-method-from-an-entity-class-back-to-the-auto-generated-type"></a>若要將 DataContext 方法的傳回型別從實體類別變更為自動產生的型別  
  
1.  選取並刪除方法窗格中的 <xref:System.Data.Linq.DataContext> 方法。  
  
2.  將資料庫物件從**伺服器總管**/**資料庫總管**拖曳到 O/R 設計工具的空白區域。  
  
3.  儲存 .dbml 檔案。  
  
## <a name="see-also"></a>另請參閱
[LINQ to SQL 工具，Visual Studio 中](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
[LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)   
[DataContext 方法 （O/R 設計工具）](../data-tools/datacontext-methods-o-r-designer.md)   
[如何： 建立對應至預存程序和函式 （O/R 設計工具） 的 DataContext 方法](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)