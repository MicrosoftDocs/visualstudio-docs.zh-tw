---
title: 在 Windows Forms 應用程式中篩選和排序資料 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- row states, filtering
- data views, sorting
- row version, filtering
- row states
- data views, filtering
- sorting datasets, using data views
- dataset filtering, using data views
ms.assetid: f4f100f1-776d-46dc-b2fd-5b35b98d9561
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 24c623efc141ff84c2585f967596271d1efbc502
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671653"
---
# <a name="filter-and-sort-data-in-a-windows-forms-application"></a>在 Windows Forms 應用程式中篩選和排序資料
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以藉由將 <xref:System.Windows.Forms.BindingSource.Filter%2A> 屬性設定為傳回所需記錄的字串運算式來篩選資料。

 將 [<xref:System.Windows.Forms.BindingSource.Sort%2A>] 屬性設為您想要排序的資料行名稱，即可排序資料;附加 `DESC` 以遞減順序排序，或附加 `ASC` 以遞增順序排序。

> [!NOTE]
> 如果您的應用程式未使用 <xref:System.Windows.Forms.BindingSource> 元件，您可以使用 <xref:System.Data.DataView> 物件來篩選和排序資料。 如需詳細資訊，請參閱[dataview](https://msdn.microsoft.com/library/0fe5dfa2-c1cd-435f-90b6-b4dd2e3ef34b)。

## <a name="to-filter-data-by-using-a-bindingsource-component"></a>使用 BindingSource 元件來篩選資料

- 將 [<xref:System.Windows.Forms.BindingSource.Filter%2A>] 屬性設為您想要傳回的運算式。 例如，下列程式碼會傳回 `CompanyName` 開頭為 "B" 的客戶：

     [!code-csharp[VbRaddataDisplaying#6](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/Form1.cs#6)]
     [!code-vb[VbRaddataDisplaying#6](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/Form1.vb#6)]

## <a name="to-sort-data-by-using-a-bindingsource-component"></a>使用 BindingSource 元件排序資料

- 將 [<xref:System.Windows.Forms.BindingSource.Sort%2A>] 屬性設為您想要排序的資料行。 例如，下列程式碼會以遞減順序排序 `CompanyName` 資料行上的客戶：

     [!code-csharp[VbRaddataDisplaying#7](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/Form1.cs#7)]
     [!code-vb[VbRaddataDisplaying#7](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/Form1.vb#7)]

## <a name="see-also"></a>請參閱
 [將控制項繫結至 Visual Studio 中的資料](../data-tools/bind-controls-to-data-in-visual-studio.md)
