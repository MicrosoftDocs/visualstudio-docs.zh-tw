---
title: "如何： 新增與移除功能和封裝的項目使用封裝總管 |Microsoft 文件"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.SharePointTools.RAD.PackagingExplorer
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords: SharePoint development in Visual Studio, packages
ms.assetid: 549d5848-f0c9-42c6-b7f5-bc1e626a30e6
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 0ad944d9997b80a89971802d86a2fa3075533a5b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-and-remove-features-and-items-to-a-package-by-using-the-packaging-explorer"></a>如何：使用封裝總管在套件中新增與移除功能和項目
  若要設定套件以部署 SharePoint 項目和功能，您可以使用 [封裝總管] 中。 您可以調整的 SharePoint 專案項目和功能.wsp 檔案內。  
  
 或者，您可以使用封裝設計工具來檢視和重新排列的功能變更的啟動順序。 如需詳細資訊，請參閱[如何： 加入和移除使用封裝設計工具的功能和封裝的項目](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)。  
  
## <a name="opening-the-packaging-explorer"></a>開啟 [封裝總管]  
 如果您的 Visual Studio 方案中有至少一個 SharePoint 專案，您可以開啟 [封裝總管] 中，使用下列程序。 此外，[封裝總管] 會自動開啟功能或封裝的設計工具的檢視時。 關閉所有的功能和封裝設計工具之後，[封裝總管] 也會關閉。  
  
#### <a name="to-open-the-packaging-explorer"></a>若要開啟 [封裝總管]  
  
1.  在功能表列上選擇 **檢視**，**其他視窗**，**封裝總管**。  
  
     **封裝總管**會出現在**工具箱**。  
  
## <a name="adding-a-feature-to-a-package"></a>將功能加入封裝  
 您可以使用 [封裝總管] 中，將新的和現有功能加入封裝中。  
  
#### <a name="to-add-a-sharepoint-feature"></a>若要加入 SharePoint 功能  
  
1.  開啟**封裝總管**，開啟專案的捷徑功能表，然後選擇**加入功能**。  
  
#### <a name="to-move-an-existing-sharepoint-feature"></a>若要移動現有的 SharePoint 功能  
  
1.  開啟**封裝總管**，然後執行下列步驟：  
  
    -   拖曳**功能**從某個專案到另一個專案。  
  
    -   開啟功能的捷徑功能表，選擇 **剪下**，開啟您想要移動功能，再選擇的專案的捷徑功能表**貼上**。  
  
    > [!NOTE]  
    >  如果您的方案中有一個以上的 SharePoint 專案，請使用此程序。  
  
## <a name="validating-a-feature-or-package"></a>驗證功能或封裝  
 您可以識別潛在問題的 SharePoint 功能和封裝驗證的檔案。 警告和錯誤會顯示在輸出視窗 和 錯誤清單 視窗中。  
  
#### <a name="to-validate-a-sharepoint-feature-or-package"></a>若要驗證的 SharePoint 功能或封裝  
  
1.  開啟**封裝總管**。  
  
2.  功能或封裝中，開啟捷徑功能表，然後選擇**驗證**。  
  
## <a name="see-also"></a>請參閱  
 [封裝和部署 SharePoint 方案](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  