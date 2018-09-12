---
title: 如何： 顯示增益集使用者介面錯誤
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- add-ins [Office development in Visual Studio], user interface errors
- errors [Office development in Visual Studio], user interface errors
- user interfaces [Office development in Visual Studio], errors
- application-level add-ins [Office development in Visual Studio], user interface errors
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: dd6da0c83d0dee835169a0a8068af8d75facbbd4
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "35671370"
---
# <a name="how-to-show-add-in-user-interface-errors"></a>如何： 顯示增益集使用者介面錯誤
  根據預設，如果 VSTO 增益集嘗試處理的 Microsoft Office 使用者介面 (UI) 和失敗，就會不顯示任何錯誤訊息。 不過，您可以設定 Microsoft Office 應用程式，顯示與 UI 相關的錯誤訊息。 您可以使用這些訊息，以協助判斷為何自訂功能區未出現，或為何出現了功能區，但沒有出現任何控制項。  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
## <a name="to-show-vsto-add-in-user-interface-errors"></a>顯示 VSTO 增益集使用者介面錯誤  
  
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
  
  