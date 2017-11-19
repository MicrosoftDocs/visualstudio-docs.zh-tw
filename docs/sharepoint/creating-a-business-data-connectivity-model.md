---
title: "建立商務資料連接模型 |Microsoft 文件"
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
- Business Data Connectivity service [SharePoint development in Visual Studio], model
- BDC [SharePoint development in Visual Studio], creating a model
- Business Data Connectivity service [SharePoint development in Visual Studio], creating a model
- SharePoint development in Visual Studio, Business Data Connectivity service
ms.assetid: 19fd12d0-a51a-4da4-98ac-918542e84507
caps.latest.revision: "24"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6661ca48321b1a19b5076beceb435e1f0c798ee0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="creating-a-business-data-connectivity-model"></a>建立商務資料連接模型
  您可以建立商務資料連線 (BDC) 模型，或使用 Visual Studio 中自訂現有的 BDC 模型。 每個 SharePoint 專案可以包含一個模型。 如需詳細資訊，請參閱[整合至 SharePoint 的商務資料](../sharepoint/integrating-business-data-into-sharepoint.md)。  
  
## <a name="creating-a-new-model"></a>建立新模型  
 若要建立新的模型，建立**商務資料連接模型**專案，或新增**商務資料連接模型**項目**空白的 SharePoint 專案**。  
  
> [!NOTE]  
>  您必須擁有[!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)]安裝在電腦上。  
  
 Visual Studio 會將資料夾加入專案。 此資料夾中沒有您指定的名稱**商務資料連接模型**中的項目**加入新項目** 對話方塊。 如果您建立新**商務資料連接模型**專案，Visual Studio 將資料夾命名為**BdcModel1**。  
  
 Visual Studio 會將下列檔案加入至新資料夾：  
  
|檔案|描述|  
|----------|-----------------|  
|模型定義檔案|包含定義實體、 方法、 企業營運 (LOB) 系統物件和其他描述模型的中繼資料的 XML。<br /><br /> 使用 BDC 設計工具中，修改此檔案的中繼資料**BDC 總管**， **BDC 方法詳細資料**視窗中，和**屬性**視窗。|  
|實體服務程式碼檔|包含方法，擷取、 更新和刪除預設實體的執行個體。|  
  
 若要定義實體的屬性，編輯 實體程式碼檔案。 如需詳細資訊，請參閱[How to： 將實體加入至模型](../sharepoint/how-to-add-an-entity-to-a-model.md)。  
  
 擷取、 更新和刪除實體的執行個體，將程式碼加入至實體服務程式碼檔。 如需詳細資訊，請參閱[設計商務資料連接模型](../sharepoint/designing-a-business-data-connectivity-model.md)。  
  
 當您編譯專案時，Visual Studio 建立組件。 請確定您不要將其他項目加入專案，將程式碼加入至專案的組件 (例如：**循序工作流程**項目或**Web 組件**項目)。 當您部署方案，因為方案套件不會複製到全域組件快取的組件時，不會執行該項目的程式碼。  方案套件會將組件部署到只會在 BDC 資料庫在 SharePoint 中。  
  
> [!NOTE]  
>  Visual Studio 偵錯專案時，將組件複製到本機電腦上的兩個位置。  
  
## <a name="adding-an-existing-model"></a>加入現有的模型  
 您可以匯入使用其他工具，例如 SharePoint Designer 所建立的模型。 您可能會選擇將現有模型匯入至您的專案，在下列情況：  
  
-   若要自訂已部署到 SharePoint 伺服器陣列的模型。  
  
-   封裝，然後將現有的模型部署到多個 SharePoint 伺服器陣列。  
  
 在任一情況下，您匯入模型中定義的 LOB 系統不會受到影響，而且將會繼續如預期般運作。 若要加入 SharePoint 專案中現有的模型，請使用 [Visual Studio**加入現有項目**] 對話方塊。 如需詳細資訊，請參閱[How to： 將現有的 BDC 模型檔案加入至 SharePoint 專案](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)。  
  
 您可以加入 LOB 系統的型別.NET Framework 組件匯入模型中的選項中選取**新增.NET 組件 LobSystem**。 這可讓您撰寫自訂程式碼，並使用設計工具定義匯入模型之中繼資料。  
  
## <a name="related-topics"></a>相關主題  
  
|標題|說明|  
|-----------|-----------------|  
|[如何：建立 BDC 模型](../sharepoint/how-to-create-a-bdc-model.md)|示範如何建立新的 BDC 模型。|  
|[如何：將現有的 BDC 模型檔案新增至 SharePoint 專案](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)|顯示如何將 SharePoint 專案匯入現有的模型。|  
|[如何：使用資源檔來指定當地語系化名稱、屬性和使用權限](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)|描述如何在當模型由 Web 組件或網頁提供模型中繼資料會合併的字串。|  
|[如何：在 BDC 功能中包含自訂組件](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)|示範如何在功能中包含自訂組件。|  
  
  