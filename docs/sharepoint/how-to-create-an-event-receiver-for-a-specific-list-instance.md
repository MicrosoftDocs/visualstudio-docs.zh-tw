---
title: 如何： 建立事件接收器的特定清單執行個體 |Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, event receivers
- event receivers [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 950eeec82d7b7c49f0bbd76b13114f80f023a6dd
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/29/2018
ms.locfileid: "37118628"
---
# <a name="how-to-create-an-event-receiver-for-a-specific-list-instance"></a>如何： 建立事件接收器的特定清單執行個體
  清單定義的任何執行個體中發生的事件回應的清單執行個體事件接收器。 雖然事件接收者範本不會啟用特定的清單執行個體的目標，您可以修改事件接收器來回應特定的清單執行個體中的事件清單定義範圍內。  
  
 中要鎖定特定的清單執行個體*Elements.xml*的事件接收器中，取代`ListTemplateId`使用`ListUrl`及新增清單執行個體的 URL。  
  
## <a name="create-a-list-instance-event-receiver"></a>建立清單執行個體事件接收器  
 下列步驟示範如何修改為只回應中的自訂宣告清單執行個體所發生事件的清單項目事件接收器。  
  
#### <a name="to-modify-an-event-receiver-to-respond-to-a-specific-list-instance"></a>若要修改事件接收器來回應特定的清單執行個體  
  
1.  在瀏覽器中開啟 SharePoint 網站。  
  
2.  在 [導覽] 窗格中，**列出**連結。  
  
3.  在 **所有網站內容**頁面上，選擇**建立**連結。  
  
4.  在**建立**對話方塊方塊中，選擇**宣布**類型，將公告命名**TestAnnouncements**，然後選擇 [**建立**] 按鈕。  
  
5.  在  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]，建立事件接收器專案。  
  
6.  在 **何種類型的事件接收器？** 清單中，選擇**清單項目事件**。  
  
    > [!NOTE]  
    >  您也可以選取任何其他類型的清單定義，例如，範圍的事件接收器**列出的電子郵件事件**或是**清單工作流程事件**。  
  
7.  在 **何種項目應該做為事件來源？** 清單中，選擇**公告**。  
  
8.  在 [**處理下列事件**清單中，選取**正在加入項目**核取方塊，，然後選擇**完成**] 按鈕。  
  
9. 在 **方案總管**下 EventReceiver1，, 開啟*Elements.xml*。  
  
     事件接收器目前是使用下列程式碼行參考 [公告] 清單定義：  
  
    ```xml  
    <Receivers ListTemplateId="104">  
    ```  
  
     請將這行變更為以下文字：  
  
    ```xml  
    <Receivers ListUrl="Lists/TestAnnouncements">  
    ```  
  
     這會指示回應只發生在新的事件的事件接收器**TestAnnouncements**您剛才建立的宣告清單。 您可以變更`ListURL`參考任何清單執行個體，在 SharePoint 伺服器上的屬性。  
  
10. 開啟事件接收器程式碼檔案，並將中斷點放在 ItemAdding 方法。  
  
11. 選擇**F5**鍵，建置並執行方案。  
  
12. 在 SharePoint 中，選擇**TestAnnouncements**瀏覽窗格中的連結。  
  
13. 選擇**加入新公告**連結。  
  
14. 以了解宣告中，輸入標題，然後選擇**儲存** 按鈕。  
  
     請注意新的項目新增至自訂的公告清單時叫用中斷點。  
  
15. 選擇**F5**鍵繼續。  
  
16. 在 [導覽] 窗格中，選擇**列出**連結，然後再選擇**公告**連結。  
  
17. 加入新的公告。  
  
     請注意，事件接收器將不會在新的公告因為接收者已設定為只回應中的自訂的公告清單執行個體中，事件才會觸發**TestAnnouncements**。  
  
## <a name="see-also"></a>另請參閱
 [如何： 建立事件接收器](../sharepoint/how-to-create-an-event-receiver.md)   
 [開發 SharePoint 方案](../sharepoint/developing-sharepoint-solutions.md)  
  
