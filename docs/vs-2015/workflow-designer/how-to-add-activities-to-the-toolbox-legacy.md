---
title: HOW TO：將活動新增至工具箱 （舊版） |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- Toolbox, adding activities
- activities, adding to Toolbox
ms.assetid: b66ea29c-120b-40ba-8a61-c1c8240850fa
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: c3a8c6f397bbafdbdb29ecbb193c4200a26335c3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62943354"
---
# <a name="how-to-add-activities-to-the-toolbox-legacy"></a>HOW TO：將活動新增至工具箱 (舊版)
建立舊版工作流程方案時[!INCLUDE[wfd1](../includes/wfd1-md.md)]目標[!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)]或[!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)]自訂活動可以加入至工作流程專案，其設計工具會置於**工具箱**的簡單存取權。 您也可以直接將活動新增**工具箱**從動態連結程式庫 (DLL)。  
  
### <a name="to-add-an-activity-to-the-toolbox-from-a-dll"></a>若要將活動從 DLL 新增至工具箱  
  
1. 以滑鼠右鍵按一下 [工具箱] 視窗介面底下**Windows 工作流程**，然後按一下**選擇項目**。  
  
2. 在 [**選擇工具箱項目**] 對話方塊中，按一下**System.Activities 元件**索引標籤，然後再按**瀏覽**從視窗的右下角。  
  
3. 從檔案目錄，包含要加入的自訂活動的實作中選取 DLL**工具箱**，然後按一下**開啟**。  
  
4. 按一下 **確定**完成將活動新增至工具箱。  
  
## <a name="see-also"></a>另請參閱  
 [使用舊版活動設計工具](../workflow-designer/using-the-legacy-activity-designer.md)   
 [舊版工作流程活動](../workflow-designer/legacy-workflow-activities.md)