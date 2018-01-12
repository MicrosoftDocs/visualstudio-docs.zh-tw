---
title: "建立 SharePoint 功能 |Microsoft 文件"
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
- SharePoint development in Visual Studio, features
- features [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 9fa42efc654bd3835a4f1ec1a5002136813550a0
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/10/2018
---
# <a name="creating-sharepoint-features"></a>建立 SharePoint 功能
  您可以使用 SharePoint 功能來分組相關更容易進行部署的 SharePoint 專案項目。 您可以建立功能、 設定範圍，及使用 SharePoint 功能設計工具，將其他功能標示為相依性。 在設計工具也會產生資訊清單，其中會描述每項功能的 XML 檔案。  
  
## <a name="adding-features-to-the-sharepoint-solution"></a>將功能加入 SharePoint 方案  
 您可新增至 SharePoint 方案的功能，使用方案總管 或 封裝總管 中。 您可以使用下列方法之一新增一項功能。  
  
-   在**方案總管] 中**，開啟捷徑功能表**功能**，然後選擇 [**加入功能**。  
  
-   在**封裝總管**，開啟封裝的捷徑功能表，然後選擇**加入功能**。  
  
## <a name="using-the-feature-designer"></a>使用功能設計工具  
 SharePoint 方案可以包含一或多個 SharePoint 功能，在 [方案總管] 中的 [功能] 節點底下的分組。 每個功能都有它自己**功能設計工具**，您可以使用自訂的功能屬性。 如需詳細資訊，請參閱[How to： 自訂 SharePoint 功能](../sharepoint/how-to-customize-a-sharepoint-feature.md)。 若要從另一個辨別功能，您可以設定的功能屬性，例如標題、 描述、 版本和範圍。  
  
### <a name="feature-designer-options"></a>功能設計工具選項  
 建立一項功能之後，您可以使用功能設計工具進行自訂。  
  
 下表描述功能設計工具中顯示的功能屬性。  
  
|屬性|描述|  
|--------------|-----------------|  
|標題|選擇性。 此功能的預設標題設定為*SolutionName**FeatureName*。|  
|描述|選擇性。 SharePoint 功能的描述。|  
|範圍|必要。 如果一項功能由使用**方案總管 中**，範圍預設設定為 Web。<br /><br /> 伺服陣列： 啟動整個伺服器陣列的功能。<br /><br /> 站台： 啟動網站集合中的所有網站的功能。<br /><br /> -Web： 啟動特定網站的功能。<br /><br /> -WebApplication： 啟動 web 應用程式中的所有網站的功能。|  
|在方案中的項目|SharePoint 的所有項目可以加入的功能。|  
|功能中的項目|SharePoint 專案項目已加入的功能。|  
  
## <a name="adding-and-removing-sharepoint-project-items"></a>加入和移除 SharePoint 專案項目  
 您可以選取您要新增可部署的 SharePoint 功能的 SharePoint 專案項目。 使用**功能設計工具**加入和移除項目功能，以及檢視功能資訊清單。 如需詳細資訊，請參閱[如何： 加入和移除 SharePoint 功能的項目](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)。  
  
## <a name="adding-feature-dependencies"></a>加入功能依存性  
 您可以設定功能資訊清單，讓 SharePoint 伺服器中啟用某些功能之前啟動您的功能。 比方說，如果您的 SharePoint 功能相依於其他功能的功能或資料，SharePoint 伺服器可以先嘗試啟動的任何功能取決於您的功能。 如需詳細資訊，請參閱[如何： 加入和移除功能相依性](../sharepoint/how-to-add-and-remove-feature-dependencies.md)。  
  
## <a name="see-also"></a>請參閱  
 [如何： 自訂 SharePoint 功能](../sharepoint/how-to-customize-a-sharepoint-feature.md)   
 [如何： 加入和移除 SharePoint 功能的項目](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)   
 [如何：新增與移除功能相依性](../sharepoint/how-to-add-and-remove-feature-dependencies.md)  
  
  