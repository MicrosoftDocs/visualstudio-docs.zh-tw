---
title: 如何： 防止 Outlook 顯示表單區域 |Microsoft 文件
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- form regions [Office development in Visual Studio], canceling display
- canceling form region display
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: a5fffde6cd92d490df2a5567763da77e723ed4f3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-prevent-outlook-from-displaying-a-form-region"></a>如何：防止 Outlook 顯示表單區域
  可能會有不想要顯示特定項目的表單區域的 Microsoft Office Outlook 中的情況。 例如，如果連絡人項目沒有商務地址，您可以防止顯示企業的位置，在地圖中出現的表單區域。  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
### <a name="to-prevent-outlook-from-displaying-a-form-region"></a>若要避免 Outlook 顯示表單區域  
  
1.  開啟您想要修改表單區域的程式碼檔案。  
  
2.  展開**表單區域 Factory**程式碼區域。  
  
3.  將程式碼加入`FormRegionInitializing`設定的事件處理常式<xref:System.ComponentModel.CancelEventArgs.Cancel%2A>屬性<xref:Microsoft.Office.Tools.Outlook.FormRegionInitializingEventArgs>類別**true**。  
  
 在此範例中，如果連絡人項目不包含地址，<xref:System.ComponentModel.CancelEventArgs.Cancel%2A>屬性設定為**true**，而且沒有出現在表單區域。  
  
## <a name="example"></a>範例  
 [!code-csharp[Trin_Outlook_FR_Separate#1](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Separate_O12/MapIt.cs#1)]
 [!code-vb[Trin_Outlook_FR_Separate#1](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Separate_O12/MapIt.vb#1)]  
  
## <a name="see-also"></a>另請參閱  
 [建立 Outlook 表單區域](../vsto/creating-outlook-form-regions.md)   
 [逐步解說： 設計 Outlook 表單區域](../vsto/walkthrough-designing-an-outlook-form-region.md)   
 [如何： 在 Outlook 增益集專案中加入表單區域](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)   
 [逐步解說： 設計 Outlook 表單區域](../vsto/walkthrough-designing-an-outlook-form-region.md)   
 [逐步解說：匯入在 Outlook 中設計的表單區域](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)  
  
  