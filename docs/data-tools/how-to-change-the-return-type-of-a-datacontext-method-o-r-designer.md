---
title: 如何： 變更 DataContext 方法 （O-R 設計工具） 的傳回型別
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c5b66bff-6dbb-43c0-bffa-317133ca5b9e
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 5c67d6dea4c64e858acdab25ecc4a6cede6bf262
ms.sourcegitcommit: e9d1018a01af62c3dc5aeb6b325faba7e20bd496
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/28/2018
ms.locfileid: "37089353"
---
# <a name="how-to-change-the-return-type-of-a-datacontext-method-or-designer"></a>如何： 變更 DataContext 方法 （O/R 設計工具） 的傳回型別
傳回型別<xref:System.Data.Linq.DataContext>（根據預存程序或函式建立） 的方法有所不同卸除預存程序或函式中的地方**O/R Designer**。 如果將項目直接放入現有的實體類別，且預存程序或函式所傳回資料的結構描述符合實體類別的型態，則建立的 <xref:System.Data.Linq.DataContext> 方法會具有該實體類別的傳回型別。 如果您將項目放的空白區域**O/R Designer**、<xref:System.Data.Linq.DataContext>建立方法會傳回自動產生的型別。 您可以在將 <xref:System.Data.Linq.DataContext> 方法加入至方法窗格後，變更方法的傳回型別。 若要檢查或變更的傳回型別<xref:System.Data.Linq.DataContext>方法中，選取它，然後按一下**傳回型別**中的屬性**屬性**視窗。

> [!NOTE]
>  您無法還原<xref:System.Data.Linq.DataContext>有傳回類型設定為實體類別，以傳回自動產生的型別所使用的方法**屬性**視窗。 若要還原<xref:System.Data.Linq.DataContext>方法來傳回自動產生的型別中，您必須將原始資料庫物件拖曳至**O/R 設計工具**一次。

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="to-change-the-return-type-of-a-datacontext-method-from-the-auto-generated-type-to-an-entity-class"></a>若要將 DataContext 方法的傳回型別從自動產生的型別變更為實體類別

1.  選取方法窗格中的 <xref:System.Data.Linq.DataContext> 方法。

2.  選取 [**傳回型別**中**屬性**] 視窗，然後選取可用的實體類別**傳回型別**清單。 如果所需的實體類別不在清單中，將它新增至或建立中**O/R Designer**將它新增至清單。

3.  儲存 *.dbml*檔案。

## <a name="to-change-the-return-type-of-a-datacontext-method-from-an-entity-class-back-to-the-auto-generated-type"></a>若要將 DataContext 方法的傳回型別從實體類別變更為自動產生的型別

1.  選取 <xref:System.Data.Linq.DataContext>方法中的**方法**窗格並將它刪除。

2.  將資料庫物件從**伺服器總管**或**資料庫總管**上的空白區域**O/R Designer**。

3.  儲存 *.dbml*檔案。

## <a name="see-also"></a>另請參閱

- [LINQ to SQL 工具，在 Visual Studio 中](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [DataContext 方法 （O/R 設計工具）](../data-tools/datacontext-methods-o-r-designer.md)
- [如何： 建立對應至預存程序和函式 （O/R 設計工具） 的 DataContext 方法](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)