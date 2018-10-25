---
title: 建立 Business Data Connectivity 模型 |Microsoft Docs
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
- Business Data Connectivity service [SharePoint development in Visual Studio], model
- BDC [SharePoint development in Visual Studio], creating a model
- Business Data Connectivity service [SharePoint development in Visual Studio], creating a model
- SharePoint development in Visual Studio, Business Data Connectivity service
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 68940d6e48f1f3a3e51017e1cc838976735de104
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49930202"
---
# <a name="create-a-business-data-connectivity-model"></a>建立 business data connectivity 模型
  您可以建立商務資料連接 (BDC) 模型，或使用 Visual Studio 中自訂現有的 BDC 模型。 每個 SharePoint 專案可以包含一個模型。 如需詳細資訊，請參閱 <<c0> [ 將商務資料整合到 SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)。  
  
## <a name="create-a-new-model"></a>建立新的模型
 若要建立新的模型，建立**Business Data Connectivity 模型**專案，或新增**Business Data Connectivity 模型**項目**空白的 SharePoint 專案**。  
  
> [!NOTE]  
>  您必須擁有[!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)]安裝在您的電腦上。  
  
 Visual Studio 會將資料夾新增至專案。 此資料夾含有您指定的名稱**Business Data Connectivity 模型**中的項目**加入新項目** 對話方塊。 如果您建立新**Business Data Connectivity 模型**專案，Visual Studio 將資料夾命名**BdcModel1**。  
  
 Visual Studio 會將新的資料夾中的下列檔案：  
  
|檔案|描述|  
|----------|-----------------|  
|模型定義檔|包含定義實體、 方法、 企業營運 (LOB) 系統物件，以及其他描述模型的中繼資料的 XML。<br /><br /> 使用 BDC 設計工具中，修改這個檔案中的中繼資料**BDC 總管**， **BDC 方法詳細資料**視窗中，並**屬性**視窗。|  
|實體服務程式碼檔|包含擷取、 更新和刪除預設實體的執行個體的方法。|  
  
 若要定義實體的屬性，編輯實體的程式碼檔案。 如需詳細資訊，請參閱 <<c0> [ 如何： 將實體新增至模型](../sharepoint/how-to-add-an-entity-to-a-model.md)。  
  
 若要擷取、 更新和刪除實體的執行個體，加入實體服務程式碼檔案中的程式碼。 如需詳細資訊，請參閱 <<c0> [ 設計 business data connectivity 模型](../sharepoint/designing-a-business-data-connectivity-model.md)。  
  
 當您編譯專案時，Visual Studio 會建立組件。 請確定您執行程式碼加入專案的組件的專案新增其他項目 (例如：**循序工作流程**項目或有**Web 組件**項目)。 當您部署方案，因為方案套件不會複製到全域組件快取的組件時，不會執行該項目的程式碼。  方案套件部署至 SharePoint 中的 BDC 資料庫只的組件。  
  
> [!NOTE]  
>  Visual Studio 會將組件複製到本機電腦上的兩個位置中，當您偵錯專案。  
  
## <a name="add-an-existing-model"></a>新增現有的模型
 您可以匯入使用 SharePoint Designer 等其他工具所建立的模型。 您可以選擇現有模型匯入至您的專案，在下列情況：  
  
- 若要自訂已部署至 SharePoint 伺服器陣列的模型。  
  
- 若要封裝並將現有的模型部署到多個 SharePoint 伺服器陣列。  
  
  在任一情況下，您匯入模型中定義的 LOB 系統不會受到影響，並將繼續如預期般運作。 若要加入 SharePoint 專案中現有的模型，請使用 [Visual Studio**加入現有項目**] 對話方塊。 如需詳細資訊，請參閱 <<c0> [ 如何： 將現有的 BDC 模型檔案新增至 SharePoint 專案](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)。  
  
  您可以加入 LOB 系統的型別.NET Framework 組件匯入模型選取中的選項**新增.NET 組件 LobSystem**。 這可讓您撰寫自訂程式碼，並使用設計工具定義匯入模型中繼資料。  
  
## <a name="related-topics"></a>相關主題
  
|標題|描述|  
|-----------|-----------------|  
|[如何： 建立 BDC 模型](../sharepoint/how-to-create-a-bdc-model.md)|說明如何建立新的 BDC 模型。|  
|[如何： 將現有的 BDC 模型檔案新增至 SharePoint 專案](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)|說明如何將 SharePoint 專案匯入現有的模型。|  
|[如何： 使用資源檔來指定當地語系化的名稱、 屬性和權限](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)|說明如何當模型由 Web 組件或網頁，提供模型中繼資料會合併的字串。|  
|[如何： 在 BDC 功能中包含自訂組件](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)|說明如何在功能中包含自訂組件。|  
  
 
