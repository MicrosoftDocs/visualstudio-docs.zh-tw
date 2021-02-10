---
title: 建立 SharePoint 功能 |Microsoft Docs
description: 建立 SharePoint 功能來將相關的 SharePoint 專案專案分組，以方便部署。 將功能新增至 SharePoint 方案。 使用功能設計工具。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, features
- features [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 8fc572f6fc5c0444fda619af5af49c6c2e52ac5d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99949112"
---
# <a name="create-sharepoint-features"></a>建立 SharePoint 功能
  您可以使用 SharePoint 功能來分組相關的 SharePoint 專案專案，以便更輕鬆地進行部署。 您可以使用 SharePoint 功能設計工具來建立功能、設定範圍，以及將其他功能標示為相依性。 設計工具也會產生資訊清單，這是描述每項功能的 XML 檔。

## <a name="add-features-to-the-sharepoint-solution"></a>將功能新增至 SharePoint 方案
 您可以使用方案總管或封裝瀏覽器，將功能新增至 SharePoint 方案。 您可以使用下列其中一種方法來新增功能。

- 在 **方案總管** 中，開啟 [ **功能**] 的快捷方式功能表，然後選擇 [ **加入功能**]。

- 在 [ **封裝瀏覽器**] 中，開啟封裝的快捷方式功能表，然後選擇 [ **加入功能**]。

## <a name="using-the-feature-designer"></a>使用功能設計工具
 SharePoint 方案可包含一或多個 SharePoint 功能，這些功能在方案總管的功能節點下分組。 每項功能都有自己的 **功能設計** 工具，可讓您用來自訂功能屬性。 如需詳細資訊，請參閱 [如何：自訂 SharePoint 功能](../sharepoint/how-to-customize-a-sharepoint-feature.md)。 若要區分不同的功能，您可以設定功能屬性，例如標題、描述、版本與範圍。

### <a name="feature-designer-options"></a>功能設計工具選項
 建立功能之後，您可以使用功能設計工具進行自訂。

 下表描述功能設計工具中顯示的功能屬性。

|屬性|描述|
|--------------|-----------------|
|標題|選擇性。 此功能的預設標題會設定為「*解決方案名稱* *」。*|
|描述|選擇性。 SharePoint 功能的描述。|
|影響範圍|必要。 如果功能是使用 **方案總管** 所建立，則範圍預設會設定為 Web。<br /><br /> -Farm：啟動整個伺服器陣列的功能。<br /><br /> -Site：為網站集合中的所有網站啟動功能。<br /><br /> -Web：啟動特定網站的功能。<br /><br /> -WebApplication：啟用 web 應用程式中所有網站的功能。|
|方案中的專案|所有可以新增至功能的 SharePoint 專案。|
|功能中的專案|已新增至功能的 SharePoint 專案專案。|

## <a name="add-and-remove-sharepoint-project-items"></a>新增和移除 SharePoint 專案專案
 您可以選取要為部署新增 SharePoint 功能的 SharePoint 專案專案。 您可以使用 **功能設計** 工具來新增和移除功能的專案，以及查看功能資訊清單。 如需詳細資訊，請參閱 [如何：在 SharePoint 功能中加入和移除專案](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)。

## <a name="add-feature-dependencies"></a>新增功能相依性
 您可以設定功能資訊清單，讓 SharePoint 伺服器先啟用某些功能，然後再啟用功能。 例如，如果您的 SharePoint 功能相依于其他功能或資料的功能，則 SharePoint server 可以先嘗試啟用功能所依賴的任何功能。 如需詳細資訊，請參閱 [如何：新增和移除功能](../sharepoint/how-to-add-and-remove-feature-dependencies.md)相依性。

## <a name="see-also"></a>另請參閱
- [如何：自訂 SharePoint 功能](../sharepoint/how-to-customize-a-sharepoint-feature.md)
- [如何：新增和移除 SharePoint 功能的專案](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)
- [如何：新增和移除功能相依性](../sharepoint/how-to-add-and-remove-feature-dependencies.md)
