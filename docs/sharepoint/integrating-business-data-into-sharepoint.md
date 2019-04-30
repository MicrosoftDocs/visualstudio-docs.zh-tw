---
title: 將商務資料整合至 SharePoint |Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: fbbdba27b5ccc52e64575aad018af4ca20cf2e14
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63008767"
---
# <a name="integrate-business-data-into-sharepoint"></a>將商務資料整合到 SharePoint
  您可以將商務資料整合到 SharePoint。 商務資料可來自後端伺服器應用程式，例如[!INCLUDE[TLA#tla_sqlsvr](../sharepoint/includes/tlasharptla-sqlsvr-md.md)]、 Siebel 和 SAP、 或 Web 服務。 使用者可以檢視、 新增、 更新或刪除使用外部清單或在 SharePoint 中的商務資料 Web 組件的商務資料。  使用者也可以存取此資料離線的 Microsoft Office 應用程式，例如 Microsoft Outlook。 如需詳細資訊，請參閱 <<c0> [ 其中可以顯示外部資料的](http://go.microsoft.com/fwlink/?LinkId=169295)。

 若要將資料整合到 SharePoint 中，建立商務資料連接 (BDC) 服務的模型。 BDC 服務是在 SharePoint 中，將資料的相關資訊儲存在商務應用程式的應用程式。 如需詳細資訊，請參閱 <<c0> [ 商務資料連接 (BDC) 服務](http://go.microsoft.com/fwlink/?LinkID=169276)。

## <a name="models-in-visual-studio"></a>在 Visual Studio 中的模型
 在 Visual Studio 中的模型可讓您撰寫自訂程式碼來擷取和更新後端資料來源的資料。 您也可以從多個資料來源的彙總資料。 例如，您可以在其中顯示一份含有資料的客戶[!INCLUDE[ssNoVersion](../sharepoint/includes/ssnoversion-md.md)]資料庫和 Web 服務。

 您也可以匯入已部署到 SharePoint 的模型。 匯入模型之後，您可以加入自訂程式碼，或只使用封裝，然後將模型部署至多個 SharePoint 伺服器陣列的 Visual Studio。 如需詳細資訊，請參閱 <<c0> [ 建立 business data connectivity 模型](../sharepoint/creating-a-business-data-connectivity-model.md)。

## <a name="design-a-model-in-visual-studio"></a>設計 Visual Studio 中的模型
 您可以使用設計工具和數個工具視窗，來設計模型。 當您設計模型時，Visual Studio 會產生模型的 XML。 如需詳細資訊，請參閱 < [BDC 模型設計工具概觀](../sharepoint/bdc-model-design-tools-overview.md)。

 模型包含實體和方法。

### <a name="entities"></a>實體
 實體描述欄位的集合。 例如，實體可以代表資料庫中的資料表。 實體會顯示為在 SharePoint 中的外部內容類型。 如需外部內容類型的詳細資訊，請參閱[外部內容類型是什麼？](http://go.microsoft.com/fwlink/?LinkId=169293)

### <a name="methods"></a>方法
 方法可讓外部內容類型實體的欄位上執行動作的取用者。 比方說，更新者方法可能會讓使用者能夠變更位址，而生日的客戶所在`Address`並`BirthDate`是欄位的`Customer`實體。

 Visual Studio 會產生每個實體服務程式碼檔案，在您的模型。 當您將方法加入您的模型時，Visual Studio 會產生對應的方法中的服務程式碼檔案。 您可以將程式碼加入每個方法，以執行適當的工作。 比方說，如果您加入至模型的建立者方法，Visual Studio 會建立者方法設定您的服務程式碼檔中產生。 當使用者按一下 BDC 服務便會呼叫這個方法**新的項目**模型為基礎的清單中的按鈕。 因此，在將新資料加入至資料來源的建立者方法中加入程式碼。 如需詳細資訊，請參閱 <<c0> [ 設計 business data connectivity 模型](../sharepoint/designing-a-business-data-connectivity-model.md)。

## <a name="related-topics"></a>相關主題

|標題|描述|
|-----------|-----------------|
|[建立 business data connectivity 模型](../sharepoint/creating-a-business-data-connectivity-model.md)|示範如何建立新的模型，或匯入您從 SharePoint 匯出模型。|
|[設計商務資料連接模型](../sharepoint/designing-a-business-data-connectivity-model.md)|說明如何使用 Visual Studio 設計工具來設計模型的項目。|
|[使用 SharePoint Designer vs 的時機。使用 BCS 的 visual Studio 建置方案](http://go.microsoft.com/fwlink/?LinkID=183448)|可協助您決定是否要使用 Visual Studio，或使用 SharePoint Designer 建立 BDC 模型。|
