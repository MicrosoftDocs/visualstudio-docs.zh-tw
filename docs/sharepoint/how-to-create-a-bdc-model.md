---
title: HOW TO：建立 BDC 模型 |Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], creating a model
- Business Data Connectivity service [SharePoint development in Visual Studio], creating a model
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 9126a0d3bb552f525247cbfb2243504a1effaa92
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63435477"
---
# <a name="how-to-create-a-bdc-model"></a>HOW TO：建立 BDC 模型
  您可以使用範本，為該類型的項目，並再將模型加入至任何 SharePoint 專案，以建立商務資料連接 (BDC) 模型。 如需詳細資訊，請參閱 <<c0> [ 建立 business data connectivity 模型](../sharepoint/creating-a-business-data-connectivity-model.md)。 如需如何設計模型的詳細資訊，請參閱[設計 business data connectivity 模型](../sharepoint/designing-a-business-data-connectivity-model.md)。

### <a name="to-create-a-bdc-project"></a>若要建立 BDC 專案

1. 在功能表列上，選擇 [檔案] > [新增] > [專案]。

    > [!NOTE]
    > 如果您的 IDE 設定為使用 Visual Basic 開發設定中，選擇**檔案** > **新專案**。

     [ **新增專案** ] 對話方塊隨即開啟。

2. 之下**Visual Basic**或是**Visual C#**，選擇  **Office/SharePoint**， **SharePoint 方案**。

3. 在 [**範本**] 窗格中，選擇**SharePoint 2013-空專案**項目，然後再選擇 [**確定**] 按鈕。

     **SharePoint 自訂精靈**隨即開啟。

4. 在 **指定偵錯的網站和安全性層級**頁面上，指定 SharePoint 網站的 URL，在本機電腦上，選擇**部署為伺服陣列方案**選項按鈕，然後再選擇  **完成** 按鈕。

     您將測試您指定的 SharePoint 網站上的模型。

    > [!IMPORTANT]
    > 您必須為陣列方案部署專案，因為 BDC 模型支援陣列方案。

     建立空白的 SharePoint 專案。

5. 在功能表列中，選擇 [專案] > [加入新項目]。

6. 在 **加入新項目**對話方塊方塊中，選擇**Office/SharePoint**節點。

7. 在 SharePoint 範本清單中，選擇**Business Data Connectivity 模型 （僅限陣列方案）**。

8. 在 [**名稱**中指定 BDC 模型的名稱，然後選擇**新增**] 按鈕。

     A **Business Data Connectivity 模型**項目加入至專案。 根據預設，模型會顯示在 BDC 設計工具中。 如需詳細資訊，請參閱 <<c0> [ 建立 business data connectivity 模型](../sharepoint/creating-a-business-data-connectivity-model.md)。

## <a name="see-also"></a>另請參閱
- [建立 business data connectivity 模型](../sharepoint/creating-a-business-data-connectivity-model.md)
- [如何：將現有的 BDC 模型檔案新增至 SharePoint 專案](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)
- [如何：使用資源檔來指定當地語系化的名稱、 屬性和權限](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)
- [如何：在 BDC 功能中包含自訂組件](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)
- [將商務資料整合至 SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)
