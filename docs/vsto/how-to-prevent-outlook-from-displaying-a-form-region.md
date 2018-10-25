---
title: 如何： 防止 Outlook 顯示表單區域
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
ms.openlocfilehash: 1ec9f45b2055a7a56e067440d216482877da14c2
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49949054"
---
# <a name="how-to-prevent-outlook-from-displaying-a-form-region"></a>如何： 防止 Outlook 顯示表單區域
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
 [建立 Outlook 表單區域](../vsto/creating-outlook-form-regions.md)   
 [逐步解說： 設計 Outlook 表單區域](../vsto/walkthrough-designing-an-outlook-form-region.md)   
 [如何： 在 Outlook 增益集專案中加入表單區域](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)   
 [逐步解說： 設計 Outlook 表單區域](../vsto/walkthrough-designing-an-outlook-form-region.md)   
 [逐步解說： 匯入在 Outlook 中設計表單區域](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)  
  
  