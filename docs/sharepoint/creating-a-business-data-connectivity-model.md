---
title: 建立商務資料連線模型 |Microsoft Docs
description: 使用 Visual Studio 建立 (BDC) 模型或自訂現有 BDC 模型的商務資料連線。 每個 SharePoint 專案只能包含一個模型。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], model
- BDC [SharePoint development in Visual Studio], creating a model
- Business Data Connectivity service [SharePoint development in Visual Studio], creating a model
- SharePoint development in Visual Studio, Business Data Connectivity service
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 8232847ce336ca559134aa1211a70057a1306faa
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99949255"
---
# <a name="create-a-business-data-connectivity-model"></a>建立商務資料連線模型
  您可以 (BDC) 模型建立商務資料連線，或使用 Visual Studio 自訂現有的 BDC 模型。 每個 SharePoint 專案只能包含一個模型。 如需詳細資訊，請參閱將 [商務資料整合到 SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)。

## <a name="create-a-new-model"></a>建立新模型
 若要建立新的模型，請建立 **商務資料連線模型** 專案，或將 **商務資料連線模型** 專案加入至 **空白的 SharePoint 專案**。

> [!NOTE]
> 您必須已 [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] 在電腦上安裝。

 Visual Studio 將資料夾新增至專案。 這個資料夾的名稱是您在 [**加入新專案**] 對話方塊中為 [**商務資料連線模型**] 專案指定的名稱。 如果您建立新的 **商務資料連線模型** 專案，Visual Studio 將資料夾命名為 **BdcModel1**。

 Visual Studio 將下列檔案新增至新的資料夾：

|檔案|描述|
|----------|-----------------|
|模型定義檔|包含定義實體、方法、企業營運 (LOB) 系統物件和其他描述模型之中繼資料的 XML。<br /><br /> 使用 [bdc 設計工具]、[bdc **Explorer**]、[ **Bdc 方法詳細資料** ] 視窗和 [ **屬性** ] 視窗，修改這個檔案中的中繼資料。|
|Entity Service 程式碼檔案|包含抓取、更新及刪除預設實體之實例的方法。|

 若要定義實體的屬性，請編輯實體程式碼檔案。 如需詳細資訊，請參閱 [如何：將實體加入至模型](../sharepoint/how-to-add-an-entity-to-a-model.md)。

 若要取出、更新和刪除實體的實例，請將程式碼加入至 entity service 程式碼檔案。 如需詳細資訊，請參閱 [設計商務資料連線模型](../sharepoint/designing-a-business-data-connectivity-model.md)。

 當您編譯專案時，Visual Studio 會建立元件。 確定您不會將其他專案新增至專案，以將程式碼加入專案元件 (例如： **連續工作流程** 專案或) 的 **Web 元件** 專案。 當您部署方案時，該專案的程式碼將不會執行，因為方案套件不會將元件複製到全域組件快取。  方案套件只會將元件部署至 SharePoint 中的 BDC 資料庫。

> [!NOTE]
> 當您在偵錯工具時，Visual Studio 會將元件複製到本機電腦上的兩個位置。

## <a name="add-an-existing-model"></a>加入現有的模型
 您可以匯入使用其他工具（例如 SharePoint Designer）所建立的模型。 在下列情況下，您可以選擇將現有的模型匯入至專案：

- 自訂已部署到 SharePoint 伺服器陣列的模型。

- 將現有的模型封裝和部署到多個 SharePoint 伺服器陣列。

  無論是哪一種情況，您匯入模型中所定義的 LOB 系統都不會受到影響，並將繼續如預期般運作。 若要將現有的模型加入至 SharePoint 專案，請使用 [ **加入現有專案** ] Visual Studio 對話方塊。 如需詳細資訊，請參閱 [如何：將現有的 BDC 模型檔案新增至 SharePoint 專案](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)。

  您可以選取 [ **新增 .net 元件 LobSystem**] 中的選項，將類型 .NET Framework 元件的 LOB 系統加入至匯入的模型。 這可讓您撰寫自訂程式碼，並使用設計工具來定義匯入模型的中繼資料。

## <a name="related-topics"></a>相關主題

|標題|描述|
|-----------|-----------------|
|[如何：建立 BDC 模型](../sharepoint/how-to-create-a-bdc-model.md)|說明如何建立新的 BDC 模型。|
|[如何：將現有的 BDC 模型檔案新增至 SharePoint 專案](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)|示範如何將現有的模型匯入到 SharePoint 專案。|
|[如何：使用資源檔來指定當地語系化的名稱、屬性和許可權](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)|描述如何提供當 Web 元件或網頁取用模型時，與模型中繼資料合併的字串。|
|[如何：在 BDC 功能中包含自訂群組件](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)|說明如何在功能中包含自訂群組件。|
