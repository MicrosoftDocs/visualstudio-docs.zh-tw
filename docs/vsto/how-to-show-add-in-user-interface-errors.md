---
title: "如何： 顯示增益集使用者介面錯誤 |Microsoft 文件"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- add-ins [Office development in Visual Studio], user interface errors
- errors [Office development in Visual Studio], user interface errors
- user interfaces [Office development in Visual Studio], errors
- application-level add-ins [Office development in Visual Studio], user interface errors
ms.assetid: aa82cc04-e616-4501-940c-79d11fb393cc
caps.latest.revision: "27"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3b483889dbd970b2225c773e6dd43b9333b0d8a5
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-show-add-in-user-interface-errors"></a>如何：顯示增益集使用者介面錯誤
  根據預設，如果 VSTO 增益集嘗試處理 Microsoft Office 使用者介面 (UI) 時失敗，不會顯示任何錯誤訊息。 不過，您可以設定 Microsoft Office 應用程式，顯示與 UI 相關的錯誤訊息。 您可以使用這些訊息來協助判斷為何自訂功能區未出現，或為何出現了功能區但沒有出現任何控制項。  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
### <a name="to-show-vsto-add-in-user-interface-errors"></a>顯示 VSTO 增益集使用者介面錯誤  
  
1.  啟動應用程式。  
  
2.  按一下 [檔案]  索引標籤。  
  
3.  按一下 [選項] 。  
  
4.  在分類窗格中，按一下 [進階] 。  
  
5.  在詳細資料窗格中，選取 [顯示 VSTO 增益集使用者介面錯誤] ，然後按一下 [確定] 。  
  
    > [!NOTE]  
    >  對於 Outlook，[顯示 VSTO 增益集使用者介面錯誤]  核取方塊位於詳細資料窗格的 [開發人員]  區段。 對於其他應用程式，此核取方塊位於詳細資料窗格的 [一般]  區段。  
  
## <a name="see-also"></a>另請參閱  
 [Office UI 自訂](../vsto/office-ui-customization.md)   
 [建立 Outlook 表單區域](../vsto/creating-outlook-form-regions.md)   
 [功能區概觀](../vsto/ribbon-overview.md)   
 [執行窗格概觀](../vsto/actions-pane-overview.md)  
  
  