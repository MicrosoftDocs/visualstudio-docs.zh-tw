---
title: HOW TO：新增和移除其他組件 |Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.RAD.CustomAssembly
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
ms.openlocfilehash: fa25413a40c9b2333acbaba96d55008dbcebfd39
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60051605"
---
# <a name="how-to-add-and-remove-additional-assemblies"></a>HOW TO：新增和移除其他組件
  如果 SharePoint 封裝相依於其他組件的功能或資料，您可以新增組件至您的方案套件 (.wsp)。 如此一來，在 SharePoint 伺服器可確保自訂組件會安裝套件。

 您也可以新增和變更的安全控制項和組件相關聯的類別資源檔案。

## <a name="add-additional-assemblies-safe-controls-and-class-resources"></a>新增其他組件、 安全的控制項和類別資源
 您可以新增至 SharePoint 方案套件的其他組件。 沙箱化方案中的其他組件部署至全域組件快取中，但沙箱化方案中的 SharePoint 專案項目新增至內容資料庫。 這些額外的組件，您也可以新增安全的控制項和類別資源。 如需有關安全控制項的詳細資訊，請參閱[Providing Packaging and Deployment Information in 專案項目](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)或 「 建立 SafeControl 項目 」 中[部署 SharePoint Foundation 中的 Web 組件](http://go.microsoft.com/fwlink/?LinkId=245505)。

#### <a name="to-add-an-existing-assembly"></a>若要新增現有組件

1. 開啟**封裝設計工具**。 如需詳細資訊，請參閱[如何：自訂 SharePoint 方案套件](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)。

2. 選擇**進階** 索引標籤。

3. 選擇**新增**按鈕，然後再選擇**加入現有組件**從清單中。

     **加入現有組件** 對話方塊隨即出現。

4. 選擇省略符號 (![ASP.NET Mobile 設計工具橢圓形](../sharepoint/media/mwellipsis.gif "ASP.NET Mobile 設計工具橢圓形"))，然後選擇您想要新增的組件。 我們建議使用所選組件的相對路徑，供可攜性。

5. 針對**部署目標**，選擇**GlobalAssemblyCache**選項按鈕，將組件部署到全域組件快取中，或選擇**WebApplication**選項若要將組件部署到執行 SharePoint 的伺服器上的 WebApplication 資料夾 按鈕。

#### <a name="to-add-an-assembly-from-project-output"></a>若要從專案輸出新增組件

1. 開啟**封裝設計工具**。

     如需詳細資訊，請參閱[如何：自訂 SharePoint 方案套件](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)。

2. 選擇**進階** 索引標籤。

3. 選擇**新增**按鈕，然後再選擇**加入專案輸出組件**從清單中。

     **加入專案輸出組件** 對話方塊隨即出現。

4. 在 **原始碼專案**清單，然後選擇您想要新增的原始碼專案。

5. 針對**部署目標**，選擇**GlobalAssemblyCache**選項按鈕，將組件部署到全域組件快取中，或選擇**WebApplication**選項若要將組件部署到執行 SharePoint 的伺服器上的 WebApplication 資料夾 按鈕。

#### <a name="to-add-a-safe-control"></a>若要將安全控制項

1. 開啟**編輯現有的組件** 對話方塊。 若要這麼做，開啟 封裝設計工具中，選擇**進階**索引標籤上，選擇 組件，然後選擇**編輯** 按鈕。

2. 在 [**安全控制項**窗格中，選擇**按一下這裡以加入新項目**] 按鈕。

3. 在 [**組件名稱**] 欄中，輸入組件的名稱。

4. 在 [**命名空間**] 欄中，輸入安全控制項的命名空間的名稱。

5. 在 [**型別名稱**] 欄中，輸入類型的名稱。

#### <a name="to-add-a-class-resource"></a>若要加入類別資源

1. 開啟**編輯現有的組件** 對話方塊。 若要這麼做，開啟 封裝設計工具中，選擇**進階**索引標籤上，選擇 組件，然後選擇**編輯** 按鈕。

2. 在 **類別的資源** 窗格中，選擇**按一下這裡以加入新項目** 按鈕。

3. 在 **檔名**資料行中，選擇省略符號 (![ASP.NET Mobile 設計工具橢圓形](../sharepoint/media/mwellipsis.gif "ASP.NET Mobile 設計工具橢圓形"))，並選擇您想要新增的類別資源。

## <a name="delete-custom-assemblies"></a>刪除自訂組件
 您可以從 SharePoint 封裝時，刪除組件，或刪除現有的組件中的安全控制項及類別資源。

#### <a name="to-delete-an-existing-assembly"></a>若要刪除的現有組件

1. 開啟**封裝設計工具**。 如需詳細資訊，請參閱[如何：自訂 SharePoint 方案套件](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)。

2. 選擇**進階** 索引標籤。

3. 在 [**其他組件**] 窗格中，選擇您想要刪除的自訂組件。

4. 選擇**刪除** 按鈕。

#### <a name="to-delete-a-safe-control-for-an-assembly"></a>若要刪除組件的安全控制項

1. 開啟**編輯現有的組件** 對話方塊。 若要這麼做，開啟 封裝設計工具中，選擇**進階**索引標籤上，選擇 組件，然後選擇**編輯** 按鈕。

2. 選擇您想要刪除的安全控制項。

3. 選擇 Delete 鍵。

#### <a name="to-delete-a-class-resource-for-an-assembly"></a>若要刪除組件的類別資源

1. 開啟**編輯現有的組件** 對話方塊。 若要這麼做，開啟 封裝設計工具中，選擇**進階**索引標籤上，選擇 組件，然後選擇**編輯** 按鈕。

2. 選擇您想要刪除的類別資源。

3. 選擇 Delete 鍵。

## <a name="see-also"></a>另請參閱
- [建立 SharePoint 功能](../sharepoint/creating-sharepoint-features.md)
- [如何：自訂 SharePoint 功能](../sharepoint/how-to-customize-a-sharepoint-feature.md)
- [如何：新增和移除 SharePoint 功能的項目](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)
