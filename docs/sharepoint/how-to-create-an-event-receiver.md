---
title: "如何： 建立事件接收器 |Microsoft 文件"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.SharePointTools.SPE.EventReceiver
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, event receivers
- event receivers [SharePoint development in Visual Studio]
ms.assetid: 6f90cb48-eb8f-43c2-a3f7-ed4ce81aedf2
caps.latest.revision: "20"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 519c6907bb5779a3819419144905ca68e5cce939
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-an-event-receiver"></a>如何：建立事件接收器
  藉由建立*事件接收器*，您可以回應使用者互動 SharePoint 項目，例如清單或清單項目時。 比方說，當使用者變更行事曆，或刪除連絡人清單的名稱，會觸發的事件接收器中的程式碼。 您可以遵循本主題，來學習如何將事件接收器加入至清單執行個體。  
  
 若要完成這些步驟，您必須安裝[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]和支援的 Windows 版本和 SharePoint。 如需詳細資訊，請參閱[開發 SharePoint 方案的需求](../sharepoint/requirements-for-developing-sharepoint-solutions.md)。 因為這個範例需要 SharePoint 專案，您也必須先完成本主題中的程序[逐步解說： 建立網站資料行、 內容類型，以及 sharepoint 清單](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)。  
  
## <a name="adding-an-event-receiver"></a>加入事件接收器  
 您在建立專案[逐步解說： 建立 SharePoint 網站資料行、 內容類型和清單](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)包括自訂網站資料行、 自訂的清單，以及內容的類型。 在下列程序中，您會展開這個專案加入簡單的事件處理常式 （事件接收器） 來顯示如何處理 SharePoint 項目，例如清單中所發生事件的清單執行個體。  
  
#### <a name="to-add-an-event-receiver-to-the-list-instance"></a>加入事件接收器的清單執行個體  
  
1.  開啟您在建立專案[逐步解說： 建立網站資料行、 內容類型，以及 sharepoint 清單](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)。  
  
2.  在**方案總管 中**，選擇 SharePoint 專案節點，稱為**診所**。  
  
3.  在功能表列上選擇 **專案**，**加入新項目**。  
  
4.  之下**Visual C#**或**Visual Basic**，依序展開**SharePoint** ] 節點，然後選擇 [ **2010年**項目。  
  
5.  在**範本** 窗格中，選擇**事件接收器**，其命名**TestEventReceiver1**，然後選擇  **確定**  按鈕。  
  
     **SharePoint 自訂精靈**隨即出現。  
  
6.  在**您要何種類型的事件接收器？**清單中，選擇**清單項目事件**。  
  
7.  在**何種項目應該做為事件來源？**清單中，選擇**病患 (Clinic\Patients)**。  
  
8.  在**處理下列事件**清單中，選取核取方塊旁的 **項目已加入**，然後選擇 **完成** 按鈕。  
  
     新的事件接收器的程式碼檔包含的單一方法，名為`ItemAdded`。 在下一個步驟中，會將程式碼加入至這個方法，讓每個連絡人將會預設名稱為 Scott Brown。  
  
9. 取代現有`ItemAdded`方法，以下列程式碼，並再選擇 F5 鍵：  
  
     [!code-csharp[SP_EventReceiver#1](../sharepoint/codesnippet/CSharp/CustomField1/TestEventReceiver1/TestEventReceiver1.cs#1)]
     [!code-vb[SP_EventReceiver#1](../sharepoint/codesnippet/VisualBasic/CustomField1_VB/EventReceiver1/EventReceiver1.vb#1)]  
  
     在程式碼執行和 SharePoint 網站會出現在網頁瀏覽器。  
  
10. 在 快速啟動 列上選擇 **病患**連結，，然後選擇 **加入新項目**連結。  
  
     新的項目項目表單隨即開啟。  
  
11. 在欄位中，輸入資料，然後選擇**儲存** 按鈕。  
  
     選擇之後**儲存** 按鈕，**病患名稱**Scott Brown 的名稱會自動更新資料行。  
  
## <a name="see-also"></a>請參閱  
 [開發 SharePoint 方案](../sharepoint/developing-sharepoint-solutions.md)  
  
  