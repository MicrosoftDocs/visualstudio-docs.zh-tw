---
title: 逐步解說：新增功能事件接收器 |Microsoft Docs
description: 在這個逐步解說中，新增功能事件接收器，也就是在安裝、啟動、停用或移除 SharePoint 功能時所執行的方法。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, advanced packaging tools
- SharePoint development in Visual Studio, event receivers
- SharePoint development in Visual Studio, feature event receivers
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 98b85222fca4da6dfca653ad74e1315801798d83
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/09/2020
ms.locfileid: "96915592"
---
# <a name="walkthrough-add-feature-event-receivers"></a>逐步解說：新增功能事件接收器
功能事件接收器是在 SharePoint 中發生下列其中一個功能相關事件時所執行的方法：

- 已安裝功能。

- 功能已啟用。

- 停用功能。

- 已移除功能。

本逐步解說示範如何將事件接收器加入至 SharePoint 專案中的功能。 它會示範下列工作：

- 使用功能事件接收器建立空白專案。

- 處理 **FeatureDeactivating** 方法。

- 使用 SharePoint 專案物件模型，將宣告加入至公告清單中。

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>必要條件
 您需要下列元件才能完成這個逐步解說：

- 支援的 Microsoft Windows 和 SharePoint 版本。

- Visual Studio。

## <a name="create-a-feature-event-receiver-project"></a>建立功能事件接收器專案
 首先，建立專案以包含功能事件接收器。

#### <a name="to-create-a-project-with-a-feature-event-receiver"></a>若要建立具有功能事件接收器的專案

1. 在功能表列上 **，選擇 [** 檔案  >  **新增**  >  **專案**]，以顯示 [**新增專案**] 對話方塊。

2. 展開 [ **Visual c #** ] 或 [ **Visual Basic**] 底下的 [ **SharePoint** ] 節點，然後選擇 [ **2010** ] 節點。

3. 在 [ **範本** ] 窗格中，選擇 [ **SharePoint 2010] 專案** 範本。

     您可以將此專案類型用於功能事件接收器，因為它們沒有專案範本。

4. 在 [ **名稱** ] 方塊中，輸入 **FeatureEvtTest**，然後選擇 [ **確定]** 按鈕以顯示 [ **SharePoint 自訂] Wizard**。

5. 在 [ **指定偵錯工具的網站和安全性等級** ] 頁面上，輸入您要加入新自訂欄位專案之 SharePoint 伺服器網站的 URL，或使用預設位置 (HTTP:// \<*system name*> /) 。

6. 在 [ **此 SharePoint 方案的信任層級為何？** ] 區段中，選擇 [ **部署為伺服器陣列方案** ] 選項按鈕。

     如需有關沙箱化方案與伺服器陣列方案的詳細資訊，請參閱 [沙箱化解決方案考慮](../sharepoint/sandboxed-solution-considerations.md)。

7. 選擇 [ **完成]** 按鈕，然後注意到名為 Feature1 的功能會出現在 [ **功能** ] 節點底下。

## <a name="add-an-event-receiver-to-the-feature"></a>將事件接收器新增至功能
 接下來，將事件接收器新增至功能，並加入停用功能時所執行的程式碼。

#### <a name="to-add-an-event-receiver-to-the-feature"></a>將事件接收器新增至功能

1. 開啟 [功能] 節點的快捷方式功能表，然後選擇 [ **加入功能** ] 來建立功能。

2. 在 [ **功能** ] 節點下，開啟 [ **Feature1**] 的快捷方式功能表，然後選擇 [ **加入事件接收器** ]，將事件接收器加入至功能。

     這會在 Feature1 底下加入程式碼檔案。 在此情況下，會根據您專案的開發語言，將它命名為 *Feature1.EventReceiver.cs* 或 *Feature1。*

3. 如果您的專案是以撰寫的 [!INCLUDE[csprcs](../sharepoint/includes/csprcs-md.md)] ，請在事件接收器的頂端新增下列程式碼（如果它還不存在）：

     [!code-csharp[SP_FeatureEvt#1](../sharepoint/codesnippet/CSharp/featureevttest2/features/feature1/feature1.eventreceiver.cs#1)]

4. 事件接收器類別包含數個以批註形式處理的方法，這些方法會當做事件。 以下列內容取代 **FeatureDeactivating** 方法：

     [!code-vb[SP_FeatureEvt#2](../sharepoint/codesnippet/VisualBasic/featureevt2vb/features/feature1/feature1.eventreceiver.vb#2)]
     [!code-csharp[SP_FeatureEvt#2](../sharepoint/codesnippet/CSharp/featureevttest2/features/feature1/feature1.eventreceiver.cs#2)]

## <a name="test-the-feature-event-receiver"></a>測試功能事件接收器
 接下來，停用此功能，測試 **FeatureDeactivating** 方法是否會將公告輸出到 SharePoint 公告清單。

#### <a name="to-test-the-feature-event-receiver"></a>測試功能事件接收器

1. 將專案的 [作用中 **部署** 設定] 屬性值設定為 [ **無啟用**]。

     設定此屬性可防止在 SharePoint 中啟用此功能，並可讓您進行功能事件接收器的調試。 如需詳細資訊，請參閱 [Debug SharePoint 方案](../sharepoint/debugging-sharepoint-solutions.md)。

2. 選擇 **F5** 鍵以執行專案，並將其部署到 SharePoint。

3. 在 SharePoint 網頁頂端，開啟 [ **網站動作** ] 功能表，然後選擇 [ **網站設定**]。

4. 在 [**網站設定**] 頁面的 [**網站動作**] 區段下，選擇 [**管理網站功能**] 連結。

5. 在 [**功能**] 頁面上，選擇 [ **FeatureEvtTest Feature1** ] 功能旁的 [**啟用**] 按鈕。

6. 在 [**功能**] 頁面上，選擇 [ **FeatureEvtTest Feature1** ] 功能旁的 [**停用**] 按鈕，然後選擇 [**停用此功能** 確認] 連結以停用此功能。

7. 選擇 [ **首頁** ] 按鈕。

     請注意，在停用此功能 **之後，公告清單中** 會出現公告。

## <a name="see-also"></a>另請參閱

- [如何：建立事件接收器](../sharepoint/how-to-create-an-event-receiver.md)
- [開發 SharePoint 方案](../sharepoint/developing-sharepoint-solutions.md)