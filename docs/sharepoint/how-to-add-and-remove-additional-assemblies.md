---
title: "如何： 加入和移除其他組件 |Microsoft 文件"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.SharePointTools.RAD.CustomAssembly
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packages
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: 13ea5388a7b4ce2d1a045dec6339dc59e5c68393
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-add-and-remove-additional-assemblies"></a>如何：新增與移除其他組件
  如果 SharePoint 套件相依於其他功能或資料的組件，您可以加入組件加入您的方案套件 (.wsp)。 如此一來，在 SharePoint 伺服器可確保套件安裝的自訂組件。  
  
 您也可以新增和變更的安全控制和組件相關聯的類別資源檔案。  
  
## <a name="adding-additional-assemblies-safe-controls-and-class-resources"></a>加入其他組件、 安全的控制項和類別資源  
 您可以加入至 SharePoint 方案套件的其他組件。 沙箱化方案中的其他組件部署至全域組件快取，但在沙箱化方案中的 SharePoint 專案項目新增至內容資料庫。 您也可以將安全控制項和類別資源加入至這些額外的組件。 如需安全控制項的詳細資訊，請參閱[提供封裝和專案項目中的部署資訊](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)或 「 建立 SafeControl 項目 」 中[部署在 SharePoint Foundation 中的 Web 組件](http://go.microsoft.com/fwlink/?LinkId=245505)。  
  
#### <a name="to-add-an-existing-assembly"></a>若要加入現有的組件  
  
1.  開啟**封裝設計工具**。 如需詳細資訊，請參閱[How to： 自訂 SharePoint 方案套件](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)。  
  
2.  選擇**進階** 索引標籤。  
  
3.  選擇**新增**按鈕，然後再選擇**加入現有的組件**從清單中。  
  
     **加入現有的組件** 對話方塊隨即出現。  
  
4.  選擇省略符號 (![ASP.NET Mobile 設計工具橢圓形](../sharepoint/media/mwellipsis.gif "ASP.NET Mobile 設計工具橢圓形"))，然後選擇您想要加入的組件。 我們建議針對可攜性用途使用所選組件的相對路徑。  
  
5.  如**部署目標**，選擇**GlobalAssemblyCache**選項按鈕，將組件部署到全域組件快取中，或選擇**WebApplication**選項按鈕，以將組件部署到執行 SharePoint 的伺服器上的 WebApplication 資料夾。  
  
#### <a name="to-add-an-assembly-from-project-output"></a>若要從專案輸出加入組件  
  
1.  開啟**封裝設計工具**。  
  
     如需詳細資訊，請參閱[How to： 自訂 SharePoint 方案套件](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)。  
  
2.  選擇**進階** 索引標籤。  
  
3.  選擇**新增**按鈕，然後再選擇**加入專案輸出組件**從清單中。  
  
     **加入專案輸出組件** 對話方塊隨即出現。  
  
4.  在**原始碼專案**清單，並選擇您想要加入的來源專案。  
  
5.  如**部署目標**，選擇**GlobalAssemblyCache**選項按鈕，將組件部署到全域組件快取中，或選擇**WebApplication**選項按鈕，以將組件部署到執行 SharePoint 的伺服器上的 WebApplication 資料夾。  
  
#### <a name="to-add-a-safe-control"></a>若要加入安全的控制項  
  
1.  開啟**編輯現有的組件** 對話方塊。 若要完成這項作業，開啟封裝設計工具，選擇**進階**索引標籤上，選擇 [組件，然後選擇**編輯**] 按鈕。  
  
2.  在**安全控制項** 窗格中，選擇**按一下此處以加入新項目** 按鈕。  
  
3.  在**組件名稱**資料行中，輸入組件的名稱。  
  
4.  在**命名空間**資料行中，輸入安全控制項的命名空間的名稱。  
  
5.  在**型別名稱**資料行中，輸入類型的名稱。  
  
#### <a name="to-add-a-class-resource"></a>若要加入類別資源  
  
1.  開啟**編輯現有的組件** 對話方塊。 若要完成這項作業，開啟封裝設計工具，選擇**進階**索引標籤上，選擇 [組件，然後選擇**編輯**] 按鈕。  
  
2.  在**類別資源** 窗格中，選擇**按一下此處以加入新項目** 按鈕。  
  
3.  在**檔案名稱**資料行中，選擇省略符號 (![ASP.NET Mobile 設計工具橢圓形](../sharepoint/media/mwellipsis.gif "ASP.NET Mobile 設計工具橢圓形"))，並選擇您想要新增的類別資源。  
  
## <a name="deleting-custom-assemblies"></a>刪除自訂組件  
 您可以從 SharePoint 封裝時，刪除組件，或刪除現有的組件中的安全控制項和類別資源。  
  
#### <a name="to-delete-an-existing-assembly"></a>若要刪除現有的組件  
  
1.  開啟**封裝設計工具**。 如需詳細資訊，請參閱[How to： 自訂 SharePoint 方案套件](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)。  
  
2.  選擇**進階** 索引標籤。  
  
3.  在**其他組件** 窗格中，選擇您想要刪除自訂組件。  
  
4.  選擇**刪除** 按鈕。  
  
#### <a name="to-delete-a-safe-control-for-an-assembly"></a>若要刪除安全控制組件  
  
1.  開啟**編輯現有的組件** 對話方塊。 若要完成這項作業，開啟封裝設計工具，選擇**進階**索引標籤上，選擇 [組件，然後選擇**編輯**] 按鈕。  
  
2.  選擇您想要刪除的安全控制項。  
  
3.  選擇 Delete 鍵。  
  
#### <a name="to-delete-a-class-resource-for-an-assembly"></a>若要刪除之組件的類別資源  
  
1.  開啟**編輯現有的組件** 對話方塊。 若要完成這項作業，開啟封裝設計工具，選擇**進階**索引標籤上，選擇 [組件，然後選擇**編輯**] 按鈕。  
  
2.  選擇您想要刪除的類別資源。  
  
3.  選擇 Delete 鍵。  
  
## <a name="see-also"></a>請參閱  
 [建立 SharePoint 功能](../sharepoint/creating-sharepoint-features.md)   
 [如何： 自訂 SharePoint 功能](../sharepoint/how-to-customize-a-sharepoint-feature.md)   
 [如何：新增與移除 SharePoint 功能中的項目](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)   
  
  