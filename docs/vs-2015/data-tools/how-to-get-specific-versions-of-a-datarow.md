---
title: 如何： 取得特定版本 DataRow |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- row states
- updating datasets, row states
- DataRow object
ms.assetid: d7cde25e-cef5-4559-b994-be00e258ac1f
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: ed409bdafaa15052a7190480a7cbc46ac766de84
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47486741"
---
# <a name="how-to-get-specific-versions-of-a-datarow"></a>如何：取得特定版本 DataRow
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

資料集將資料列變更時，會保留原始 (<xref:System.Data.DataRowVersion>) 和新 (<xref:System.Data.DataRowVersion>) 的資料列版本。 比方說，之前呼叫`AcceptChanges`方法中，您的應用程式可以存取記錄的不同版本 (如中所定義<xref:System.Data.DataRowVersion>列舉型別) 並據以處理變更。  
  
> [!NOTE]
>  不同版本的資料列存在，僅有經編輯後再`AcceptChanges`呼叫的方法。 之後`AcceptChanges`已呼叫方法、 目前和原始的版本都相同。  
  
 傳遞<xref:System.Data.DataRowVersion>值資料行索引 （或資料行名稱做為字串） 以及傳回該資料行的特定資料列版本的值。 已變更的資料行識別期間<xref:System.Data.DataTable.ColumnChanging>和<xref:System.Data.DataTable.ColumnChanged>事件，這是要檢查不同的好時機資料列進行驗證的版本。 不過，如果您已暫時停用條件約束，就不會引發這些事件，您必須以程式設計方式識別哪些資料行已變更。 您可以逐一查看<xref:System.Data.DataTable.Columns%2A>集合，並比較不同<xref:System.Data.DataRowVersion>值。  
  
## <a name="accessing-the-original-version-of-a-datarow"></a>存取 DataRow 的原始版本  
  
#### <a name="to-get-the-original-version-of-a-record"></a>若要取得一筆資料錄的原始版本  
  
-   存取傳入的資料行的值<xref:System.Data.DataRowVersion>您想要傳回的資料列。  
  
     下列範例示範如何使用<xref:System.Data.DataRowVersion>若要取得的原始值的值`CompanyName`欄位中<xref:System.Data.DataRow>:  
  
     [!code-csharp[VbRaddataEditing#21](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#21)]
     [!code-vb[VbRaddataEditing#21](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#21)]  
  
## <a name="accessing-the-current-version-of-a-datarow"></a>存取目前版本的 DataRow  
  
#### <a name="to-get-the-current-version-of-a-record"></a>若要取得目前的版本記錄的  
  
-   存取資料行的值，並將參數加入的索引，表示您想要傳回的資料列版本。  
  
     下列範例示範如何使用<xref:System.Data.DataRowVersion>若要取得的目前值的值`CompanyName`欄位中<xref:System.Data.DataRow>:  
  
     [!code-csharp[VbRaddataEditing#22](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#22)]
     [!code-vb[VbRaddataEditing#22](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#22)]  
  
## <a name="see-also"></a>另請參閱  
 [在您的應用程式中編輯資料](../data-tools/editing-data-in-your-application.md)   
 [驗證資料](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [儲存資料](../data-tools/saving-data.md)   
 [資料逐步解說](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)   
 [將 Windows Forms 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [在 Visual Studio 中的資料應用程式的概觀](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [連接到 Visual Studio 中的資料](../data-tools/connecting-to-data-in-visual-studio.md)   
 [準備您的應用程式接收資料](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [將資料擷取至您的應用程式](../data-tools/fetching-data-into-your-application.md)   
 [將控制項繫結至 Visual Studio 中的資料](../data-tools/bind-controls-to-data-in-visual-studio.md)