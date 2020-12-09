---
title: 如何：將現有的 BDC 模型檔案新增至 SharePoint 專案 |Microsoft Docs
titleSuffix: ''
description: 將現有的商務資料連線 (BDC) 模型檔案新增至 Visual Studio 中的 SharePoint 專案，讓您可以自訂、封裝和重新部署 BDC 模型。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- VS.SharePointTools.BDC.ImportDialog
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], import a model
- Business Data Connectivity service [SharePoint development in Visual Studio], reuse a model
- BDC [SharePoint development in Visual Studio], import a model
- BDC [SharePoint development in Visual Studio], remove a model
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ce65f286c3de760ff74e5ef7239aac54d760f003
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/09/2020
ms.locfileid: "96914955"
---
# <a name="how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project"></a>如何：將現有的 BDC 模型檔案新增至 SharePoint 專案
  您可以使用 Visual Studio 將模型檔案 (*. .bdcm*) 加入至任何 SharePoint 伺服器陣列專案，以自訂、封裝和重新部署商務資料連線 (BDC) 模型。 如需詳細資訊，請參閱 [建立商務資料連線模型](../sharepoint/creating-a-business-data-connectivity-model.md)。

### <a name="to-add-a-bdc-model-file-to-a-sharepoint-project"></a>將 BDC 模型檔案新增至 SharePoint 專案

1. 在 **方案總管** 中，選擇 SharePoint 專案的資料夾。

2. 在功能表列上，選擇 [**專案**  >  **加入現有專案**]。

3. 在 [ **加入現有專案** ] 對話方塊中，流覽至您要加入至專案的模型定義檔位置，選擇該檔案，然後選擇 [ **加入** ] 按鈕。

    如果模型未定義企業營運 *(類型為 .net 元件的 LOB) 系統*，就會開啟 [ **新增 .net 元件 LobSystem** ] 對話方塊。

4. 如果出現對話方塊，請執行下列其中一個步驟：

   - 如果您想要撰寫自訂程式碼，並使用設計工具來定義匯入模型的中繼資料，請選擇 [ **是]** 按鈕、為系統命名，然後選擇 [ **確定]** 按鈕。

   - 否則，請選擇 [ **否** ] 按鈕，然後選擇 [ **確定]** 按鈕。

     **商務資料連線模型** 專案會加入至專案。

## <a name="see-also"></a>另請參閱
- [建立商務資料連線模型](../sharepoint/creating-a-business-data-connectivity-model.md)
- [如何：建立 BDC 模型](../sharepoint/how-to-create-a-bdc-model.md)
- [如何：使用資源檔來指定當地語系化的名稱、屬性和許可權](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)
- [如何：在 BDC 功能中包含自訂群組件](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)
- [將商務資料整合至 SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)
