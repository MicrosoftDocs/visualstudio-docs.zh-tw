---
title: 建立 SharePoint 功能 |Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, features
- features [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 55b1b3f2f243a6c4d35a4c1effbb4ca759abd9d9
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53842878"
---
# <a name="create-sharepoint-features"></a>建立 SharePoint 功能
  您可以使用 SharePoint 功能，將相關的 SharePoint 專案項目更容易部署。 您可以建立功能、 設定範圍，並標示為相依性的其他功能，使用 SharePoint 功能設計工具。 設計工具也會產生資訊清單，也就是描述每項功能的 XML 檔案。  
  
## <a name="add-features-to-the-sharepoint-solution"></a>將功能加入至 SharePoint 方案
 您可以使用 [方案總管] 或 [封裝總管] 中，將功能新增至 SharePoint 方案中。 您可以使用下列方法之一新增一項功能。  
  
-   中**方案總管**，開啟捷徑功能表**功能**，然後選擇**新增功能**。  
  
-   在 **封裝總管**，開啟封裝的捷徑功能表，然後選擇**加入功能**。  
  
## <a name="using-the-feature-designer"></a>使用功能設計工具
 SharePoint 方案可以包含一或多個 SharePoint 功能，在 [方案總管] 中的 [功能] 節點下分組。 每項功能都有它自己**功能設計工具**，您可以使用自訂的功能屬性。 如需詳細資訊，請參閱[＜How to：自訂 SharePoint 功能](../sharepoint/how-to-customize-a-sharepoint-feature.md)。 若要從另一個辨別功能，您可以設定功能屬性，例如標題、 描述、 版本和範圍。  
  
### <a name="feature-designer-options"></a>功能設計工具選項
 建立一項功能之後，您可以使用功能設計工具來自訂它。  
  
 下表描述會顯示在功能設計工具的功能屬性。  
  
|屬性|描述|  
|--------------|-----------------|  
|標題|選擇性。 此功能的預設標題設為*SolutionName* *FeatureName*。|  
|描述|選擇性。 SharePoint 功能的描述。|  
|範圍|必要項。 如果使用已建立特徵**方案總管 中**，範圍預設設定為 Web。<br /><br /> 伺服器陣列：啟用整個伺服器陣列的功能。<br /><br /> 站台：啟動網站集合中的所有網站的功能。<br /><br /> Web:啟動特定的 web 站台的功能。<br /><br /> -WebApplication:啟動 web 應用程式中的所有網站的功能。|  
|在方案中的項目|所有 SharePoint 項目可以加入至功能。|  
|在功能中的項目|此功能已加入 SharePoint 專案項目。|  
  
## <a name="add-and-remove-sharepoint-project-items"></a>新增和移除 SharePoint 專案項目
 您可以選取您想要新增可部署的 SharePoint 功能的 SharePoint 專案項目。 使用**功能設計工具**加入和移除項目功能，以及檢視功能資訊清單。 如需詳細資訊，請參閱[＜How to：新增和移除 SharePoint 功能的項目](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)。  
  
## <a name="add-feature-dependencies"></a>新增功能相依性
 您可以設定功能資訊清單，以便在 SharePoint 伺服器在之前啟動您的功能，就會啟動特定功能。 比方說，如果您的 SharePoint 功能相依於其他功能的功能或資料，在 SharePoint 伺服器可以先嘗試啟用的任何功能，取決於您的功能。 如需詳細資訊，請參閱[＜How to：新增和移除功能相依性](../sharepoint/how-to-add-and-remove-feature-dependencies.md)。  
  
## <a name="see-also"></a>另請參閱
 [如何：自訂 SharePoint 功能](../sharepoint/how-to-customize-a-sharepoint-feature.md)   
 [如何：新增和移除 SharePoint 功能的項目](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)   
 [如何：新增和移除功能相依性](../sharepoint/how-to-add-and-remove-feature-dependencies.md)  
