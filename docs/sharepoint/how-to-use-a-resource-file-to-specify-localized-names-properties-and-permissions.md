---
title: 如何： 使用資源檔來指定當地語系化的名稱、 屬性和權限 |Microsoft 文件
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], localize strings
- BDC [SharePoint development in Visual Studio], localize strings
- BDC [SharePoint development in Visual Studio], resource file
- Business Data Connectivity service [SharePoint development in Visual Studio], resource strings
- BDC [SharePoint development in Visual Studio], properties
- Business Data Connectivity service [SharePoint development in Visual Studio], properties
- Business Data Connectivity service [SharePoint development in Visual Studio], resource file
- BDC [SharePoint development in Visual Studio], resource strings
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 58c8d74e29144a525eb33031fb98e25051d0305f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions"></a>如何：使用資源檔來指定當地語系化名稱、屬性和使用權限
  藉由使用資源檔，您可以提供當地語系化的名稱和定義屬性，或是對商務資料連接 (BDC) 模型中定義的物件套用權限。 若要指定這項資訊，您將加入**商務資料連接資源**要包含的專案項目**商務資料連接模型**項目。 然後編輯資源檔的 XML，藉此指定名稱、屬性和權限。  
  
### <a name="to-add-a-bdc-resource-file-to-a-sharepoint-project"></a>若要將 BDC 資源檔加入至 SharePoint 專案  
  
1.  在**方案總管 中**展開 SharePoint 專案的資料夾，然後選擇包含 BDC 模型的資料夾。  
  
2.  在功能表列上選擇 **專案**，**加入新項目**。  
  
3.  展開**SharePoint** ] 節點，然後選擇 [ **2010年**節點。  
  
4.  在**加入新項目**對話方塊方塊中，選擇**商務資料連接資源項目**。  
  
5.  在**名稱**方塊，並指定名稱的資源檔，然後選擇**新增** 按鈕。  
  
     副檔名為 .bdcr 的資源檔隨即加入至專案並開啟供編輯。  
  
6.  加入 XML 以定義您要套用 BDC 模型的當地語系化名稱、屬性以及權限。  
  
     如需如何定義這些項目資訊，請參閱[模型和資源檔](http://go.microsoft.com/fwlink/?LinkID=169283)。  
  
## <a name="see-also"></a>另請參閱  
 [如何： 將現有的 BDC 模型檔案加入至 SharePoint 專案](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)   
 [建立商務資料連接模型](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [如何： 建立 BDC 模型](../sharepoint/how-to-create-a-bdc-model.md)   
 [如何： 在 BDC 功能中包含自訂組件](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)   
 [將商業資料整合至 SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)  
  
  