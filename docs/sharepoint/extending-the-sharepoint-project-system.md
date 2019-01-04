---
title: 擴充 SharePoint 專案系統 |Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, extending projects
- SharePoint development in Visual Studio, extending project items
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 51449003457ecd09e7dca7bc579d652c94a592e2
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53891108"
---
# <a name="extend-the-sharepoint-project-system"></a>擴充 SharePoint 專案系統
  您可以使用 Visual Studio 中的一組專案範本和項目範本來建立 SharePoint 方案。 這些範本符合許多的開發案例的需求，但您可能會發現某些情況下，它們不在此提供您所需要的功能。 在這些情況下，您可以擴充 SharePoint 專案系統。  
  
## <a name="overview-of-the-sharepoint-project-system"></a>SharePoint 專案系統的概觀
 SharePoint 專案系統為基礎的基本元件*SharePoint 專案項目*。 SharePoint 專案項目代表單一 SharePoint 自訂，例如清單定義、 網頁組件或內容類型。  
  
 SharePoint 專案是 Visual Studio 專案，其中包含一或多個 SharePoint 專案項目。 SharePoint 專案也包含定義如何將專案項目分組到功能及部署套件的其他元件。  
  
 如需詳細的 SharePoint 專案項目與 SharePoint 專案內容的相關資訊，請參閱[建立項目範本和專案範本，為 SharePoint 專案項目](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)。  
  
## <a name="how-to-extend-the-sharepoint-project-system"></a>如何擴充 SharePoint 專案系統
 您可以透過下列方式來擴充 SharePoint 專案系統：  
  
-   定義您自己的 SharePoint 專案項目類型，並將其與新的項目範本或 Visual Studio 中的專案範本關聯。 例如，您可以定義 SharePoint 專案項目類型來建立自訂動作或欄位。 如需詳細資訊，請參閱 <<c0> [ 定義自訂 SharePoint 專案項目類型](../sharepoint/defining-custom-sharepoint-project-item-types.md)。  
  
-   擴充已安裝 Visual Studio 中的 SharePoint 專案項目類型。 例如，您可以讓快顯功能表項目加入專案項目中**方案總管 中**和自訂專案項目，當開發人員選擇功能表項目。 如需詳細資訊，請參閱 <<c0> [ 擴充 SharePoint 專案項目](../sharepoint/extending-sharepoint-project-items.md)。  
  
-   擴充 SharePoint 專案。 例如，您可以新增事件處理常式，加入或移除 SharePoint 專案項目時，執行特定工作。 如需詳細資訊，請參閱 <<c0> [ 擴充 SharePoint 專案](../sharepoint/extending-sharepoint-projects.md)。  
  
-   擴充 SharePoint 專案項目與 SharePoint 專案的封裝和部署行為。 例如，您可以建立自己的部署步驟，或在您部署或撤銷的專案，Visual Studio 執行特定的部署步驟時，您可以執行額外的自訂工作時執行。 如需詳細資訊，請參閱 <<c0> [ 擴充 SharePoint 封裝和部署](../sharepoint/extending-sharepoint-packaging-and-deployment.md)。  
  
## <a name="common-development-tasks"></a>一般開發工作
 擴充功能的 SharePoint 專案系統中，您可以執行下列常見工作：  
  
-   專案項目與許多不同類型的專案檔中，將儲存自訂的字串資料。 如需詳細資訊，請參閱 <<c0> [ 將資料儲存於 SharePoint 專案系統擴充](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)。  
  
-   SharePoint 專案系統中的 Visual Studio 自動化物件模型或整合物件模型中，對應的物件中轉換物件，反之亦然。 如需詳細資訊，請參閱 <<c0> [ 將 SharePoint 專案系統類型與其他 Visual Studio 專案類型之間](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)。  
  
## <a name="see-also"></a>另請參閱
 [定義自訂 SharePoint 專案項目類型](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [擴充 SharePoint 專案項目](../sharepoint/extending-sharepoint-project-items.md)   
 [擴充 SharePoint 專案](../sharepoint/extending-sharepoint-projects.md)   
 [擴充 SharePoint 封裝和部署](../sharepoint/extending-sharepoint-packaging-and-deployment.md)   
 [將資料儲存在 SharePoint 專案系統的擴充功能](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)   
 [SharePoint 專案系統類型與其他 Visual Studio 專案類型之間轉換](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)   
 [擴充 Visual Studio 中的 SharePoint 工具](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)   
 [SharePoint 工具延伸模組的程式設計概念和功能](../sharepoint/programming-concepts-and-features-for-sharepoint-tools-extensions.md)  
