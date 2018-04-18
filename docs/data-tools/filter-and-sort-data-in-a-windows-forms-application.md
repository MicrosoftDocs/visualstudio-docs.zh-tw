---
title: 在 Windows Form 應用程式中的篩選與排序資料 |Microsoft 文件
ms.custom: ''
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
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: a2703a075a2083f960ad644784671a1af033aaee
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="filter-and-sort-data-in-a-windows-forms-application"></a>在 Windows Form 應用程式中的篩選與排序資料
您藉由設定來篩選資料<xref:System.Windows.Forms.BindingSource.Filter%2A>屬性來傳回所要的記錄的字串運算式。  
  
 設定排序資料<xref:System.Windows.Forms.BindingSource.Sort%2A>屬性資料行名稱為您要用來排序，則為附加`DESC`依遞減順序排序，或附加`ASC`以遞增順序排序。  
  
> [!NOTE]
>  如果您的應用程式不會使用<xref:System.Windows.Forms.BindingSource>元件，您可以篩選和排序資料，使用<xref:System.Data.DataView>物件。 如需詳細資訊，請參閱[Dataview](/dotnet/framework/data/adonet/dataset-datatable-dataview/dataviews)。  
  
## <a name="to-filter-data-by-using-a-bindingsource-component"></a>若要篩選資料，藉由使用 BindingSource 元件  
  
-   設定<xref:System.Windows.Forms.BindingSource.Filter%2A>屬性，以您想要傳回的運算式。 例如，下列程式碼會傳回客戶及`CompanyName`以"B"開頭：  
  
     [!code-csharp[VbRaddataDisplaying#6](../data-tools/codesnippet/CSharp/filter-and-sort-data-in-a-windows-forms-application_1.cs)]
     [!code-vb[VbRaddataDisplaying#6](../data-tools/codesnippet/VisualBasic/filter-and-sort-data-in-a-windows-forms-application_1.vb)]  
  
## <a name="to-sort-data-by-using-a-bindingsource-component"></a>若要使用 BindingSource 元件排序資料  
  
-   設定<xref:System.Windows.Forms.BindingSource.Sort%2A>到您要排序的資料行的屬性。 例如，下列程式碼上排序客戶`CompanyName`資料行以遞減的順序：  
  
     [!code-csharp[VbRaddataDisplaying#7](../data-tools/codesnippet/CSharp/filter-and-sort-data-in-a-windows-forms-application_2.cs)]
     [!code-vb[VbRaddataDisplaying#7](../data-tools/codesnippet/VisualBasic/filter-and-sort-data-in-a-windows-forms-application_2.vb)]  
  
## <a name="see-also"></a>另請參閱  
 [將控制項繫結至 Visual Studio 中的資料](../data-tools/bind-controls-to-data-in-visual-studio.md)