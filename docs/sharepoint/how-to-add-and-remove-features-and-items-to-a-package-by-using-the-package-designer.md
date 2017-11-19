---
title: "如何： 加入和移除使用封裝設計工具的功能和封裝的項目 |Microsoft 文件"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.SharePointTools.RAD.PackageDesignerDesign
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords: SharePoint development in Visual Studio, packages
ms.assetid: 7dfa2c5d-3ac7-4573-abac-12a5e16efd1d
caps.latest.revision: "22"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9da26de3b5a3a71927e7518ff126a7186c01d7e5
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer"></a>如何：使用封裝設計工具在套件中新增與移除功能
  當您建立 SharePoint 方案時，Visual Studio 會將預設的 SharePoint 功能加入方案中的套件。 最終的部署之前新增和移除 SharePoint 專案項目與要修改 SharePoint 封裝的功能。  
  
 或者，您可以使用 [封裝總管] 來新增和移除 SharePoint 專案項目。 您也可以檢視和變更階層中的 SharePoint 專案項目並放套件 (.wsp) 的功能。 如需詳細資訊，請參閱[如何： 新增與移除功能和封裝的項目使用封裝總管](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-packaging-explorer.md)。  
  
## <a name="adding-features-to-a-sharepoint-package"></a>將功能加入 SharePoint 套件  
 您可以使用封裝設計工具，將功能加入 SharePoint 封裝。  
  
#### <a name="to-add-sharepoint-features-with-the-package-designer"></a>若要加入 SharePoint 功能與封裝設計工具  
  
1.  開啟**封裝設計工具**。  
  
     如需詳細資訊，請參閱[How to： 自訂 SharePoint 方案套件](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)。  
  
2.  新增一或多個 SharePoint 功能，執行下列其中一個或多個下列步驟：  
  
    1.  按兩下每個項目**方案中的項目**您想要加入的清單。  
  
    2.  選擇您想要新增，然後選擇一個項目**新增**按鈕 (>)。  
  
    3.  選擇**全部加入**按鈕 (>>) 若要同時新增所有項目。  
  
     例如，您可以按兩下中的項目**方案中的項目**將它加入至清單**封裝中的項目**清單。  
  
     SharePoint 專案項目和功能會出現在**封裝中的項目**清單。  
  
## <a name="removing-features-from-a-sharepoint-package"></a>從 SharePoint 套件中移除功能  
 若要移除 SharePoint 封裝的功能，您可以使用封裝設計工具。  
  
#### <a name="to-remove-sharepoint-features-with-the-package-designer"></a>若要移除 SharePoint 功能與封裝設計工具  
  
1.  在**封裝中的項目**清單中，選擇您想要移除，然後選擇一個項目**移除**(<) 按鈕，或選擇**全部移除**按鈕 (<<) 移除所有項目。  
  
     SharePoint 項目會出現在**方案中的項目**清單。  
  
## <a name="see-also"></a>另請參閱  
 [建立 SharePoint 方案套件](../sharepoint/creating-sharepoint-solution-packages.md)   
 [如何：自訂 SharePoint 方案套件](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)  
 [如何： 建立封裝](http://msdn.microsoft.com/en-us/b24be45c-e91d-49bb-afb0-7b265404214b)  
  
  