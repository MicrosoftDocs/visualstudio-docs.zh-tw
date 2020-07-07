---
title: 封裝設計工具：新增 & 移除封裝的功能和專案
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
ms.openlocfilehash: 4dfbda711c42e475af5f17c8799e53b13e26611a
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: zh-TW
ms.lasthandoff: 07/06/2020
ms.locfileid: "86014602"
---
# <a name="how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer"></a>如何：使用封裝設計工具在封裝中加入和移除功能和專案
  當您建立 SharePoint 方案時，Visual Studio 會將預設 SharePoint 功能加入方案中的封裝。 在最終部署之前，您可以新增和移除 SharePoint 專案專案和功能，以修改 SharePoint 封裝。

 或者，您可以使用 [封裝瀏覽器] 來新增和移除 SharePoint 專案專案。 您也可以查看和變更放入封裝（.wsp）中的 SharePoint 專案專案和功能的階層。 如需詳細資訊，請參閱[如何：使用封裝瀏覽器新增和移除封裝中的功能和專案](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-packaging-explorer.md)。

## <a name="add-features-to-a-sharepoint-package"></a>將功能新增至 SharePoint 封裝
 您可以使用封裝設計工具將功能加入至 SharePoint 封裝。

#### <a name="to-add-sharepoint-features-with-the-package-designer"></a>若要使用封裝設計工具加入 SharePoint 功能

1. 開啟**封裝設計**工具。

    如需詳細資訊，請參閱[如何：自訂 SharePoint 方案套件](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)。

2. 執行下列一或多個步驟，以新增一或多個 SharePoint 功能：

   1. 按兩下 [方案清單] 中您想要新增之**專案**中的每個專案。

   2. 選擇您想要新增的專案，然後選擇 [**新增**] 按鈕（>）。

   3. 選擇 [**全部新增**] 按鈕（>>），一次新增所有專案。

      例如，您可以按兩下 [**方案**] 清單中專案的專案，將它加入至 [封裝] 清單**中的專案**。

      SharePoint 專案專案和功能會出現在 **[封裝**] 清單中的專案中。

## <a name="remove-features-from-a-sharepoint-package"></a>從 SharePoint 封裝移除功能
 您可以使用封裝設計工具來移除 SharePoint 封裝的功能。

#### <a name="to-remove-sharepoint-features-with-the-package-designer"></a>若要使用封裝設計工具移除 SharePoint 功能

1. 在 [**封裝的專案**] 清單中，選擇您想要移除的專案，然後選擇 [**移除**] （<）按鈕，或選擇 [**全部移除**] 按鈕（<<）以移除所有專案。

     SharePoint 專案會出現在 **[方案**] 清單的專案中。

## <a name="see-also"></a>另請參閱
- [建立 SharePoint 方案套件](../sharepoint/creating-sharepoint-solution-packages.md)
- [如何：自訂 SharePoint 方案套件](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)
- [如何：建立封裝](https://msdn.microsoft.com/b24be45c-e91d-49bb-afb0-7b265404214b)
