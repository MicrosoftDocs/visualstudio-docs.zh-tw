---
title: "如何： 自訂 SharePoint 方案套件 |Microsoft 文件"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.SharePointTools.RAD.PackageDesignerAdvanced
- VS.SharePointTools.RAD.PackageDesigner.Manifest
- VS.SharePointTools.RAD.PackageDesignerProperties
- VS.SharePointTools.RAD.PackageDesigner.SwitchView
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords: SharePoint development in Visual Studio, packages
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 277ceea1b908c5819608a1bdf1d6be97c2f6ce77
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-customize-a-sharepoint-solution-package"></a>如何：自訂 SharePoint 方案套件
  您可以使用封裝設計工具建立和自訂套件 (.wsp)。 例如，您可以加入 SharePoint 專案項目和功能、 指定 Web 伺服器重設部署方案時，以及設定部署伺服器類型。  
  
## <a name="opening-the-package-designer"></a>開啟 封裝設計工具  
  
#### <a name="to-open-the-package-designer"></a>若要開啟 封裝設計工具  
  
-   在**方案總管 中**，連按兩下**封裝**，或選擇**檢視表設計工具**的捷徑功能表上**封裝**。  
  
## <a name="viewing-the-packaged-manifest-file"></a>檢視封裝資訊清單檔案  
 您可以使用封裝設計工具來修改並產生封裝資訊清單檔案。 然後，您可以在 Visual Studio 中檢視此檔案的 XML 程式碼。  
  
#### <a name="to-view-the-xml-source-file"></a>若要檢視 XML 來源檔案  
  
1.  在**封裝設計工具**，選擇**資訊清單**。  
  
#### <a name="to-view-the-packaged-manifest-file-by-using-solution-explorer"></a>若要使用方案總管 中檢視封裝資訊清單檔案  
  
1.  在**方案總管 中**，選擇**顯示所有檔案**。  
  
2.  擴充封裝中，依序展開，然後開啟 Package.Template.xml 檔案。  
  
    > [!NOTE]  
    >  當您開啟封裝範本的資訊清單 XML 檔案時，檔案會自動進行驗證，以及您可以忽略 [錯誤清單] 視窗中出現的警告。  
  
## <a name="changing-the-manifest-template"></a>變更資訊清單範本  
 您可以變更 Visual Studio XML 編輯器或 [資訊清單範本] 窗格中的封裝資訊清單檔案的 XML 程式碼。 XML 程式碼的任何變更會合併到封裝的封裝資訊清單檔。  
  
#### <a name="to-change-the-manifest-template-by-using-the-xml-editor"></a>若要使用 XML 編輯器來變更資訊清單範本  
  
1.  在**封裝設計工具**，選擇**資訊清單**索引標籤上，依序展開**編輯選項**] 節點，然後選擇 [ **XML 編輯器中開啟**連結。  
  
     Xml 的變更會合併到封裝資訊清單檔案。  
  
#### <a name="to-change-the-manifest-template-by-using-the-manifest-template-pane"></a>若要使用資訊清單範本 窗格來變更資訊清單範本  
  
1.  在**封裝設計工具**，選擇**資訊清單**索引標籤上，依序展開**編輯選項**節點，然後再變更顯示在資訊清單範本 窗格中的 XML。  
  
     Xml 的變更會出現在**預覽的封裝資訊清單**窗格。  
  
## <a name="overwriting-the-packaged-manifest-file"></a>覆寫封裝資訊清單檔案  
 您可以停用封裝設計工具，然後手動建立 manifest.xml 檔案。 第一次您執行此程序，在封裝設計工具中的目前設定會儲存至封裝範本 XML 檔。 然後，您可以修改或覆寫的 XML 程式碼。  
  
> [!NOTE]  
>  如果您新增或移除 SharePoint 專案項目和功能的 XML 檔案中停用封裝設計工具時，這些專案項目和功能不被封裝。  
  
#### <a name="to-overwrite-packaged-manifest-file-by-disabling-the-designer"></a>若要停用設計工具覆寫封裝的資訊清單檔案  
  
1.  在**封裝設計工具**，選擇**資訊清單** 索引標籤。  
  
2.  。  
  
3.  展開**編輯選項** 節點，選擇**覆寫產生的 XML 和編輯資訊清單 XML 編輯器中**連結，，然後選擇 **是** 按鈕。  
  
     此範本會使用目前的封裝資訊清單檔案更新。  
  
## <a name="enabling-the-package-designer"></a>啟用封裝設計工具  
 您可以重新啟用自訂 manifest.xml 檔封裝設計工具。  
  
#### <a name="to-re-enable-the-designer"></a>若要重新啟用設計工具  
  
1.  在**封裝設計工具**，選擇**捨棄資訊清單的編輯和重新啟用設計工具**連結，，然後選擇 [**是**] 按鈕。  
  
     範本會以原始的文字，重新整理，而且 XML 的任何變更都會遺失。  
  
## <a name="see-also"></a>請參閱  
 [封裝和部署 SharePoint 方案](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  