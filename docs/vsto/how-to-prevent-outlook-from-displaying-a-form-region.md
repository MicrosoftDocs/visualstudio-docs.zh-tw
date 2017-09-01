---
title: 'How to: Prevent Outlook from Displaying a Form Region | Microsoft Docs'
ms.custom: 
ms.date: 02/02/2017
ms.prod: visual-studio-dev14
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- form regions [Office development in Visual Studio], canceling display
- canceling form region display
ms.assetid: 82a25def-776a-476a-a72d-d0a48a827d3c
caps.latest.revision: 24
author: kempb
ms.author: kempb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: eb5c9550fd29b0e98bf63a7240737da4f13f3249
ms.openlocfilehash: e1b1d6af0009b071618cf2611f8198b04a64044b
ms.contentlocale: zh-tw
ms.lasthandoff: 08/30/2017

---
# <a name="how-to-prevent-outlook-from-displaying-a-form-region"></a>How to: Prevent Outlook from Displaying a Form Region
  There might be situations in which you do not want Microsoft Office Outlook to display a form region for a particular item. For example, if a contact item does not contain a business address, you can prevent a form region that shows the location of the business in a map from appearing.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
### <a name="to-prevent-outlook-from-displaying-a-form-region"></a>To prevent Outlook from displaying a form region  
  
1.  Open the code file for the form region you want to modify.  
  
2.  Expand the **Form Region Factory** code region.  
  
3.  Add code to the `FormRegionInitializing` event handler that sets the <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> property of the <xref:Microsoft.Office.Tools.Outlook.FormRegionInitializingEventArgs> class to **true**.  
  
 In this example, if the contact item does not contain an address, the <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> property is set to **true**, and the form region does not appear.  
  
## <a name="example"></a>Example  
 [!code-csharp[Trin_Outlook_FR_Separate#1](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Separate_O12/MapIt.cs#1)] [!code-vb[Trin_Outlook_FR_Separate#1](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Separate_O12/MapIt.vb#1)]  
  
## <a name="see-also"></a>See Also  
 [Creating Outlook Form Regions](../vsto/creating-outlook-form-regions.md)   
 [Walkthrough: Designing an Outlook Form Region](../vsto/walkthrough-designing-an-outlook-form-region.md)   
 [How to: Add a Form Region to an Outlook Add-in Project](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)   
 [Walkthrough: Designing an Outlook Form Region](../vsto/walkthrough-designing-an-outlook-form-region.md)   
 [Walkthrough: Importing a Form Region That Is Designed in Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)  
  
  
