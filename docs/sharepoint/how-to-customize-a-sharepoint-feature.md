---
title: HOW TO：自訂 SharePoint 功能 |Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.RAD.FeatureDesigner.SwitchView
- VS.SharePointTools.RAD.featureDesigner.Manifest
- VS.SharePointTools.RAD.FeatureDesignerProperties
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, features
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 15cb1b9527cb3a1e469d33a4125e1b410209d98f
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53835470"
---
# <a name="how-to-customize-a-sharepoint-feature"></a>HOW TO：自訂 SharePoint 功能
  您可以建立及使用 Visual Studio 中的功能設計工具自訂 SharePoint 功能。 比方說，您可以設定功能範圍，以及新增為相依性的其他功能。 根據預設，當您在方案總管 或 SharePoint 封裝總管 中新增的新功能時，會開啟功能設計工具。  
  
## <a name="opening-the-feature-designer"></a>開啟功能設計工具  
 您可以新增或移除 SharePoint 專案項目，以使用功能設計工具的功能。  
  
#### <a name="to-open-the-feature-designer"></a>若要開啟功能設計工具
  
1.  在 **方案總管**，展開**功能**。  
  
2.  按兩下*Feature1*項目，或開啟捷徑功能表*Feature1*項目，然後選擇**檢視表設計工具**。  
  
## <a name="view-the-packaged-manifest-file"></a>檢視封裝的資訊清單檔案  
 您可以使用功能設計工具修改和產生功能的封裝資訊清單檔案 (*feature.xml*)。 然後，您也可以在 Visual Studio 中檢視此檔案的 XML 程式碼。  
  
#### <a name="to-view-the-packaged-manifest-file"></a>若要檢視封裝的資訊清單檔案  
  
1.  在 [**功能設計工具**，選擇**資訊清單**] 索引標籤。  
  
#### <a name="to-view-the-packaged-manifest-file-by-using-solution-explorer"></a>若要使用方案總管 中檢視封裝的資訊清單檔案  
  
1.  在 **方案總管**，選擇**顯示所有檔案**圖示。  
  
2.  展開 [功能]、 展開 FeatureName、 展開 FeatureName.feature，然後再開啟 *\<FeatureName >。Template.xml*檔案。  
  
    > [!NOTE]  
    >  當您開啟了功能範本資訊清單的 XML 檔案時，檔案會自動進行驗證，並出現在 [錯誤清單] 視窗中出現的警告可以忽略。  
  
## <a name="change-the-manifest-template"></a>變更資訊清單範本  
 您可以變更 Visual Studio XML 編輯器或 [資訊清單的範本] 窗格中的功能資訊清單檔案的 XML 程式碼。 XML 程式碼的任何變更會合併到封裝的資訊清單檔案中，功能。 例如，您可能要變更資訊清單的範本，以自訂功能屬性。  
  
#### <a name="to-change-the-manifest-template-by-using-the-xml-editor"></a>若要使用 XML 編輯器中變更資訊清單範本  
  
1.  中**功能設計工具**，選擇**資訊清單**索引標籤上，展開**編輯選項** 節點，然後選擇**XML 編輯器中開啟**連結。  
  
     Xml 的變更合併至封裝的資訊清單檔案。  
  
#### <a name="to-change-the-manifest-template-by-using-the-manifest-template-pane"></a>若要變更資訊清單範本資訊清單的範本 窗格  
  
1.  在 **功能設計工具**，選擇**資訊清單**索引標籤上，展開**編輯選項**節點，然後再變更出現在 資訊清單的範本 窗格中的 XML。  
  
     Xml 的變更會出現在**預覽的封裝資訊清單**窗格。  
  
## <a name="overwrite-the-packaged-manifest-file"></a>覆寫封裝資訊清單檔案  
 您可以停用功能設計工具，並建立*feature.xml*手動檔案。 第一次您執行此程序，在功能設計工具中目前的設定會儲存到功能的範本 XML 檔。 然後，您可以修改或覆寫 XML 程式碼。  
  
> [!NOTE]  
>  如果您新增或移除 SharePoint 專案項目 XML 檔案中，停用功能設計工具時，這些專案項目不會封裝。  
  
#### <a name="to-overwrite-packaged-manifest-file-by-disabling-the-designer"></a>若要覆寫封裝資訊清單的檔案，藉由停用設計工具  
  
1.  在 [**功能設計工具**，選擇**資訊清單**] 索引標籤。  
  
2.  依序展開**編輯選項**節點，選擇**覆寫產生 XML 和編輯資訊清單 XML 編輯器中的**連結，然後選擇**是** 按鈕。  
  
     此範本會更新目前的封裝資訊清單檔案。  
  
## <a name="enable-the-feature-designer"></a>啟用功能設計工具  
 您可以重新啟用功能設計工具來自訂*feature.xml*檔案。  
  
#### <a name="to-re-enable-the-designer"></a>若要重新啟用設計工具  
  
1.  在 [**功能設計工具**，選擇**捨棄資訊清單編輯和重新啟用設計工具**連結，然後選擇**是**] 按鈕。  
  
2.  範本會使用原始的文字、 重新整理，而且 XML 的任何變更都會遺失。  
  
## <a name="see-also"></a>另請參閱
 [封裝和部署 SharePoint 方案](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
