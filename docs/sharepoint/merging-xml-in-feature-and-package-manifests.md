---
title: 合併功能和套件資訊清單中的 XML |Microsoft Docs
description: 合併設計工具-在 SharePoint 功能和套件資訊清單中產生和使用者加入的 XML 程式碼。 學習功能和套件資訊清單元素，以及合併例外狀況。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packaging
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 16305ed63f48d9f14e35aeb8d37e35f23f40be25
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2020
ms.locfileid: "96304227"
---
# <a name="merge-xml-in-feature-and-package-manifests"></a>合併功能和封裝資訊清單中的 XML
  功能和封裝是由資訊清單檔案所定義 [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] 。 這些封裝的資訊清單是 [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] 由使用者從在資訊清單範本中輸入的設計師和自訂所產生的資料組合。 在封裝期間，將 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 自訂 [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] 語句與提供的設計工具合併， [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] 以形成封裝的 [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] 資訊清單檔案。 類似的元素（稍後會在合併例外狀況中注明例外狀況）會合並，以避免 [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] 在您將檔案部署至 SharePoint 之後的驗證錯誤，以及讓資訊清單檔案更小且更有效率。

## <a name="modify-the-manifests"></a>修改資訊清單
 在您停用功能或封裝設計工具之前，您無法直接修改已封裝的資訊清單檔案。 不過，您可以 [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] 透過功能和封裝設計工具或編輯器，手動將自訂元素加入資訊清單範本 [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] 。 如需詳細資訊，請參閱 [如何：自訂 Sharepoint 功能](../sharepoint/how-to-customize-a-sharepoint-feature.md) 和 [如何：自訂 sharepoint 方案套件](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)。

## <a name="feature-and-package-manifest-merge-process"></a>功能和套件資訊清單合併處理
 將自訂元素與設計工具提供的專案結合時，會 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 使用下列程式。 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 檢查每個元素是否有唯一的索引鍵值。 如果項目沒有唯一的索引鍵值，則會將其附加至封裝的資訊清單檔。 同樣地，具有多個索引鍵的項目無法合併。 因此，它們會附加至資訊清單檔。

 如果專案有唯一索引鍵，則會 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 比較設計工具和自訂索引鍵的值。 如果值相符，則會合並成單一值。 如果值不同，則會捨棄設計工具索引鍵值，並使用自訂索引鍵值。 集合也會合並。 例如，如果設計工具產生的 [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] 和自訂 [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] 都包含元件集合，則封裝的資訊清單只會包含一個元件集合。

## <a name="merge-exceptions"></a>合併例外狀況
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 將大部分的設計工具 [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] 元素與類似的自訂元素合併在一起 [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] ，只要它們具有單一、唯一的識別屬性即可。 不過，某些元素缺少合併所需的唯一識別碼 [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] 。 這些元素稱為 *合併例外* 狀況。 在這些情況下，不 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 會將自訂元素與設計工具提供的專案合併在 [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] 一起 [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] ，而是將它們附加至封裝的資訊清單檔案。

 以下是功能和套件資訊清單檔案的合併例外狀況清單 [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] 。

|Designer|XML 元素|
|--------------|-----------------|
|功能設計工具|ActivationDependency|
|功能設計工具|UpgradeAction|
|封裝設計工具|SafeControl|
|封裝設計工具|Codeaccesssecurityhelper|

## <a name="feature-manifest-elements"></a>功能資訊清單元素
 下表列出所有可以合併的功能資訊清單元素，以及用於比對的唯一索引鍵。

|元素名稱|唯一索引鍵|
|------------------|----------------|
|功能 (所有屬性) |*屬性名稱* (功能專案的每個屬性名稱都是唯一索引鍵。 ) |
|ElementFile|Location|
|ElementManifests/ElementManifest|Location|
|屬性/屬性|Key|
|CustomUpgradeAction|名稱|
|CustomUpgradeActionParameter|名稱|

> [!NOTE]
> 由於修改 CustomUpgradeAction 專案的唯一方法是在自訂編輯器中 [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] ，因此不會合並的效果很低。

## <a name="package-manifest-elements"></a>封裝資訊清單元素
 下表列出所有可以合併的套件資訊清單元素，以及用於比對的唯一索引鍵。

|元素名稱|唯一索引鍵|
|------------------|----------------|
|所有屬性) 的解決方案 (|*屬性名稱* (方案元素的每個屬性名稱都是唯一索引鍵。 ) |
|ApplicationResourceFiles/ApplicationResourceFile|Location|
|元件/元件|Location|
|ClassResources/ClassResource|Location|
|DwpFiles/DwpFile|Location|
|FeatureManifests/FeatureManifest|Location|
|資源/資源|Location|
|RootFiles/RootFile|Location|
|SiteDefinitionManifests/SiteDefinitionManifest|Location|
|WebTempFile|Location|
|TemplateFiles/TemplateFile|Location|
|SolutionDependency|SolutionID|

## <a name="manually-add-deployed-files"></a>手動新增已部署的檔案
 某些資訊清單元素（例如 ApplicationResourceFile 和 DwpFiles）會指定包含檔案名的位置。 但是，將檔案名專案加入資訊清單範本中並不會將基礎檔案加入封裝中。 您必須將檔案新增至專案，以將它包含在封裝中，並據以設定其部署類型屬性。

## <a name="see-also"></a>另請參閱
- [封裝和部署 SharePoint 方案](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
- [建置和偵錯 SharePoint 方案](../sharepoint/building-and-debugging-sharepoint-solutions.md)
