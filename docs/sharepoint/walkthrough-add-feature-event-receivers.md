---
title: "逐步解說： 新增功能事件接收器 |Microsoft 文件"
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
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, advanced packaging tools
- SharePoint development in Visual Studio, event receivers
- SharePoint development in Visual Studio, feature event receivers
ms.assetid: fbd44c33-2c27-4d57-abca-21cddc16fbc3
caps.latest.revision: "24"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 27d565a51c026a6e143e18f122039d90627f55ff
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-add-feature-event-receivers"></a>逐步解說：新增功能事件接收器
  功能事件接收器是在 SharePoint 中其中一個的下列功能相關的事件發生時執行的方法：  
  
-   功能的安裝。  
  
-   啟動功能。  
  
-   一項功能會停用。  
  
-   已移除的功能。  
  
 本逐步解說示範如何將事件接收器加入至 SharePoint 專案中的功能。 它會示範下列工作：  
  
-   正在建立功能事件接收器的空專案。  
  
-   處理**FeatureDeactivating**方法。  
  
-   使用 SharePoint 專案物件模型將宣告新增至宣告清單。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>必要條件  
 您需要下列元件才能完成此逐步解說：  
  
-   支援的 Microsoft Windows 和 SharePoint 版本。 如需詳細資訊，請參閱[開發 SharePoint 方案的需求](../sharepoint/requirements-for-developing-sharepoint-solutions.md)。  
  
-   Visual Studio。  
  
## <a name="creating-a-feature-event-receiver-project"></a>建立功能事件接收器專案  
 首先，建立專案以包含功能事件接收器。  
  
#### <a name="to-create-a-project-with-a-feature-event-receiver"></a>若要建立專案，而功能事件接收器  
  
1.  在功能表列上選擇 [**檔案**，**新增**，**專案**顯示**新專案**] 對話方塊。  
  
2.  展開**SharePoint**節點之下**Visual C#**或**Visual Basic**，然後選擇  **2010年**節點。  
  
3.  在**範本** 窗格中，選擇**SharePoint 2010 專案**範本。  
  
     因為它們沒有專案範本，您可以使用適用於功能事件接收器的這種專案類型。  
  
4.  在**名稱**方塊中，輸入**FeatureEvtTest**，然後選擇 [**確定**] 按鈕以顯示**SharePoint 自訂精靈**。  
  
5.  在**指定偵錯的網站和安全性層級**頁面上，輸入您要加入新的自訂欄位項目，在 SharePoint 伺服器網站的 URL，或使用預設位置 (http://\<*系統名稱*> /)。  
  
6.  在**此 SharePoint 方案的信任層級為何？**區段中，選擇**部署為伺服陣列方案**選項按鈕。  
  
     如需有關沙箱化方案和伺服器陣列方案的詳細資訊，請參閱[沙箱化方案考量](../sharepoint/sandboxed-solution-considerations.md)。  
  
7.  選擇**完成**按鈕，並請注意，名為 Feature1 一項功能會出現下**功能**節點。  
  
## <a name="adding-an-event-receiver-to-the-feature"></a>將事件接收器加入至功能  
 接下來，將事件接收器加入至功能，並加入功能停用時執行的程式碼。  
  
#### <a name="to-add-an-event-receiver-to-the-feature"></a>若要將事件接收器加入至功能  
  
1.  開啟 [功能] 節點的捷徑功能表，然後選擇**加入功能**建立功能。  
  
2.  在下**功能**] 節點，開啟捷徑功能表**Feature1**，然後選擇 [**加入事件接收器**新增功能事件接收器。  
  
     這樣會加入 Feature1 底下的程式碼檔案。 在此情況下，它稱為 Feature1.EventReceiver.cs 或 Feature1.EventReceiver.vb，視您的專案開發語言而定。  
  
3.  如果您的專案以撰寫[!INCLUDE[csprcs](../sharepoint/includes/csprcs-md.md)]，事件接收器的最上方加入下列程式碼，如果它已經不存在：  
  
     [!code-csharp[SP_FeatureEvt#1](../sharepoint/codesnippet/CSharp/featureevttest2/features/feature1/feature1.eventreceiver.cs#1)]  
  
4.  事件接收器類別中包含數個標記為註解方法做為事件。 取代**FeatureDeactivating**以下列方法：  
  
     [!code-vb[SP_FeatureEvt#2](../sharepoint/codesnippet/VisualBasic/featureevt2vb/features/feature1/feature1.eventreceiver.vb#2)]
     [!code-csharp[SP_FeatureEvt#2](../sharepoint/codesnippet/CSharp/featureevttest2/features/feature1/feature1.eventreceiver.cs#2)]  
  
## <a name="testing-the-feature-event-receiver"></a>測試功能事件接收器  
 接下來，停用此功能來測試是否**FeatureDeactivating**方法輸出至 SharePoint 的公告清單公告。  
  
#### <a name="to-test-the-feature-event-receiver"></a>若要測試功能事件接收器  
  
1.  設定專案的值**現用部署組態**屬性**無啟用**。  
  
     設定這個屬性可防止在 SharePoint 中啟用的功能，並讓您偵錯功能事件接收器。 如需詳細資訊，請參閱[偵錯 SharePoint 方案](../sharepoint/debugging-sharepoint-solutions.md)。  
  
2.  選擇**F5**執行專案，並將它部署至 SharePoint 的索引鍵。  
  
3.  在 SharePoint 網頁的頂端，開啟**網站動作**功能表，然後選擇 **站台設定**。  
  
4.  在下**網站動作**區段**站台設定**頁面上，選擇**管理網站功能**連結。  
  
5.  在**功能**頁面上，選擇**Activate**旁邊**FeatureEvtTest Feature1**功能。  
  
6.  在**功能**頁面上，選擇**停用**旁邊**FeatureEvtTest Feature1**功能，然後選擇 **停用這項功能**確認連結可停用此功能。  
  
7.  選擇**首頁** 按鈕。  
  
     請注意，宣告會出現在**公告**清單之後停用此功能。  
  
## <a name="see-also"></a>另請參閱  
 [如何： 建立事件接收器](../sharepoint/how-to-create-an-event-receiver.md)   
 [開發 SharePoint 方案](../sharepoint/developing-sharepoint-solutions.md)  
  
  