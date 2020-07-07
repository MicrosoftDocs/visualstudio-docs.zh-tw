---
title: 如何：自訂 SharePoint 方案套件 |Microsoft Docs
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- VS.SharePointTools.RAD.PackageDesignerAdvanced
- VS.SharePointTools.RAD.PackageDesigner.Manifest
- VS.SharePointTools.RAD.PackageDesignerProperties
- VS.SharePointTools.RAD.PackageDesigner.SwitchView
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
ms.openlocfilehash: 77b66160d489f711b5588fdcdd024d13769d734f
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: zh-TW
ms.lasthandoff: 07/06/2020
ms.locfileid: "86016867"
---
# <a name="how-to-customize-a-sharepoint-solution-package"></a>如何：自訂 SharePoint 方案套件
  您可以使用封裝設計工具來建立和自訂封裝（*.wsp*）。 例如，您可以加入 SharePoint 專案專案和功能，指定是否要在部署方案時重設 Web 服務器，並設定部署伺服器類型。

## <a name="open-the-package-designer"></a>開啟封裝設計工具

#### <a name="to-open-the-package-designer"></a>若要開啟封裝設計工具

- 在**方案總管**中，按兩下 [**套件**]，或在 [**封裝**] 的快捷方式功能表上選擇 [**視圖設計**工具]。

## <a name="view-the-packaged-manifestffile"></a>觀看已封裝的 manifestfFile
 您可以使用封裝設計工具來修改和產生已封裝的資訊清單檔案。 然後，您可以在 Visual Studio 中，查看此檔案的 XML 程式碼。

#### <a name="to-view-the-xml-source-file"></a>若要查看 XML 原始檔

1. 在**封裝設計**工具中，選擇 [**資訊清單**]。

#### <a name="to-view-the-packaged-manifest-file-by-using-solution-explorer"></a>若要使用方案總管來查看已封裝的資訊清單檔

1. 在 [方案總管]**** 中選擇 [顯示所有檔案]****。

2. 展開 [封裝]，展開 [Package]，然後開啟*Package.Template.xml*檔案。

    > [!NOTE]
    > 當您開啟封裝範本的資訊清單 XML 檔案時，系統會自動驗證檔案，而且您可以忽略出現在錯誤清單視窗中的警告。

## <a name="change-the-manifest-template"></a>變更資訊清單範本
 您可以在 [Visual Studio XML 編輯器] 或 [資訊清單] 範本窗格中，變更已封裝之資訊清單檔案的 XML 程式碼。 對 XML 程式碼所做的任何變更都會合並到封裝的封裝資訊清單檔中。

#### <a name="to-change-the-manifest-template-by-using-the-xml-editor"></a>使用 XML 編輯器變更資訊清單範本

1. 在 [**封裝設計**工具] 中，選擇 [**資訊清單**] 索引標籤，展開 [**編輯選項**] 節點，然後選擇 [**在 XML 編輯器中開啟**] 連結。

     XML 的變更會合並到封裝的資訊清單檔中。

#### <a name="to-change-the-manifest-template-by-using-the-manifest-template-pane"></a>使用資訊清單範本窗格變更資訊清單範本

1. 在 [**封裝設計**工具] 中，選擇 [**資訊清單**] 索引標籤，展開 [**編輯選項**] 節點，然後變更出現在 [資訊清單] 範本窗格中的 XML。

     XML 的變更會出現在 [**封裝的資訊清單**] 窗格的預覽中。

## <a name="overwrite-the-packaged-manifest-file"></a>覆寫已封裝的資訊清單檔案
 您可以停用封裝設計工具，並手動建立*manifest.xml*檔案。 當您第一次執行此程式時，封裝設計工具中的目前設定會儲存至封裝範本 XML 檔案。 然後，您可以修改或覆寫 XML 程式碼。

> [!NOTE]
> 如果您在停用封裝設計工具時，于 XML 檔案中新增或移除 SharePoint 專案專案和功能，則不會封裝這些專案專案和功能。

#### <a name="to-overwrite-packaged-manifest-file-by-disabling-the-designer"></a>藉由停用設計工具來覆寫已封裝的資訊清單檔

1. 在**封裝設計**工具中，選擇 [**資訊清單**] 索引標籤。

2. 展開 [**編輯選項**] 節點，選擇 [xml 編輯器] 連結中的 [**覆寫產生的 XML] 和 [編輯資訊清單**]，然後選擇 [**是]** 按鈕。

     此範本會以目前已封裝的資訊清單檔案進行更新。

## <a name="enable-the-package-designer"></a>啟用封裝設計工具
 您可以重新啟用封裝設計工具，以自訂*manifest.xml*檔案。

#### <a name="to-re-enable-the-designer"></a>重新啟用設計工具

1. 在 [**封裝設計**工具] 中，選擇 [**捨棄資訊清單編輯] 並重新啟用 [設計**工具] 連結，然後選擇 [**是]** 按鈕。

     範本會以原始文字重新整理，而且對 XML 所做的任何變更都會遺失。

## <a name="see-also"></a>另請參閱
- [封裝和部署 SharePoint 方案](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
