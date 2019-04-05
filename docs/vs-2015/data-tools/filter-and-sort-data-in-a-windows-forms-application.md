---
title: 在 Windows Forms 應用程式中的篩選和排序資料 |Microsoft Docs
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 5592a488788c61af7ad6875de239fca62746857c
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58930574"
---
# <a name="filter-and-sort-data-in-a-windows-forms-application"></a>在 Windows Forms 應用程式中篩選和排序資料
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
設定篩選資料<xref:System.Windows.Forms.BindingSource.Filter%2A>屬性來傳回所要的記錄的字串運算式。  
  
 您藉由設定排序的資料<xref:System.Windows.Forms.BindingSource.Sort%2A>屬性的資料行名稱為您要用來排序，; 附加`DESC`依遞減順序排序，或是附加`ASC`若要以遞增順序排序。  
  
> [!NOTE]
>  如果您的應用程式不會使用<xref:System.Windows.Forms.BindingSource>元件，您可以篩選和排序資料，使用<xref:System.Data.DataView>物件。 如需詳細資訊，請參閱 < [Dataview](http://msdn.microsoft.com/library/0fe5dfa2-c1cd-435f-90b6-b4dd2e3ef34b)。  
  
## <a name="to-filter-data-by-using-a-bindingsource-component"></a>若要篩選資料，藉由使用 BindingSource 元件  
  
-   設定<xref:System.Windows.Forms.BindingSource.Filter%2A>屬性設為您想要傳回的運算式。 例如，下列程式碼會傳回客戶及`CompanyName`以"B"開頭的：  
  
     [!code-csharp[VbRaddataDisplaying#6](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/Form1.cs#6)]
     [!code-vb[VbRaddataDisplaying#6](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/Form1.vb#6)]  
  
## <a name="to-sort-data-by-using-a-bindingsource-component"></a>若要使用 BindingSource 元件排序資料  
  
-   設定<xref:System.Windows.Forms.BindingSource.Sort%2A>您想要排序的資料行的屬性。 例如，下列程式碼上排序客戶`CompanyName`資料行以遞減順序：  
  
     [!code-csharp[VbRaddataDisplaying#7](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/Form1.cs#7)]
     [!code-vb[VbRaddataDisplaying#7](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/Form1.vb#7)]  
  
## <a name="see-also"></a>另請參閱  
 [將控制項繫結至 Visual Studio 中的資料](../data-tools/bind-controls-to-data-in-visual-studio.md)
