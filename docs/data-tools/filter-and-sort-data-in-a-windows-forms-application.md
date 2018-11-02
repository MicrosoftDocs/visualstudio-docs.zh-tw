---
title: 在 Windows Forms 應用程式中篩選和排序資料
ms.date: 11/04/2016
ms.topic: conceptual
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
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 1868d670458e204f6e503b132aaceab17f3da742
ms.sourcegitcommit: 1df0ae74af03bcf0244129a29fd6bd605efc9f61
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2018
ms.locfileid: "50750919"
---
# <a name="filter-and-sort-data-in-a-windows-forms-application"></a>在 Windows Forms 應用程式中篩選和排序資料

設定篩選資料<xref:System.Windows.Forms.BindingSource.Filter%2A>屬性來傳回所要的記錄的字串運算式。

您藉由設定排序的資料<xref:System.Windows.Forms.BindingSource.Sort%2A>屬性設為資料行名稱，在其要用來排序; 附加`DESC`依遞減順序排序，或是附加`ASC`若要以遞增順序排序。

> [!NOTE]
> 如果您的應用程式不會使用<xref:System.Windows.Forms.BindingSource>元件，您可以篩選和排序資料，使用<xref:System.Data.DataView>物件。 如需詳細資訊，請參閱 < [Dataview](/dotnet/framework/data/adonet/dataset-datatable-dataview/dataviews)。

## <a name="to-filter-data-by-using-a-bindingsource-component"></a>若要篩選資料，藉由使用 BindingSource 元件

-   設定<xref:System.Windows.Forms.BindingSource.Filter%2A>屬性設為您想要傳回的運算式。 例如，下列程式碼會傳回客戶及`CompanyName`以"B"開頭的：

     [!code-csharp[VbRaddataDisplaying#6](../data-tools/codesnippet/CSharp/filter-and-sort-data-in-a-windows-forms-application_1.cs)]
     [!code-vb[VbRaddataDisplaying#6](../data-tools/codesnippet/VisualBasic/filter-and-sort-data-in-a-windows-forms-application_1.vb)]

## <a name="to-sort-data-by-using-a-bindingsource-component"></a>若要使用 BindingSource 元件排序資料

-   設定<xref:System.Windows.Forms.BindingSource.Sort%2A>您想要排序的資料行的屬性。 例如，下列程式碼上排序客戶`CompanyName`資料行以遞減順序：

     [!code-csharp[VbRaddataDisplaying#7](../data-tools/codesnippet/CSharp/filter-and-sort-data-in-a-windows-forms-application_2.cs)]
     [!code-vb[VbRaddataDisplaying#7](../data-tools/codesnippet/VisualBasic/filter-and-sort-data-in-a-windows-forms-application_2.vb)]

## <a name="see-also"></a>另請參閱

- [將控制項繫結至 Visual Studio 中的資料](../data-tools/bind-controls-to-data-in-visual-studio.md)