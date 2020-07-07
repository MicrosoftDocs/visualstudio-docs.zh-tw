---
title: 如何：在 SharePoint 功能中加入和移除專案 |Microsoft Docs
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- VS.SharePointTools.RAD.FeatureDesigner
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, features
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 27c6ebfb0b0cdbff0a184859ffa2a73acab809c1
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: zh-TW
ms.lasthandoff: 07/06/2020
ms.locfileid: "86014532"
---
# <a name="how-to-add-and-remove-items-to-sharepoint-features"></a>如何：在 SharePoint 功能中加入和移除專案
  當您建立 SharePoint 方案時，Visual Studio 會將預設 SharePoint 專案專案加入至您的功能。 部署之前，您可以加入和移除 SharePoint 專案專案，以修改 SharePoint 功能。

## <a name="add-sharepoint-project-items-to-a-feature"></a>將 SharePoint 專案專案加入至功能

#### <a name="to-add-sharepoint-project-items-with-the-feature-designer"></a>若要使用功能設計工具加入 SharePoint 專案專案

1. 開啟功能設計工具。

    如需詳細資訊，請參閱[如何：自訂 SharePoint 功能](../sharepoint/how-to-customize-a-sharepoint-feature.md)。

2. 執行下列一或多個步驟，將**方案清單中**的專案中的一個或多個專案新增至功能清單**中的專案**：

   - 按兩下您要加入的每個項目。

   - 選擇您想要新增的專案，然後選擇 [**新增**] 按鈕（>）。

   - 選擇 [**全部新增**] 按鈕（>>）。

     SharePoint 專案專案會出現在功能清單的**專案**中。

## <a name="remove-sharepoint-project-items-from-a-feature"></a>從功能移除 SharePoint 專案專案

#### <a name="to-remove-sharepoint-items-with-the-feature-designer"></a>若要使用功能設計工具移除 SharePoint 專案

1. 在 [功能清單] 的 [**專案**] 中，選擇一或多個專案。

2. 選擇 [**移除**] 按鈕（<）一次移除一個專案，或選擇 [**全部移除**] 按鈕（<<）以移除所有專案。

     SharePoint 專案專案會出現在 **[方案**] 清單的專案中。

## <a name="see-also"></a>另請參閱
- [建立 SharePoint 功能](../sharepoint/creating-sharepoint-features.md)
- [封裝和部署 SharePoint 方案](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
