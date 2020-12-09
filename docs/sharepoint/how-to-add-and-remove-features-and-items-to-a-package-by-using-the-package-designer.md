---
title: 封裝設計工具：新增 & 移除功能和專案至封裝
titleSuffix: ''
description: 請參閱 Visual Studio 中的封裝設計工具，以瞭解如何在 SharePoint 套件中加入和移除功能和專案。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- VS.SharePointTools.RAD.PackageDesignerDesign
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packages
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 45c8da30a059599a291b18155dc48c4521d6d875
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/09/2020
ms.locfileid: "96914942"
---
# <a name="how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer"></a>如何：使用封裝設計工具加入和移除封裝的功能和專案
  當您建立 SharePoint 方案時，Visual Studio 會將預設的 SharePoint 功能加入至方案中的封裝。 在最終部署之前，您可以新增和移除 SharePoint 專案專案和功能，以修改 SharePoint 套件。

 或者，您也可以使用封裝瀏覽器來加入和移除 SharePoint 專案專案。 您也可以查看和變更放入封裝 ( .wsp) 中的 SharePoint 專案專案和功能的階層。 如需詳細資訊，請參閱 [如何：使用封裝瀏覽器加入和移除封裝的功能和專案](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-packaging-explorer.md)。

## <a name="add-features-to-a-sharepoint-package"></a>將功能加入至 SharePoint 套件
 您可以使用封裝設計工具將功能加入至 SharePoint 套件。

#### <a name="to-add-sharepoint-features-with-the-package-designer"></a>使用封裝設計工具加入 SharePoint 功能

1. 開啟 [ **封裝設計** 工具]。

    如需詳細資訊，請參閱 [如何：自訂 SharePoint 方案套件](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)。

2. 藉由執行下列一或多個步驟，加入一或多個 SharePoint 功能：

   1. 在 **[方案** ] 清單中，按兩下您要新增之專案中的每個專案。

   2. 選擇您要新增的專案，然後選擇 [ **新增** ] 按鈕 ( # A0) 。

   3. 選擇 [ **全部加入** ] 按鈕 ( # A2) ，一次加入所有專案。

      例如，您可以按兩下 **[方案** ] 清單中專案內的專案，將它加入至 **[封裝** ] 清單中的專案。

      SharePoint 專案專案和功能會出現在 **[封裝** ] 清單中的專案中。

## <a name="remove-features-from-a-sharepoint-package"></a>從 SharePoint 套件移除功能
 您可以使用封裝設計工具來移除 SharePoint 封裝的功能。

#### <a name="to-remove-sharepoint-features-with-the-package-designer"></a>若要使用封裝設計工具移除 SharePoint 功能

1. 在 **[封裝** ] 清單中的專案中，選擇您要移除的專案，然後選擇 [ **移除** ] ( # A0) 按鈕，或選擇 [ **全部移除** ] 按鈕 ( # A3) 移除所有專案。

     SharePoint 專案會出現在 **[方案** ] 清單中的專案中。

## <a name="see-also"></a>另請參閱
- [建立 SharePoint 方案套件](../sharepoint/creating-sharepoint-solution-packages.md)
- [如何：自訂 SharePoint 方案套件](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)
- [如何：建立封裝](/previous-versions/ee231585(v=vs.110))