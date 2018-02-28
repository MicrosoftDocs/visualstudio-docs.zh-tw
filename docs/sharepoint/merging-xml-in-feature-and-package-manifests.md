---
title: "合併功能和封裝中的 XML 資訊清單 |Microsoft 文件"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packaging
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: 81e6f83dd4fc825e885843a47d45485918f7dabe
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/10/2018
---
# <a name="merging-xml-in-feature-and-package-manifests"></a>合併功能和封裝資訊清單中的 XML
  功能和封裝所定義[!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]資訊清單檔案。 這些封裝資訊清單是從設計工具及自訂產生的資料組合[!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]由使用者輸入資訊清單範本中。 在封裝階段[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]merges 自訂[!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]陳述式與設計工具提供[!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]形成封裝[!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]資訊清單檔案。 類似的項目更新版本中合併的例外狀況，例外狀況會合併，以避免[!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]之後將檔案部署至 SharePoint，並將資訊清單檔案較小且更有效率的驗證錯誤。  
  
## <a name="modifying-the-manifests"></a>修改資訊清單  
 您無法直接修改封裝的資訊清單檔案，直到您停用的功能或封裝的設計工具。 不過，您可以手動新增自訂[!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]元素資訊清單範本的功能和封裝設計工具透過或[!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]編輯器。 如需詳細資訊，請參閱[How to： 自訂 SharePoint 功能](../sharepoint/how-to-customize-a-sharepoint-feature.md)和[How to： 自訂 SharePoint 方案套件](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)。  
  
## <a name="feature-and-package-manifest-merge-process"></a>功能和封裝資訊清單合併程序  
 合併與設計工具提供的項目，自訂項目時[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]會使用下列程序。 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]檢查每個項目是否具有唯一索引鍵值。 如果項目沒有唯一的索引鍵值，則會將其附加至封裝的資訊清單檔。 同樣地，具有多個索引鍵的項目無法合併。 因此，它們會附加到資訊清單檔案。  
  
 如果項目具有唯一的索引鍵，[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]比較的設計工具和自訂的索引鍵的值。 如果值相符時，合併成單一值。 如果值不同，則會捨棄設計工具索引鍵的值，且自訂的索引鍵值。 集合也會合併。 例如，如果設計工具產生[!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]和自訂[!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]同時包含組件的集合、 封裝資訊清單包含只有一個組件集合。  
  
## <a name="merge-exceptions"></a>合併例外狀況  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]大部分的設計工具會將合併[!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]以及類似的自訂項目[!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]只要他們有單一的唯一識別屬性的項目。 不過，某些項目沒有所需的唯一識別碼[!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]合併。 這些項目稱為*合併例外狀況*。 在這些情況下，[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]不會合併自訂[!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]項目及設計工具提供[!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]項目，但改為將它們附加至封裝資訊清單檔案。  
  
 下列是合併功能和封裝的例外狀況清單[!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]資訊清單檔案。  
  
|Designer|XML 項目|  
|--------------|-----------------|  
|功能設計工具|ActivationDependency|  
|功能設計工具|UpgradeAction|  
|封裝設計工具|SafeControl|  
|封裝設計工具|CodeAccessSecurity|  
  
## <a name="feature-manifest-elements"></a>功能資訊清單的項目  
 下表是一份其用來比對的唯一索引鍵的功能資訊清單的所有項目可以合併。  
  
|項目名稱|唯一索引鍵|  
|------------------|----------------|  
|功能 （所有屬性）|*屬性名稱*（功能項目的每個屬性名稱是唯一的索引鍵）。|  
|ElementFile|位置|  
|ElementManifests/ElementManifest|位置|  
|Properties/屬性|Key|  
|CustomUpgradeAction|名稱|  
|CustomUpgradeActionParameter|名稱|  
  
> [!NOTE]  
>  因為修改 CustomUpgradeAction 元素的唯一方式是在自訂[!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]編輯器 中，未合併的影響很低。  
  
## <a name="package-manifest-elements"></a>封裝資訊清單的項目  
 下表是一份套件資訊清單的所有項目可以合併和其用來比對的唯一索引鍵。  
  
|元素名稱|唯一索引鍵|  
|------------------|----------------|  
|方案 （所有屬性）|*屬性名稱*（方案項目之每個屬性名稱是唯一的索引鍵）。|  
|ApplicationResourceFiles/ApplicationResourceFile|位置|  
|組件/組件|位置|  
|ClassResources/ClassResource|位置|  
|DwpFiles/DwpFile|位置|  
|FeatureManifests/FeatureManifest|位置|  
|資源/資源|位置|  
|資料夾/RootFile|位置|  
|SiteDefinitionManifests/SiteDefinitionManifest|位置|  
|WebTempFile|位置|  
|TemplateFiles/TemplateFile|位置|  
|SolutionDependency|方案識別碼已|  
  
## <a name="manually-add-deployed-files"></a>手動新增已部署的檔案  
 資訊清單的項目，例如 ApplicationResourceFile 和 DwpFiles，指定包含檔案名稱的位置。 不過，將檔案名稱的項目加入至資訊清單範本不會對基礎檔案封裝。 您必須將檔案加入至要包含在封裝中，並據此將其部署類型屬性的專案。  
  
## <a name="see-also"></a>請參閱  
 [封裝和部署 SharePoint 方案](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)   
 [建置和偵錯 SharePoint 方案](../sharepoint/building-and-debugging-sharepoint-solutions.md)  
  
  