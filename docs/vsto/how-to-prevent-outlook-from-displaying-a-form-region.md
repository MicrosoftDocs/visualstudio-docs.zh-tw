---
title: HOW TO：防止 Outlook 顯示表單區域
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- form regions [Office development in Visual Studio], canceling display
- canceling form region display
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ad17041650324e597fb76925f521bb7fc2e9ce93
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62967653"
---
# <a name="how-to-prevent-outlook-from-displaying-a-form-region"></a>HOW TO：防止 Outlook 顯示表單區域
  可能有不想要顯示特定項目的表單區域的 Microsoft Office Outlook 中的情況。 例如，如果連絡人項目沒有商務地址，您就可以防止表單區域，使其不出現對應中會顯示企業的位置。

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="to-prevent-outlook-from-displaying-a-form-region"></a>若要防止 Outlook 顯示表單區域

1. 開啟您想要修改表單區域的程式碼檔案。

2. 依序展開**表單區域 Factory**程式碼區域。

3. 將程式碼加入`FormRegionInitializing`設定的事件處理常式<xref:System.ComponentModel.CancelEventArgs.Cancel%2A>屬性<xref:Microsoft.Office.Tools.Outlook.FormRegionInitializingEventArgs>類別，即可**true**。

   在此範例中，如果連絡人項目不包含地址，<xref:System.ComponentModel.CancelEventArgs.Cancel%2A>屬性設定為 **，則為 true**，而未顯示表單區域。

## <a name="example"></a>範例
 [!code-csharp[Trin_Outlook_FR_Separate#1](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Separate_O12/MapIt.cs#1)]
 [!code-vb[Trin_Outlook_FR_Separate#1](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Separate_O12/MapIt.vb#1)]

## <a name="see-also"></a>另請參閱
- [建立 Outlook 表單區域](../vsto/creating-outlook-form-regions.md)
- [逐步解說：設計 Outlook 表單區域](../vsto/walkthrough-designing-an-outlook-form-region.md)
- [如何：將表單區域加入 Outlook 增益集專案](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)
- [逐步解說：設計 Outlook 表單區域](../vsto/walkthrough-designing-an-outlook-form-region.md)
- [逐步解說：匯入在 Outlook 中設計的表單區域](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)
