---
title: 如何：自訂 SharePoint 功能 |Microsoft Docs
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a330f3c4cbe1e410ddc6a1612796c92eeda281b8
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: zh-TW
ms.lasthandoff: 07/06/2020
ms.locfileid: "86016892"
---
# <a name="how-to-customize-a-sharepoint-feature"></a>如何：自訂 SharePoint 功能
  您可以使用 Visual Studio 中的功能設計工具來建立和自訂 SharePoint 功能。 例如，您可以設定功能範圍，並將其他功能新增為相依性。 根據預設，當您在方案總管或 SharePoint 封裝瀏覽器中加入新功能時，就會開啟功能設計工具。

## <a name="opening-the-feature-designer"></a>開啟功能設計工具
 您可以使用功能設計工具，在功能中加入或移除 SharePoint 專案專案。

#### <a name="to-open-the-feature-designer"></a>若要開啟功能設計工具

1. 在**方案總管**中，展開 [**功能**]。

2. 按兩下 [ *Feature1* ] 專案，或開啟*Feature1*專案的快捷方式功能表，然後選擇 [**視圖設計**工具]。

## <a name="view-the-packaged-manifest-file"></a>查看已封裝的資訊清單檔案
 您可以使用 [功能設計工具] 來修改和產生功能的封裝資訊清單檔（*feature.xml*）。 然後，您可以在 Visual Studio 中，查看此檔案的 XML 程式碼。

#### <a name="to-view-the-packaged-manifest-file"></a>若要查看已封裝的資訊清單檔案

1. 在 [**功能設計**工具] 中，選擇 [**資訊清單**] 索引標籤。

#### <a name="to-view-the-packaged-manifest-file-by-using-solution-explorer"></a>若要使用方案總管來查看已封裝的資訊清單檔

1. 在**方案總管**中，選擇 [**顯示所有**檔案] 圖示。

2. 依序展開 [功能]、[功能]、[功能]，然後開啟* \<FeatureName>.Template.xml*檔案。

    > [!NOTE]
    > 當您開啟功能範本資訊清單 XML 檔案時，系統會自動驗證檔案，而且可以忽略出現在錯誤清單視窗中的警告。

## <a name="change-the-manifest-template"></a>變更資訊清單範本
 您可以在 [Visual Studio XML 編輯器] 或 [資訊清單] 範本窗格中，變更功能資訊清單檔案的 XML 程式碼。 對 XML 程式碼所做的任何變更都會合並到功能的封裝資訊清單檔中。 例如，您可能會想要變更資訊清單範本，以自訂功能屬性。

#### <a name="to-change-the-manifest-template-by-using-the-xml-editor"></a>使用 XML 編輯器變更資訊清單範本

1. 在 [**功能設計**工具] 中，選擇 [**資訊清單**] 索引標籤，展開 [**編輯選項**] 節點，然後選擇 [**在 XML 編輯器中開啟**] 連結。

     XML 的變更會合並到封裝的資訊清單檔中。

#### <a name="to-change-the-manifest-template-by-using-the-manifest-template-pane"></a>使用資訊清單範本窗格變更資訊清單範本

1. 在 [**功能設計**工具] 中，選擇 [**資訊清單**] 索引標籤，展開 [**編輯選項**] 節點，然後變更出現在 [資訊清單] 範本窗格中的 XML。

     XML 的變更會出現在 [**封裝的資訊清單**] 窗格的預覽中。

## <a name="overwrite-the-packaged-manifest-file"></a>覆寫已封裝的資訊清單檔案
 您可以停用 [功能設計工具]，並手動建立*feature.xml*檔案。 當您第一次執行此程式時，功能設計工具中的目前設定會儲存至功能範本 XML 檔案。 然後，您可以修改或覆寫 XML 程式碼。

> [!NOTE]
> 如果您在停用功能設計工具時，加入或移除 XML 檔案中的 SharePoint 專案專案，則不會封裝這些專案專案。

#### <a name="to-overwrite-packaged-manifest-file-by-disabling-the-designer"></a>藉由停用設計工具來覆寫已封裝的資訊清單檔

1. 在 [**功能設計**工具] 中，選擇 [**資訊清單**] 索引標籤。

2. 展開 [**編輯選項**] 節點，選擇 [xml 編輯器] 連結中的 [**覆寫產生的 XML] 和 [編輯資訊清單**]，然後選擇 [**是]** 按鈕。

     此範本會以目前已封裝的資訊清單檔案進行更新。

## <a name="enable-the-feature-designer"></a>啟用功能設計工具
 您可以重新啟用 [功能設計工具] 來自訂*feature.xml*檔案。

#### <a name="to-re-enable-the-designer"></a>重新啟用設計工具

1. 在 [**功能設計**工具] 中，選擇 [**捨棄資訊清單編輯] 並重新啟用 [設計**工具] 連結，然後選擇 [**是]** 按鈕。

2. 範本會以原始文字重新整理，而且對 XML 所做的任何變更都會遺失。

## <a name="see-also"></a>另請參閱
- [封裝和部署 SharePoint 方案](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
