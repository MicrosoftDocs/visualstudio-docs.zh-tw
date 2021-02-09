---
title: 無法刪除選取的類別
description: 無法刪除所選取的類別，因為它是用來當做一或多個 DataContext 方法的傳回類型。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: d68254a0-f3a1-47e2-aed3-a83471e1d711
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: a9948df37df4faf7cc5349b2729ca4f648d973cb
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99866381"
---
# <a name="the-selected-class-cannot-be-deleted-because-it-is-used-as-a-return-type-for-one-or-more-datacontext-methods"></a>無法刪除所選取的類別，因為它是用來當做一或多個 DataContext 方法的傳回類型。

有一個或多個 <xref:System.Data.Linq.DataContext> 方法的傳回型別是選取的實體類別 (Class)。 刪除當做方法之傳回型別的實體類別， <xref:System.Data.Linq.DataContext> 會導致專案編譯失敗。 若要刪除選取的實體類別，請識別使用它的 <xref:System.Data.Linq.DataContext> 方法，並將這些方法的傳回型別設定為不同的實體類別。

若要將 <xref:System.Data.Linq.DataContext> 方法的傳回型別還原成它們原來自動產生的類型，請先從 [方法] 窗格中刪除 <xref:System.Data.Linq.DataContext> 方法，然後再次將物件從 **伺服器總管**/**資料庫總管** 拖曳至 **O/R 設計工具**。

## <a name="to-correct-this-error"></a>更正這個錯誤

1. 選取 [方法] 窗格中的 <xref:System.Data.Linq.DataContext> 方法，然後檢查 [屬性] 視窗中的 [傳回型別] 屬性，以識別將實體類別用作傳回型別的 <xref:System.Data.Linq.DataContext> 方法。

2. 將 **傳回型別** 設定為不同的實體類別，或從方法窗格中刪除 <xref:System.Data.Linq.DataContext> 方法。

## <a name="see-also"></a>另請參閱

- [Visual Studio 中的 LINQ to SQL 工具](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
