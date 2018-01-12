---
title: "將商業資料整合至 SharePoint |Microsoft 文件"
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
- Business Data Connectivity service [SharePoint development in Visual Studio], business data
- BDC [SharePoint development in Visual Studio], aggregating data
- BDC [SharePoint development in Visual Studio], business data
- Business Data Connectivity service [SharePoint development in Visual Studio], aggregating data
- BDC [SharePoint development in Visual Studio], creating a model
- Business Data Connectivity service [SharePoint development in Visual Studio], creating a model
- Business Data Connectivity service [SharePoint development in Visual Studio], data
- BDC [SharePoint development in Visual Studio], data
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: c054049c09f13c224ee4f0bb3021af1121f5cea8
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/10/2018
---
# <a name="integrating-business-data-into-sharepoint"></a>將商業資料整合至 SharePoint
  您可以將商業資料整合至 SharePoint。 商務資料可以來自後端伺服器應用程式，例如[!INCLUDE[TLA#tla_sqlsvr](../sharepoint/includes/tlasharptla-sqlsvr-md.md)]、 Siebel 和 SAP，或 Web 服務。 使用者可以檢視、 新增、 更新或刪除外部清單或商務資料 Web 組件在 SharePoint 中使用的商務資料。  使用者也可以存取此資料離線的 Microsoft Office 應用程式，例如 Microsoft Outlook。 如需詳細資訊，請參閱[其中可以您顯示外部資料](http://go.microsoft.com/fwlink/?LinkId=169295)。  
  
 若要將資料整合到 SharePoint 中，建立商務資料連線 (BDC) 服務的型號。 BDC 服務是在 SharePoint 中，將資料的相關資訊儲存在商務應用程式的應用程式。 如需詳細資訊，請參閱[商務資料連線 (BDC) 服務](http://go.microsoft.com/fwlink/?LinkID=169276)。  
  
## <a name="models-in-visual-studio"></a>在 Visual Studio 中的模型  
 在 Visual Studio 中的模型可讓您撰寫自訂程式碼來擷取和更新後端資料來源的資料。 您也可以從多個資料來源的彙總資料。 例如，您可以顯示一份含有資料的客戶[!INCLUDE[ssNoVersion](../sharepoint/includes/ssnoversion-md.md)]資料庫和 Web 服務。  
  
 您也可以匯入已部署至 SharePoint 的模型。 匯入模型之後，您可以加入自訂程式碼，或只使用 Visual Studio 來封裝及部署至多個 SharePoint 伺服器陣列的模型。 如需詳細資訊，請參閱[建立商務資料連接模型](../sharepoint/creating-a-business-data-connectivity-model.md)。  
  
## <a name="designing-a-model-in-visual-studio"></a>設計 Visual Studio 中的模型  
 您可以使用設計工具和數個工具視窗來設計模型。 當您設計模型時，Visual Studio 會產生模型 XML。 如需詳細資訊，請參閱[BDC 模型設計工具概觀](../sharepoint/bdc-model-design-tools-overview.md)。  
  
 模型包含實體和方法。  
  
### <a name="entities"></a>實體  
 實體描述欄位的集合。 例如，實體可以代表資料庫中的資料表。 實體會顯示為在 SharePoint 外部內容類型。 如需有關外部內容類型的詳細資訊，請參閱[外部內容類型為何？](http://go.microsoft.com/fwlink/?LinkId=169293)  
  
### <a name="methods"></a>方法  
 方法可讓取用者要實體欄位上執行動作的外部內容類型。 比方說，Updater 方法可能會讓使用者變更位址，並出生日期的客戶位置`Address`和`BirthDate`是欄位的`Customer`實體。  
  
 Visual Studio 會產生您的模型中的每個實體服務程式碼檔案。 當您將方法加入您的模型時，Visual Studio 會產生對應的方法中的服務程式碼檔案。 將程式碼加入至每個方法，以執行適當的工作。 比方說，如果您將建立者方法加入至模型，Visual Studio 會在您的服務程式碼檔中產生建立者方法。 當使用者按一下 BDC 服務便會呼叫這個方法**新項目**模型為基礎的清單中的按鈕。 因此，在將新資料加入至資料來源的建立者方法中加入程式碼。 如需詳細資訊，請參閱[設計商務資料連接模型](../sharepoint/designing-a-business-data-connectivity-model.md)。  
  
## <a name="related-topics"></a>相關主題  
  
|標題|描述|  
|-----------|-----------------|  
|[建立商務資料連接模型](../sharepoint/creating-a-business-data-connectivity-model.md)|示範如何建立新的模型，或匯入您從 SharePoint 匯出模型。|  
|[設計商務資料連接模型](../sharepoint/designing-a-business-data-connectivity-model.md)|說明如何使用 Visual Studio 設計工具設計的模型項目。|  
|[使用 SharePoint Designer vs 的時機。使用 BCS 的 visual Studio 時，建置解決方案](http://go.microsoft.com/fwlink/?LinkID=183448)|可協助您決定是否要使用 Visual Studio 或使用 SharePoint Designer 建立 BDC 模型。|  
  
  