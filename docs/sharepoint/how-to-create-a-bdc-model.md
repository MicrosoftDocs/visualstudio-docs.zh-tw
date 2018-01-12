---
title: "如何： 建立 BDC 模型 |Microsoft 文件"
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
- BDC [SharePoint development in Visual Studio], creating a model
- Business Data Connectivity service [SharePoint development in Visual Studio], creating a model
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 6b4e01a61ac3802edc2dc6e5f6ab3680d39e7704
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-create-a-bdc-model"></a>如何：建立 BDC 模型
  您可以使用為該類型的項目範本，然後將模型加入至任何 SharePoint 專案中建立的商務資料連線 (BDC) 模型。 如需詳細資訊，請參閱[建立商務資料連接模型](../sharepoint/creating-a-business-data-connectivity-model.md)。 如需如何設計模型的詳細資訊，請參閱[設計商務資料連接模型](../sharepoint/designing-a-business-data-connectivity-model.md)。  
  
### <a name="to-create-a-bdc-project"></a>若要建立 BDC 專案  
  
1.  在功能表列上，選擇 [檔案] 、[新增] 、[專案] 。  
  
    > [!NOTE]  
    >  如果您的 IDE 設定為使用 Visual Basic 開發設定，請選擇**檔案**，**新專案**。  
  
     [ **新增專案** ] 對話方塊隨即開啟。  
  
2.  之下**Visual Basic**或**Visual C#**，選擇**Office/SharePoint**， **SharePoint 方案**。  
  
3.  在**範本** 窗格中，選擇**SharePoint 2013-空專案**項目，然後再選擇**確定** 按鈕。  
  
     **SharePoint 自訂精靈**隨即開啟。  
  
4.  在**指定偵錯的網站和安全性層級**頁面上，指定 SharePoint 網站的 URL，在本機電腦上，選擇**部署為伺服陣列方案**選項按鈕，然後再選擇 [ **完成**] 按鈕。  
  
     您將測試您指定之 SharePoint 網站上的模型。  
  
    > [!IMPORTANT]  
    >  因為 BDC 模型支援僅伺服器陣列方案，您必須在專案部署為陣列方案。  
  
     建立空的 SharePoint 專案。  
  
5.  在功能表列上選擇 **專案**，**加入新項目**。  
  
6.  在**加入新項目**對話方塊方塊中，選擇**Office/SharePoint**節點。  
  
7.  在 SharePoint 範本清單中選擇**商務資料連接模型 （僅限陣列方案）**。  
  
8.  在**名稱**方塊，並指定 BDC 模型名稱，然後選擇**新增** 按鈕。  
  
     A**商務資料連接模型**項目加入至專案。 根據預設，模型會出現在 BDC 設計工具。 如需詳細資訊，請參閱[建立商務資料連接模型](../sharepoint/creating-a-business-data-connectivity-model.md)。  
  
## <a name="see-also"></a>請參閱  
 [建立商務資料連接模型](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [如何： 將現有的 BDC 模型檔案加入至 SharePoint 專案](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)   
 [如何： 使用資源檔來指定當地語系化的名稱、 屬性和權限](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)   
 [如何： 在 BDC 功能中包含自訂組件](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)   
 [將商業資料整合至 SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)  
  
  