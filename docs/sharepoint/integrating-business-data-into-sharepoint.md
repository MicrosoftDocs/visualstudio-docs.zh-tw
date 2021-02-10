---
title: 將商務資料整合到 SharePoint 中 |Microsoft Docs
description: 閱讀有關如何藉由建立商務資料連線 (BDC) 服務的模型，來將商務資料整合至 SharePoint 的高階摘要。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: overview
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], business data
- BDC [SharePoint development in Visual Studio], aggregating data
- BDC [SharePoint development in Visual Studio], business data
- Business Data Connectivity service [SharePoint development in Visual Studio], aggregating data
- BDC [SharePoint development in Visual Studio], creating a model
- Business Data Connectivity service [SharePoint development in Visual Studio], creating a model
- Business Data Connectivity service [SharePoint development in Visual Studio], data
- BDC [SharePoint development in Visual Studio], data
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 94162e2fca66fd86b2ac8b237c518e391d0a9908
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99964676"
---
# <a name="integrate-business-data-into-sharepoint"></a>將商務資料整合至 SharePoint
  您可以將商務資料整合到 SharePoint。 商務資料可能來自後端伺服器應用程式，例如 [!INCLUDE[TLA#tla_sqlsvr](../sharepoint/includes/tlasharptla-sqlsvr-md.md)] 、Siebel、SAP 或 Web 服務。 使用者可以在 SharePoint 中使用外部清單或商務資料 Web 組件來查看、加入、更新或刪除商務資料。  使用者也可以在 Microsoft Office 的應用程式（例如 Microsoft Outlook）中離線存取此資料。 如需詳細資訊，請參閱 [哪裡可以顯示外部資料](/previous-versions/office/developer/sharepoint-2010/ee558737(v=office.14))。

 若要將資料整合到 SharePoint 中，請建立商務資料連線 (BDC) 服務的模型。 BDC 服務是 SharePoint 中的應用程式，可將資料的相關資訊儲存在商務應用程式中。 如需詳細資訊，請參閱 [ (BDC) Service 的商務資料連線](/previous-versions/office/developer/sharepoint-2010/ee556407(v=office.14))。

## <a name="models-in-visual-studio"></a>Visual Studio 中的模型
 Visual Studio 中的模型可讓您撰寫自訂程式碼，以從後端資料來源取出和更新資料。 您也可以匯總來自多個資料來源的資料。 例如，您可以顯示客戶清單，其中包含 [!INCLUDE[ssNoVersion](../sharepoint/includes/ssnoversion-md.md)] 資料庫和 Web 服務的資料。

 您也可以匯入已經部署到 SharePoint 的模型。 匯入模型之後，您可以加入自訂程式碼，或只使用 Visual Studio 將模型封裝並部署到多個 SharePoint 伺服器陣列。 如需詳細資訊，請參閱 [建立商務資料連線模型](../sharepoint/creating-a-business-data-connectivity-model.md)。

## <a name="design-a-model-in-visual-studio"></a>在 Visual Studio 中設計模型
 您可以使用設計工具和數個工具視窗來設計模型。 當您設計模型時，Visual Studio 會產生模型 XML。 如需詳細資訊，請參閱 [BDC 模型設計工具總覽](../sharepoint/bdc-model-design-tools-overview.md)。

 模型包含實體和方法。

### <a name="entities"></a>實體
 實體會描述欄位的集合。 例如，實體可以代表資料庫中的資料表。 實體會顯示為 SharePoint 中的外部內容類型。 如需外部內容類型的詳細資訊，請參閱 [什麼是外部內容類型？](/previous-versions/office/developer/sharepoint-2010/ee556391(v=office.14))

### <a name="methods"></a>方法
 方法可讓外部內容類型的取用者在實體的欄位上執行動作。 例如，更新程式方法可讓使用者變更客戶的位址和出生日期，以及 `Address` `BirthDate` 實體的欄位 `Customer` 。

 Visual Studio 會針對模型中的每個實體產生服務程式代碼檔案。 當您將方法加入至模型時，Visual Studio 會在服務程式代碼檔案中產生對應的方法。 將程式碼加入至每個方法，以執行適當的工作。 例如，如果您將建立者方法加入至模型，Visual Studio 會在您的服務程式代碼檔案中產生建立者方法。 當使用者按一下以模型為基礎之清單中的 [ **新增專案** ] 按鈕時，BDC 服務會呼叫這個方法。 因此，將程式碼加入至將新資料新增至資料來源的建立者方法。 如需詳細資訊，請參閱 [設計商務資料連線模型](../sharepoint/designing-a-business-data-connectivity-model.md)。

## <a name="related-topics"></a>相關主題

|標題|描述|
|-----------|-----------------|
|[建立商務資料連線模型](../sharepoint/creating-a-business-data-connectivity-model.md)|說明如何建立新的模型，或匯入您從 SharePoint 匯出的模型。|
|[設計商務資料連線模型](../sharepoint/designing-a-business-data-connectivity-model.md)|說明如何使用 Visual Studio 的設計工具來設計模型的元素。|
|[使用 BCS 建立方案時，使用 SharePoint Designer 與 Visual Studio 的時機](/previous-versions/office/developer/sharepoint-2010/ee558875(v=office.14))|協助您決定是否要使用 Visual Studio，或使用 SharePoint Designer 建立 BDC 的模型。|
