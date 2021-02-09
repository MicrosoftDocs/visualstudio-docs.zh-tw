---
title: 如何：建立 BDC 模型 |Microsoft Docs
description: 使用適用于該專案類型的 Visual Studio 範本，然後將模型加入至任何 SharePoint 專案，以 (BDC) 模型建立商務資料連線。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], creating a model
- Business Data Connectivity service [SharePoint development in Visual Studio], creating a model
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 77ffd8b6cd913b79249862a875b6267848a131af
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99923363"
---
# <a name="how-to-create-a-bdc-model"></a>如何：建立 BDC 模型
  您可以使用該專案類型的範本，然後將模型加入至任何 SharePoint 專案，來建立 (BDC) 模型的商務資料連線。 如需詳細資訊，請參閱 [建立商務資料連線模型](../sharepoint/creating-a-business-data-connectivity-model.md)。 如需如何設計模型的詳細資訊，請參閱 [設計商務資料連線模型](../sharepoint/designing-a-business-data-connectivity-model.md)。

### <a name="to-create-a-bdc-project"></a>建立 BDC 專案

1. 在功能表列上 **，選擇 [** 檔案  >  **新增**  >  **專案**]。

    > [!NOTE]
    > 如果您的 IDE 設定為使用 Visual Basic 開發設定，請 **選擇 [** 檔案  >  **新增專案**]。

     此時會開啟 [新增專案] 對話方塊。

2. 在 **Visual Basic** 或 **Visual c #** 下，選擇 [ **Office/Sharepoint**]、[ **sharepoint 方案**]。

3. 在 [ **範本** ] 窗格中，選擇 [ **SharePoint 2013-空白] 專案** 專案，然後選擇 [ **確定]** 按鈕。

     [ **SharePoint 自訂嚮導]** 隨即開啟。

4. 在 [ **指定要進行偵錯工具的網站和安全性層級** ] 頁面上，指定本機電腦上 SharePoint 網站的 URL，選擇 [ **部署為伺服器陣列方案** ] 選項按鈕，然後選擇 [ **完成]** 按鈕。

     您將在您指定的 SharePoint 網站上測試模型。

    > [!IMPORTANT]
    > 您必須將專案部署為伺服器陣列方案，因為 BDC 模型只支援伺服器陣列方案。

     系統會建立空白的 SharePoint 專案。

5. 在功能表列上，選擇 [ **Project**  >  **加入新專案**]。

6. 在 [ **加入新專案** ] 對話方塊中，選擇 [ **Office/SharePoint** ] 節點。

7. 在 SharePoint 範本清單中，選擇 [ **商務資料連線模型 (伺服器陣列方案])**。

8. 在 [ **名稱** ] 方塊中，指定 BDC 模型的名稱，然後選擇 [ **加入** ] 按鈕。

     **商務資料連線模型** 專案會加入至專案。 依預設，此模型會顯示在 BDC 設計工具中。 如需詳細資訊，請參閱 [建立商務資料連線模型](../sharepoint/creating-a-business-data-connectivity-model.md)。

## <a name="see-also"></a>另請參閱
- [建立商務資料連線模型](../sharepoint/creating-a-business-data-connectivity-model.md)
- [如何：將現有的 BDC 模型檔案新增至 SharePoint 專案](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)
- [如何：使用資源檔來指定當地語系化的名稱、屬性和許可權](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)
- [如何：在 BDC 功能中包含自訂群組件](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)
- [將商務資料整合至 SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)
