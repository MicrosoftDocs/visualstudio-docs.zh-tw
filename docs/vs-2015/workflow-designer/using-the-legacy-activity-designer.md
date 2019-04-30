---
title: 使用舊版活動設計工具 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- activities, configuring
- custom activities
- Activity Designer
- child activities, adding
- activities, adding child
- activities, creating custom
ms.assetid: 2fea8a05-6e58-423d-94bf-a822b15ffb80
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 5755c6a3b4ece5b40c7799d83bdf33966d5c2b3e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62855768"
---
# <a name="using-the-legacy-activity-designer"></a>使用舊版活動設計工具
本主題描述如何在舊版 [!INCLUDE[wfd1](../includes/wfd1-md.md)] 中使用活動設計工具。 當以 [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] 或 [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] 為目標時，請使用舊版設計工具。  
  
 活動設計工具可讓您建立自訂活動。  
  
## <a name="creating-a-custom-activity"></a>建立自訂活動  
 依照下列步驟使用活動設計工具建立自訂活動：  
  
1. 在 **專案**功能表上，按一下**新增活動**。  
  
2. 選取 **活動**或是**活動 （程式碼分開置放）** 範本。  
  
   1. 使用**活動**範本來建立活動的活動定義和使用者程式碼，在相同的程式碼檔案。  
  
   2. 使用**活動 （程式碼分開置放）** 範本來建立活動的活動定義表示成工作流程標記和不同的程式碼檔案中的使用者程式碼。  
  
3. 輸入活動名稱或保留預設名稱，然後按一下**新增**。  
  
   您也可以藉由建立新專案的型別建立一組自訂活動**Workflow Activity Library**。 如需有關此專案類型的詳細資訊，請參閱[How to:建立工作流程活動程式庫 （舊版）](../workflow-designer/how-to-create-a-workflow-activity-library-legacy.md)。  
  
## <a name="configuring-an-activity"></a>設定活動  
 活動設計工具為使用中時，可使用屬性瀏覽器設定下表所列的屬性。  
  
|屬性|註解|  
|--------------|--------------|  
|**名稱**|活動名稱。|  
|**基底類別**|衍生活動的基底類別。 預設的基底類別[SequenceActivity](http://go.microsoft.com/fwlink?LinkID=65020)。 在 [**屬性**] 視窗中，按一下**基底類別**省略符號 **[...]** 以選取中的另一個基底類別[瀏覽並選取.NET 類型對話方塊 （舊版）](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box-legacy.md)。|  
|**描述**|使用者定義的活動描述。|  
|**已啟用**|設定為 **，則為 True**預設為啟用活動執行和驗證。 設定為**False**停用活動執行和驗證。 如需活動執行和驗證資訊，請參閱[開發工作流程活動](http://go.microsoft.com/fwlink?LinkID=65024)。|  
  
## <a name="adding-child-activities"></a>新增子活動  
 您可以將子活動從 [工具箱] 拖曳至您正在設計的活動。 接著，便可以使用屬性瀏覽器設定每一個子活動。  
  
## <a name="see-also"></a>另請參閱  
 [開發工作流程活動](http://go.microsoft.com/fwlink?LinkID=65024)   
 [建立自訂活動](http://go.microsoft.com/fwlink?LinkID=65021)   
 [舊版工作流程活動](../workflow-designer/legacy-workflow-activities.md)   
 [自訂活動範例](http://go.microsoft.com/fwlink?LinkID=65022)   
 [如何：建立工作流程活動程式庫 （舊版）](../workflow-designer/how-to-create-a-workflow-activity-library-legacy.md)   
 [使用舊版工作流程設計工具](../workflow-designer/using-the-legacy-workflow-designer.md)