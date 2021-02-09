---
title: 如何：新增和移除其他元件 |Microsoft Docs
description: 瞭解如何在 SharePoint 方案套件中加入和移除其他元件。 也可以新增或刪除安全控制項和類別資源。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- VS.SharePointTools.RAD.CustomAssembly
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packages
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: cc672a8a0ff7edd66504b5ecbf48e622fad085ea
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99923627"
---
# <a name="how-to-add-and-remove-additional-assemblies"></a>如何：新增和移除其他元件
  如果 SharePoint 封裝相依于其他元件的功能或資料，您可以將元件加入至方案套件， ( .wsp) 。 如此一來，SharePoint 伺服器便可確保自訂群組件會隨封裝一起安裝。

 您也可以新增和變更與元件相關聯的安全控制項和類別資源檔。

## <a name="add-additional-assemblies-safe-controls-and-class-resources"></a>新增其他元件、安全控制項和類別資源
 您可以將其他元件新增至 SharePoint 方案套件。 沙箱化方案中的其他元件會部署到全域組件快取，但是沙箱化方案中的 SharePoint 專案專案會新增至內容資料庫。 您也可以將安全的控制項和類別資源加入這些額外的元件。 如需安全控制項的詳細資訊，請參閱在[SharePoint Foundation 中部署 Web 組件](/previous-versions/office/developer/sharepoint-2010/cc768621(v=office.14))中[提供專案專案中的封裝和部署資訊](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)或「建立 SafeControl 專案」。

#### <a name="to-add-an-existing-assembly"></a>若要加入現有的元件

1. 開啟 [ **封裝設計** 工具]。 如需詳細資訊，請參閱 [如何：自訂 SharePoint 方案套件](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)。

2. 選擇 [ **Advanced （Advanced** ）] 索引標籤。

3. 選擇 [ **加入** ] 按鈕，然後從清單中選擇 [ **加入現有的元件** ]。

     [ **加入現有元件** ] 對話方塊隨即出現。

4. 選擇省略號 (![ASP.NET Mobile Designer 橢圓形](../sharepoint/media/mwellipsis.gif "ASP.NET Mobile 設計工具橢圓形")) ，然後選擇您要加入的元件。 基於可攜性的目的，我們建議使用所選元件的相對路徑。

5. 在 [ **部署目標**] 中，選擇 [ **GlobalAssemblyCache** ] 選項按鈕將元件部署到全域組件快取，或選擇 [ **WebApplication** ] 選項按鈕，將元件部署到執行 SharePoint 的伺服器上的 WebApplication 資料夾。

#### <a name="to-add-an-assembly-from-project-output"></a>從專案輸出加入元件

1. 開啟 [ **封裝設計** 工具]。

     如需詳細資訊，請參閱 [如何：自訂 SharePoint 方案套件](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)。

2. 選擇 [ **Advanced （Advanced** ）] 索引標籤。

3. 選擇 [ **加入** ] 按鈕，然後從清單中選擇 [ **從專案輸出加入元件** ]。

     [ **從專案輸出加入元件** ] 對話方塊隨即出現。

4. 在 [ **來源專案** ] 清單中，選擇您要加入的來源專案。

5. 在 [ **部署目標**] 中，選擇 [ **GlobalAssemblyCache** ] 選項按鈕將元件部署到全域組件快取，或選擇 [ **WebApplication** ] 選項按鈕，將元件部署到執行 SharePoint 的伺服器上的 WebApplication 資料夾。

#### <a name="to-add-a-safe-control"></a>若要加入安全控制項

1. 開啟 [ **編輯現有元件** ] 對話方塊。 若要完成此動作，請開啟 [封裝設計工具]，選擇 [ **Advanced** ] 索引標籤，選擇元件，然後選擇 [ **編輯** ] 按鈕。

2. 在 [ **安全控制項** ] 窗格中，選擇 [ **按一下這裡加入新專案** ] 按鈕。

3. 在 [ **元件名稱** ] 欄中，輸入元件的名稱。

4. 在 [ **命名空間** ] 欄中，輸入安全控制項命名空間的名稱。

5. 在 [ **類型名稱** ] 欄中，輸入類型的名稱。

#### <a name="to-add-a-class-resource"></a>新增類別資源

1. 開啟 [ **編輯現有元件** ] 對話方塊。 若要完成此動作，請開啟 [封裝設計工具]，選擇 [ **Advanced** ] 索引標籤，選擇元件，然後選擇 [ **編輯** ] 按鈕。

2. 在 [ **類別資源** ] 窗格中，選擇 [ **按一下這裡加入新專案** ] 按鈕。

3. 在 [ **檔案名** ] 欄中，選擇省略號 (![ASP.NET Mobile Designer 橢圓形](../sharepoint/media/mwellipsis.gif "ASP.NET Mobile 設計工具橢圓形")) ，然後選擇您要加入的類別資源。

## <a name="delete-custom-assemblies"></a>刪除自訂群組件
 您可以從 SharePoint 封裝刪除元件，或從現有的元件中刪除安全的控制項和類別資源。

#### <a name="to-delete-an-existing-assembly"></a>若要刪除現有的元件

1. 開啟 [ **封裝設計** 工具]。 如需詳細資訊，請參閱 [如何：自訂 SharePoint 方案套件](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)。

2. 選擇 [ **Advanced （Advanced** ）] 索引標籤。

3. 在 [ **其他元件** ] 窗格中，選擇您要刪除的自訂群組件。

4. 選擇 [**刪除**] 按鈕。

#### <a name="to-delete-a-safe-control-for-an-assembly"></a>若要刪除元件的安全控制項

1. 開啟 [ **編輯現有元件** ] 對話方塊。 若要完成此動作，請開啟 [封裝設計工具]，選擇 [ **Advanced** ] 索引標籤，選擇元件，然後選擇 [ **編輯** ] 按鈕。

2. 選擇您想要刪除的安全控制項。

3. 選擇 [刪除] 機碼。

#### <a name="to-delete-a-class-resource-for-an-assembly"></a>刪除元件的類別資源

1. 開啟 [ **編輯現有元件** ] 對話方塊。 若要完成此動作，請開啟 [封裝設計工具]，選擇 [ **Advanced** ] 索引標籤，選擇元件，然後選擇 [ **編輯** ] 按鈕。

2. 選擇您想要刪除的類別資源。

3. 選擇 [刪除] 機碼。

## <a name="see-also"></a>另請參閱
- [建立 SharePoint 功能](../sharepoint/creating-sharepoint-features.md)
- [如何：自訂 SharePoint 功能](../sharepoint/how-to-customize-a-sharepoint-feature.md)
- [如何：新增和移除 SharePoint 功能的專案](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)
