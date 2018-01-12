---
title: "如何： 自訂 SharePoint 功能 |Microsoft 文件"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.SharePointTools.RAD.FeatureDesigner.SwitchView
- VS.SharePointTools.RAD.featureDesigner.Manifest
- VS.SharePointTools.RAD.FeatureDesignerProperties
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords: SharePoint development in Visual Studio, features
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: adb4283a56715da704df8991543ea89c6cbc79a4
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-customize-a-sharepoint-feature"></a>如何：自訂 SharePoint 功能
  您可以建立和使用功能設計工具，Visual Studio 中自訂 SharePoint 功能。 例如，您可以設定功能範圍，以及做為相依性加入其他功能。 根據預設，當您將新功能加入方案總管 或 SharePoint 封裝總管 中，會開啟功能設計工具。  
  
## <a name="opening-the-feature-designer"></a>開啟功能設計工具  
 您可以新增或移除 SharePoint 專案項目，使用功能設計工具的一項功能。  
  
#### <a name="to-open-the-feature-designer"></a>若要開啟功能設計工具  
  
1.  在**方案總管 中**，依序展開**功能**。  
  
2.  按兩下*Feature1*項目，或開啟捷徑功能表*Feature1*項目，然後選擇 **檢視表設計工具**。  
  
## <a name="viewing-the-packaged-manifest-file"></a>檢視封裝資訊清單檔案  
 若要修改，並產生封裝資訊清單檔案 （這個） 功能，您可以使用功能設計工具。 然後，您可以在 Visual Studio 中檢視此檔案的 XML 程式碼。  
  
#### <a name="to-view-the-packaged-manifest-file"></a>若要檢視封裝資訊清單檔案  
  
1.  在**功能設計工具**，選擇**資訊清單** 索引標籤。  
  
#### <a name="to-view-the-packaged-manifest-file-by-using-solution-explorer"></a>若要使用方案總管 中檢視封裝資訊清單檔案  
  
1.  在**方案總管 中**，選擇**顯示所有檔案**圖示。  
  
2.  展開 [功能]，展開 FeatureName、 展開 FeatureName.feature，並開啟*FeatureName*。Template.xml 檔案。  
  
    > [!NOTE]  
    >  當您開啟了功能範本資訊清單 XML 檔案時，檔案會自動進行驗證，您可以忽略 [錯誤清單] 視窗中出現的警告。  
  
## <a name="changing-the-manifest-template"></a>變更資訊清單範本  
 您可以變更 Visual Studio XML 編輯器或 [資訊清單範本] 窗格中的功能資訊清單檔案的 XML 程式碼。 XML 程式碼的任何變更併入封裝資訊清單檔案中，功能。 例如，您可能要變更的資訊清單範本來自訂功能屬性。  
  
#### <a name="to-change-the-manifest-template-by-using-the-xml-editor"></a>若要使用 XML 編輯器來變更資訊清單範本  
  
1.  在**功能設計工具**，選擇**資訊清單**索引標籤上，依序展開**編輯選項**] 節點，然後選擇 [ **XML 編輯器中開啟**連結。  
  
     Xml 的變更會合併到封裝資訊清單檔案。  
  
#### <a name="to-change-the-manifest-template-by-using-the-manifest-template-pane"></a>若要使用資訊清單範本 窗格來變更資訊清單範本  
  
1.  在**功能設計工具**，選擇**資訊清單**索引標籤上，依序展開**編輯選項**節點，然後再變更顯示在資訊清單範本 窗格中的 XML。  
  
     Xml 的變更會出現在**預覽的封裝資訊清單**窗格。  
  
## <a name="overwriting-the-packaged-manifest-file"></a>覆寫封裝資訊清單檔案  
 您可以停用功能設計工具，並手動建立這個檔案。 第一次您執行此程序中，功能設計工具中的目前設定會儲存到功能的範本 XML 檔。 然後，您可以修改或覆寫的 XML 程式碼。  
  
> [!NOTE]  
>  如果您新增或移除 SharePoint 專案項目 XML 檔案中，停用功能設計工具時，則不會封裝這些專案項目。  
  
#### <a name="to-overwrite-packaged-manifest-file-by-disabling-the-designer"></a>若要停用設計工具覆寫封裝的資訊清單檔案  
  
1.  在**功能設計工具**，選擇**資訊清單** 索引標籤。  
  
2.  展開**編輯選項** 節點，選擇**覆寫產生的 XML 和編輯資訊清單 XML 編輯器中**連結，，然後選擇 **是** 按鈕。  
  
     此範本會使用目前的封裝資訊清單檔案更新。  
  
## <a name="enabling-the-feature-designer"></a>啟用功能設計工具  
 您可以重新啟用功能設計工具來自訂這個檔案。  
  
#### <a name="to-re-enable-the-designer"></a>若要重新啟用設計工具  
  
1.  在**功能設計工具**，選擇**捨棄資訊清單的編輯和重新啟用設計工具**連結，，然後選擇 [**是**] 按鈕。  
  
2.  範本會以原始的文字，重新整理，而且 XML 的任何變更都會遺失。  
  
## <a name="see-also"></a>請參閱  
 [封裝和部署 SharePoint 方案](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  