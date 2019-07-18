---
title: 封裝設計工具：新增 / 移除功能和封裝的項目
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: fbd44bbf3b337815c8c72cea66dd4d56fc645ade
ms.sourcegitcommit: 25570fb5fb197318a96d45160eaf7def60d49b2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/30/2019
ms.locfileid: "66401617"
---
# <a name="how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer"></a>作法：新增和移除功能和項目加入封裝時，使用封裝設計工具
  當您建立 SharePoint 方案時，Visual Studio 會將預設的 SharePoint 功能加入方案中的套件。 最終的部署之前，您可以新增並移除 SharePoint 專案項目及修改 SharePoint 封裝的功能。

 或者，您可以使用 [封裝總管] 中新增和移除 SharePoint 專案項目。 您也可以檢視和變更的階層會放入套件 (.wsp) 的功能與 SharePoint 專案項目。 如需詳細資訊，請參閱[如何：新增和移除功能和項目加入封裝時，使用 [封裝總管] 中](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-packaging-explorer.md)。

## <a name="add-features-to-a-sharepoint-package"></a>將功能加入至 SharePoint 封裝
 您可以使用 封裝設計工具，將功能新增至 SharePoint 封裝。

#### <a name="to-add-sharepoint-features-with-the-package-designer"></a>若要新增的 SharePoint 功能與封裝設計工具

1. 開啟**封裝設計工具**。

    如需詳細資訊，請參閱[如何：自訂 SharePoint 方案套件](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)。

2. 執行下列一或多個下列的步驟，以新增一或多個 SharePoint 功能：

   1. 按兩下每個項目**方案中的項目**您想要新增的清單。

   2. 選擇您想要新增，然後選擇的項目**新增**按鈕 (>)。

   3. 選擇**全部新增**按鈕 (>>) 若要同時新增的所有項目。

      例如，您可以按兩下中的項目**方案中的項目**將它加入至清單**封裝中的項目**清單。

      SharePoint 專案項目和功能會出現在**封裝中的項目**清單。

## <a name="remove-features-from-a-sharepoint-package"></a>從 SharePoint 封裝中移除功能
 您可以使用封裝設計工具來移除 SharePoint 封裝的功能。

#### <a name="to-remove-sharepoint-features-with-the-package-designer"></a>若要移除 SharePoint 功能與封裝設計工具

1. 在 **封裝中的項目**清單中，選擇您想要移除此項目，然後選擇的項目**移除**(<) 按鈕，或選擇**全部移除**按鈕 (<<) 移除所有項目。

     SharePoint 項目會出現在**方案中的項目**清單。

## <a name="see-also"></a>另請參閱
- [建立 SharePoint 方案套件](../sharepoint/creating-sharepoint-solution-packages.md)
- [如何：自訂 SharePoint 方案套件](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)
- [如何：建立封裝](https://msdn.microsoft.com/b24be45c-e91d-49bb-afb0-7b265404214b)
