---
title: "擴充 SharePoint 專案系統 |Microsoft 文件"
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
helpviewer_keywords:
- SharePoint development in Visual Studio, extending projects
- SharePoint development in Visual Studio, extending project items
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: e79808ef9d5d4712d67426b202046615c8ab14b2
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/10/2018
---
# <a name="extending-the-sharepoint-project-system"></a>擴充 SharePoint 專案系統
  您可以使用 Visual Studio 中的一組專案範本和項目範本來建立 SharePoint 方案。 這些範本符合需求的許多開發案例，但您可能會發現某些情況下，它們不在其中提供您所需要的功能。 在這些情況下，您可以擴充 SharePoint 專案系統。  
  
## <a name="overview-of-the-sharepoint-project-system"></a>SharePoint 專案系統的概觀  
 SharePoint 專案系統為基礎的基本元件*SharePoint 專案項目*。 SharePoint 專案項目代表單一 SharePoint 自訂，例如清單定義、 Web 組件或內容類型。  
  
 SharePoint 專案是 Visual Studio 專案包含一個或多個 SharePoint 專案項目。 SharePoint 專案也包含可定義如何將專案項目分組的功能和封裝部署到其他元件。  
  
 SharePoint 專案項目和 SharePoint 專案的內容的相關資訊，請參閱[建立項目範本和專案範本，為 SharePoint 專案項目](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)。  
  
## <a name="how-to-extend-the-sharepoint-project-system"></a>如何擴充 SharePoint 專案系統  
 您可以下列方式來擴充 SharePoint 專案系統：  
  
-   定義您自己的 SharePoint 專案項目類型，並將其與新的項目範本] 或 [Visual Studio 中的專案範本關聯。 例如，您可以建立自訂動作或欄位定義 SharePoint 專案項目類型。 如需詳細資訊，請參閱[定義自訂 SharePoint 專案項目類型](../sharepoint/defining-custom-sharepoint-project-item-types.md)。  
  
-   擴充已安裝 Visual Studio 中的 SharePoint 專案項目類型。 例如，將快顯功能表項目加入專案項目中**方案總管 中**和自訂專案項目，當開發人員選擇功能表項目。 如需詳細資訊，請參閱[擴充 SharePoint 專案項目](../sharepoint/extending-sharepoint-project-items.md)。  
  
-   擴充 SharePoint 專案。 例如，您可以加入事件處理常式，加入或移除 SharePoint 專案項目時，執行特定工作。 如需詳細資訊，請參閱[擴充 SharePoint 專案](../sharepoint/extending-sharepoint-projects.md)。  
  
-   擴充 SharePoint 專案項目和 SharePoint 專案的封裝和部署行為。 例如，您可以建立您自己的部署步驟，或在您部署或撤銷專案時，Visual Studio 執行特定的部署步驟時，您可以執行額外的自訂工作時執行。 如需詳細資訊，請參閱[擴充 SharePoint 封裝和部署](../sharepoint/extending-sharepoint-packaging-and-deployment.md)。  
  
## <a name="common-development-tasks"></a>常見的開發工作  
 擴充 SharePoint 專案系統中，您可以執行下列的一般工作：  
  
-   專案項目並在多種不同類型的專案檔中儲存自訂字串資料。 如需詳細資訊，請參閱[擴充 SharePoint 專案系統中儲存的資料](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)。  
  
-   SharePoint 專案系統中的 Visual Studio 自動化物件模型或整合物件模型中，對應的物件中轉換物件，反之亦然。 如需詳細資訊，請參閱[轉換之間 SharePoint 專案系統類型與其他 Visual Studio 專案類型](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)。  
  
## <a name="see-also"></a>請參閱  
 [定義自訂 SharePoint 專案項目類型](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [擴充 SharePoint 專案項目](../sharepoint/extending-sharepoint-project-items.md)   
 [擴充 SharePoint 專案](../sharepoint/extending-sharepoint-projects.md)   
 [擴充 SharePoint 封裝和部署](../sharepoint/extending-sharepoint-packaging-and-deployment.md)   
 [擴充 SharePoint 專案系統中儲存資料](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)   
 [SharePoint 專案系統類型與其他 Visual Studio 專案類型之間轉換](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)   
 [擴充 Visual Studio 中的 SharePoint 工具](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)   
 [SharePoint 工具延伸模組的程式設計概念和功能](../sharepoint/programming-concepts-and-features-for-sharepoint-tools-extensions.md)  
  
  