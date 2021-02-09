---
title: 在 Windows Forms 應用程式中篩選和排序資料
description: 在 Windows Forms 應用程式中篩選和排序資料。 將 Filter 屬性設定為傳回所需記錄的字串運算式。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- row states, filtering
- data views, sorting
- row version, filtering
- row states
- data views, filtering
- sorting datasets, using data views
- dataset filtering, using data views
ms.assetid: f4f100f1-776d-46dc-b2fd-5b35b98d9561
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: b1708d6871f1acdf437895563d9b5a39dbe93f21
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99858848"
---
# <a name="filter-and-sort-data-in-a-windows-forms-application"></a>在 Windows Forms 應用程式中篩選和排序資料

您可以藉由將屬性設定為傳回所 <xref:System.Windows.Forms.BindingSource.Filter%2A> 需記錄的字串運算式來篩選資料。

您可以藉由將 <xref:System.Windows.Forms.BindingSource.Sort%2A> 屬性設定為您要排序的資料行名稱 `DESC` 、附加以遞減順序排序，或附加 `ASC` 至以遞增順序排序的資料行名稱來排序資料。

> [!NOTE]
> 如果您的應用程式未使用 <xref:System.Windows.Forms.BindingSource> 元件，您可以使用物件來篩選和排序資料 <xref:System.Data.DataView> 。 如需詳細資訊，請參閱 [dataview](/dotnet/framework/data/adonet/dataset-datatable-dataview/dataviews)。

## <a name="to-filter-data-by-using-a-bindingsource-component"></a>使用 BindingSource 元件篩選資料

- 將 <xref:System.Windows.Forms.BindingSource.Filter%2A> 屬性設定為您想要傳回的運算式。 例如，下列程式碼會傳回開頭為 `CompanyName` "B" 的客戶：

     [!code-csharp[VbRaddataDisplaying#6](../data-tools/codesnippet/CSharp/filter-and-sort-data-in-a-windows-forms-application_1.cs)]
     [!code-vb[VbRaddataDisplaying#6](../data-tools/codesnippet/VisualBasic/filter-and-sort-data-in-a-windows-forms-application_1.vb)]

## <a name="to-sort-data-by-using-a-bindingsource-component"></a>使用 BindingSource 元件排序資料

- 將 <xref:System.Windows.Forms.BindingSource.Sort%2A> 屬性設定為您想要排序的資料行。 例如，下列程式碼會以遞減順序排序資料行上的客戶 `CompanyName` ：

     [!code-csharp[VbRaddataDisplaying#7](../data-tools/codesnippet/CSharp/filter-and-sort-data-in-a-windows-forms-application_2.cs)]
     [!code-vb[VbRaddataDisplaying#7](../data-tools/codesnippet/VisualBasic/filter-and-sort-data-in-a-windows-forms-application_2.vb)]

## <a name="see-also"></a>另請參閱

- [將控制項繫結至 Visual Studio 中的資料](../data-tools/bind-controls-to-data-in-visual-studio.md)
