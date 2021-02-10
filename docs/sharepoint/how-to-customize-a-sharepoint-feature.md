---
title: 如何：自訂 SharePoint 功能 |Microsoft Docs
description: 自訂 Visual Studio 中的 SharePoint 功能。 當您在方案總管或 SharePoint 套件瀏覽器中加入新功能時，會開啟功能設計工具。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- VS.SharePointTools.RAD.FeatureDesigner.SwitchView
- VS.SharePointTools.RAD.featureDesigner.Manifest
- VS.SharePointTools.RAD.FeatureDesignerProperties
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, features
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 0604b6497920e1e6df0a792ce758519f425ac155
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99959944"
---
# <a name="how-to-customize-a-sharepoint-feature"></a>如何：自訂 SharePoint 功能
  您可以使用 Visual Studio 中的功能設計工具來建立和自訂 SharePoint 功能。 例如，您可以設定功能範圍，並將其他功能新增為相依性。 依預設，當您在方案總管或 SharePoint 套件瀏覽器中加入新功能時，會開啟功能設計工具。

## <a name="opening-the-feature-designer"></a>開啟功能設計工具
 您可以使用 [功能設計工具]，將 SharePoint 專案專案加入或移除功能。

#### <a name="to-open-the-feature-designer"></a>開啟功能設計工具

1. 在 **方案總管** 中，展開 [ **功能**]。

2. 按兩下 [ *Feature1* ] 專案，或開啟 [ *Feature1* ] 專案的快捷方式功能表，然後選擇 [ **視圖設計** 工具]。

## <a name="view-the-packaged-manifest-file"></a>查看已封裝的資訊清單檔案
 您可以使用 [功能設計工具] 來修改和產生功能 (*feature.xml*) 的封裝資訊清單檔。 然後，您可以在 Visual Studio 中查看此檔案的 XML 程式碼。

#### <a name="to-view-the-packaged-manifest-file"></a>若要查看封裝的資訊清單檔

1. 在 [ **功能設計** 工具] 中，選擇 [ **資訊清單** ] 索引標籤。

#### <a name="to-view-the-packaged-manifest-file-by-using-solution-explorer"></a>使用方案總管來查看封裝的資訊清單檔

1. 在 **方案總管** 中，選擇 [ **顯示所有** 檔案] 圖示。

2. 展開 [功能]，展開 [功能]，展開 [功能]，然後開啟 *\<FeatureName>.Template.xml* 檔案。

    > [!NOTE]
    > 當您開啟功能範本資訊清單 XML 檔案時，檔案會自動進行驗證，而且會忽略出現在 [錯誤清單] 視窗中的警告。

## <a name="change-the-manifest-template"></a>變更資訊清單範本
 您可以在 [Visual Studio XML 編輯器] 或 [資訊清單範本] 窗格中，變更功能資訊清單檔案的 XML 程式碼。 對 XML 程式碼所做的任何變更都會合並到功能的封裝資訊清單檔中。 例如，您可能會想要變更資訊清單範本以自訂功能屬性。

#### <a name="to-change-the-manifest-template-by-using-the-xml-editor"></a>使用 XML 編輯器變更資訊清單範本

1. 在 [ **功能設計** 工具] 中，選擇 [ **資訊清單** ] 索引標籤，展開 [ **編輯選項** ] 節點，然後選擇 [ **在 XML 編輯器中開啟** ] 連結。

     XML 的變更會合並到封裝的資訊清單檔案中。

#### <a name="to-change-the-manifest-template-by-using-the-manifest-template-pane"></a>使用資訊清單範本窗格變更資訊清單範本

1. 在 [ **功能設計** 工具] 中，選擇 [ **資訊清單** ] 索引標籤，展開 [ **編輯選項** ] 節點，然後變更 [資訊清單範本] 窗格中顯示的 XML。

     XML 的變更會出現在 [已 **封裝的資訊清單** ] 窗格的預覽中。

## <a name="overwrite-the-packaged-manifest-file"></a>覆寫封裝的資訊清單檔案
 您可以停用 [功能設計工具]，並手動建立 *feature.xml* 檔案。 當您第一次執行此程式時，功能設計工具中的目前設定會儲存至功能範本 XML 檔案。 然後，您可以修改或覆寫 XML 程式碼。

> [!NOTE]
> 如果您在功能設計工具停用時，于 XML 檔案中新增或移除 SharePoint 專案專案，則不會封裝這些專案專案。

#### <a name="to-overwrite-packaged-manifest-file-by-disabling-the-designer"></a>停用設計工具以覆寫封裝的資訊清單檔

1. 在 [ **功能設計** 工具] 中，選擇 [ **資訊清單** ] 索引標籤。

2. 展開 [ **編輯選項** ] 節點， **在 [XML 編輯器] 連結中選擇 [覆寫產生的 XML] 和 [編輯資訊清單** ]，然後選擇 [ **是]** 按鈕。

     範本會以目前封裝的資訊清單檔案進行更新。

## <a name="enable-the-feature-designer"></a>啟用功能設計工具
 您可以重新啟用功能設計工具來自訂 *feature.xml* 的檔案。

#### <a name="to-re-enable-the-designer"></a>重新啟用設計工具

1. 在 [ **功能設計** 工具] 中，選擇 [ **捨棄資訊清單編輯] 並重新啟用 [設計** 工具] 連結，然後選擇 [ **是]** 按鈕。

2. 範本會以原始文字重新整理，而 XML 的任何變更都會遺失。

## <a name="see-also"></a>另請參閱
- [封裝和部署 SharePoint 方案](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
