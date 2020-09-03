---
title: 變更 DataCoNtext 方法的傳回型別無法復原 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 76b161fc-5075-4192-8d94-f15b02e199e9
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f020aed4c1213d3db008862386704c0f63b86bde
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72662460"
---
# <a name="changing-the-return-type-of-a-datacontext-method-cannot-be-undone"></a>如果變更 DataContext 方法的傳回類型，將無法復原
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

變更 DataContext 方法的傳回型別將無法復原。 若要還原成自動產生的型別，請再次從 [伺服器總管]/[資料庫總管] 將此項目拖曳到 O/R 設計工具上。 您確定要變更此傳回型別嗎?

 <xref:System.Data.Linq.DataContext> 方法的傳回型別會根據項目置放在 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]中的位置而不同。 如果將項目直接置放入現有的實體類別，則會建立具有實體類別之傳回型別的 <xref:System.Data.Linq.DataContext> 方法。 如果您將項目放入 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]的空白區域，則建立的 <xref:System.Data.Linq.DataContext> 方法會傳回自動產生的型別。 您可以在將 <xref:System.Data.Linq.DataContext> 方法加入至方法窗格後，變更方法的傳回型別。 若要檢查或變更 <xref:System.Data.Linq.DataContext> 方法的傳回型別，請選取該方法，然後按一下 [屬性]**** 視窗中的 [傳回型別]**** 屬性。

### <a name="to-change-the-return-type-of-a-datacontext"></a>若要變更 DataContext 的傳回型別

- 按一下 [是]  。

### <a name="to-exit-the-message-box-and-leave-the-return-type-unchanged"></a>若要結束訊息方塊而不變更傳回型別

- 按一下 **[否]** 。

### <a name="to-revert-to-the-original-return-type-after-changing-the-return-type"></a>若要在變更傳回型別之後還原成原始傳回型別

1. 在 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] 上選取 <xref:System.Data.Linq.DataContext> 方法並予以刪除。

2. 在 [伺服器總管]/[資料庫總管]**** 中找出這個項目，並將其拖曳至 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]。

     會建立具有原始預設傳回型別的 <xref:System.Data.Linq.DataContext> 方法。

## <a name="see-also"></a>另請參閱
 [Visual Studio DataCoNtext 方法中的 LINQ to SQL 工具](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [ (o/r 設計工具) ](../data-tools/datacontext-methods-o-r-designer.md) [如何：建立對應至預存程式和函式的 DataCoNtext 方法 (O/r 設計工具) ](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)
