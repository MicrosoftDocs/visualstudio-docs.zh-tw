---
title: "如何： 將現有的 BDC 模型檔案加入至 SharePoint 專案 |Microsoft 文件"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.SharePointTools.BDC.ImportDialog
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], import a model
- Business Data Connectivity service [SharePoint development in Visual Studio], reuse a model
- BDC [SharePoint development in Visual Studio], import a model
- BDC [SharePoint development in Visual Studio], remove a model
ms.assetid: e843738a-f936-4dcd-be35-249407573b74
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 64a32115aa7810352148a61e3dd0faeebb0ee9a1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project"></a>如何：將現有的 BDC 模型檔案加入至 SharePoint 專案
  您可以自訂封裝，及使用 Visual Studio 將模型檔案 (.bdcm) 新增至任何 SharePoint 伺服器陣列的專案重新部署商務資料連線 (BDC) 模型。 如需詳細資訊，請參閱[建立商務資料連接模型](../sharepoint/creating-a-business-data-connectivity-model.md)。  
  
### <a name="to-add-a-bdc-model-file-to-a-sharepoint-project"></a>若要加入的 BDC 模型檔案至 SharePoint 專案  
  
1.  在**方案總管 中**，選擇 SharePoint 專案的資料夾。  
  
2.  在功能表列上選擇 **專案**，**加入現有項目**。  
  
3.  在**加入現有項目**對話方塊中，瀏覽至您想要新增至您的專案，選擇 檔案，然後選擇的模型定義檔的位置**新增** 按鈕。  
  
     如果未定義模型*類型的.NET 組件的企業營運 (LOB) 系統*、**新增.NET 組件 LobSystem**對話方塊隨即開啟。  
  
4.  如果出現對話方塊，請執行下列步驟：  
  
    -   如果您想要撰寫自訂程式碼，並使用設計工具定義匯入模型之中繼資料，請選擇**是**按鈕並命名系統，然後選擇 [**確定**] 按鈕。  
  
    -   否則，請選擇**否**按鈕，然後再選擇**確定** 按鈕。  
  
     **商務資料連接模型**項目加入至專案。  
  
## <a name="see-also"></a>請參閱  
 [建立商務資料連接模型](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [如何： 建立 BDC 模型](../sharepoint/how-to-create-a-bdc-model.md)   
 [如何： 使用資源檔來指定當地語系化的名稱、 屬性和權限](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)   
 [如何： 在 BDC 功能中包含自訂組件](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)   
 [將商業資料整合至 SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)  
  
  