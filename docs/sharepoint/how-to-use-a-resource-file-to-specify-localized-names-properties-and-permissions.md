---
title: 如何：使用資源檔來指定當地語系化名稱、屬性和許可權 |Microsoft Docs
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a87cc8a3eb8f98ea19a87e93c37aae5303151ecf
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: zh-TW
ms.lasthandoff: 07/06/2020
ms.locfileid: "86015404"
---
# <a name="how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions"></a>如何：使用資源檔來指定當地語系化名稱、屬性和許可權
  藉由使用資源檔，您可以提供當地語系化的名稱和定義屬性，或是對商務資料連接 (BDC) 模型中定義的物件套用權限。 若要指定這項資訊，您可以將**商務資料連線資源**專案加入至包含**商務資料連線模型**專案的專案。 然後編輯資源檔的 XML，藉此指定名稱、屬性和權限。

### <a name="to-add-a-bdc-resource-file-to-a-sharepoint-project"></a>若要將 BDC 資源檔加入至 SharePoint 專案

1. 在**方案總管**中，展開 SharePoint 專案的資料夾，然後選擇包含 BDC 模型的資料夾。

2. 在功能表列上，選擇 [**專案**] [  >  **加入新專案**]。

3. 展開 [ **SharePoint** ] 節點，然後選擇 [ **2010** ] 節點。

4. 在 [**加入新專案**] 對話方塊中，選擇 [**商務資料連線資源專案**]。

5. 在 [**名稱**] 方塊中，指定資源檔的名稱，然後選擇 [**新增**] 按鈕。

     副檔名為 .bdcr 的資源檔隨即加入至專案並開啟供編輯。

6. 加入 XML 以定義您要套用 BDC 模型的當地語系化名稱、屬性以及權限。

     如需如何定義這些元素的詳細資訊，請參閱[模型和資源檔](/previous-versions/office/developer/sharepoint-2010/aa674515(v=office.14))。

## <a name="see-also"></a>另請參閱
- [如何：將現有的 BDC 模型檔案加入至 SharePoint 專案](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)
- [建立商務資料連線模型](../sharepoint/creating-a-business-data-connectivity-model.md)
- [如何：建立 BDC 模型](../sharepoint/how-to-create-a-bdc-model.md)
- [如何：在 BDC 功能中包含自訂群組件](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)
- [將商務資料整合至 SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)
