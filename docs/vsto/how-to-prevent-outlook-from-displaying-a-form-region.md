---
title: 如何：防止 Outlook 顯示表單區域
description: 瞭解如何防止 Microsoft Office Outlook 顯示特定專案的表單區域。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- form regions [Office development in Visual Studio], canceling display
- canceling form region display
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 1dc9322dd2ad3c3a2111222d7491f9e1a82cd6c4
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825845"
---
# <a name="how-to-prevent-outlook-from-displaying-a-form-region"></a>如何：防止 Outlook 顯示表單區域
  在某些情況下，您可能不想 Microsoft Office Outlook 顯示特定專案的表單區域。 例如，如果連絡人項目不包含商務位址，您可以防止在地圖中顯示企業位置的表單區域出現。

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="to-prevent-outlook-from-displaying-a-form-region"></a>防止 Outlook 顯示表單區域

1. 開啟您想要修改之表單區域的程式碼檔案。

2. 展開 **表單區域 Factory** 程式碼區域。

3. 將程式碼加入至 `FormRegionInitializing` 事件處理常式，將 <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> 類別的屬性設定 <xref:Microsoft.Office.Tools.Outlook.FormRegionInitializingEventArgs> 為 **true**。

   在此範例中，如果連絡人項目不包含位址， <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> 屬性會設定為 **true**，而且不會顯示表單區域。

## <a name="example"></a>範例
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Outlook_FR_Separate_O12/MapIt.cs" id="Snippet1":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Separate_O12/MapIt.vb" id="Snippet1":::


## <a name="see-also"></a>另請參閱
- [建立 Outlook 表單區域](../vsto/creating-outlook-form-regions.md)
- [逐步解說：設計 Outlook 表單區域](../vsto/walkthrough-designing-an-outlook-form-region.md)
- [如何：在 Outlook 增益集專案中加入表單區域](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)
- [逐步解說：設計 Outlook 表單區域](../vsto/walkthrough-designing-an-outlook-form-region.md)
- [逐步解說：匯入在 Outlook 中設計的表單區域](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)
