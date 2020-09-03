---
title: 無法刪除選取的類別，因為它是用來當做一或多個 DataCoNtext 方法的傳回型別 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: d68254a0-f3a1-47e2-aed3-a83471e1d711
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: cf16fe7453388e19308ed603ee9dbbac207cec41
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667263"
---
# <a name="the-selected-class-cannot-be-deleted-because-it-is-used-as-a-return-type-for-one-or-more-datacontext-methods"></a>無法刪除所選取的類別，因為它是用來當做一或多個 DataContext 方法的傳回類型。
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

有一個或多個 <xref:System.Data.Linq.DataContext> 方法的傳回型別是選取的實體類別 (Class)。 刪除被 <xref:System.Data.Linq.DataContext> 方法當做傳回型別的實體類別，會使專案編譯作業失敗。 若要刪除選取的實體類別，請識別使用它的 <xref:System.Data.Linq.DataContext> 方法，並將這些方法的傳回型別設定為不同的實體類別。

 若要將方法的傳回類型還原 <xref:System.Data.Linq.DataContext> 為其原始自動產生的型別，請先 <xref:System.Data.Linq.DataContext> 從方法窗格中刪除方法，然後再次將物件從**伺服器總管** / **資料庫總管**拖曳至 O/R 設計工具。

### <a name="to-correct-this-error"></a>更正這個錯誤

1. 藉 <xref:System.Data.Linq.DataContext> 由 <xref:System.Data.Linq.DataContext> 在 [方法] 窗格中選取方法，然後檢查 [**屬性**] 視窗中的 [傳回**型**別] 屬性，識別使用實體類別做為傳回型別的方法。

2. 將**傳回型別**設定為不同的實體類別，或從方法窗格中刪除 <xref:System.Data.Linq.DataContext> 方法。

## <a name="see-also"></a>另請參閱
 [Visual Studio 逐步解說中的 LINQ to SQL 工具](../data-tools/linq-to-sql-tools-in-visual-studio2.md)[逐步解說：建立 LINQ to SQL 類別 (o-r 設計工具) ](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233) [DatacoNtext 方法 (o/r 設計](../data-tools/datacontext-methods-o-r-designer.md)工具) [如何：變更 DataCoNtext 方法的傳回型別 (o/r 設計工具) ](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md)
