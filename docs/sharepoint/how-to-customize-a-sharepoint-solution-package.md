---
title: HOW TO：自訂 SharePoint 方案套件 |Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: 5e1c2e86f489191c3876154143706be4f9b0f1e4
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2019
ms.locfileid: "54874935"
---
# <a name="how-to-customize-a-sharepoint-solution-package"></a>HOW TO：自訂 SharePoint 方案套件
  您可以使用 封裝設計工具來建立和自訂套件 (*.wsp*)。 比方說，您可以新增 SharePoint 專案項目及功能，指定是否會重設部署方案時，Web 伺服器，以及設定部署伺服器類型。  
  
## <a name="open-the-package-designer"></a>開啟 封裝設計工具  
  
#### <a name="to-open-the-package-designer"></a>若要開啟 封裝設計工具
  
-   在**方案總管**，按兩下**封裝**，或選擇**檢視表設計工具**的捷徑功能表上**封裝**。  
  
## <a name="view-the-packaged-manifestffile"></a>檢視封裝的 manifestfFile  
 您可以使用 封裝設計工具修改和產生封裝資訊清單檔案。 然後，您也可以在 Visual Studio 中檢視此檔案的 XML 程式碼。  
  
#### <a name="to-view-the-xml-source-file"></a>若要檢視 XML 原始程式檔  
  
1.  在  **Package Designer**，選擇**資訊清單**。  
  
#### <a name="to-view-the-packaged-manifest-file-by-using-solution-explorer"></a>若要使用方案總管 中檢視封裝的資訊清單檔案  
  
1.  在 [方案總管] 中選擇 [顯示所有檔案]。  
  
2.  封裝展開，展開 封裝，並開啟*Package.Template.xml*檔案。  
  
    > [!NOTE]  
    >  當您開啟 [套件] 範本的資訊清單 XML 檔案時，檔案進行自動驗證，以及您可以略過警告出現在 [錯誤清單] 視窗中。  
  
## <a name="change-the-manifest-template"></a>變更資訊清單範本  
 您可以變更 Visual Studio XML 編輯器或 [資訊清單的範本] 窗格中的封裝資訊清單檔案的 XML 程式碼。 XML 程式碼的任何變更會合併到封裝的封裝資訊清單檔案。  
  
#### <a name="to-change-the-manifest-template-by-using-the-xml-editor"></a>若要使用 XML 編輯器中變更資訊清單範本  
  
1.  中**封裝設計工具**，選擇**資訊清單**索引標籤上，展開**編輯選項** 節點，然後選擇**XML 編輯器中開啟**連結。  
  
     Xml 的變更合併至封裝的資訊清單檔案。  
  
#### <a name="to-change-the-manifest-template-by-using-the-manifest-template-pane"></a>若要變更資訊清單範本資訊清單的範本 窗格  
  
1.  在 **封裝設計工具**，選擇**資訊清單**索引標籤上，展開**編輯選項**節點，然後再變更出現在 資訊清單的範本 窗格中的 XML。  
  
     Xml 的變更會出現在**預覽的封裝資訊清單**窗格。  
  
## <a name="overwrite-the-packaged-manifest-file"></a>覆寫封裝資訊清單檔案  
 您可以停用封裝設計工具，並建立*manifest.xml*手動檔案。 第一次您執行此程序，在封裝設計工具中的目前設定會儲存到封裝範本 XML 檔。 然後，您可以修改或覆寫 XML 程式碼。  
  
> [!NOTE]  
>  如果您新增或移除 SharePoint 專案項目和功能的 XML 檔案中停用封裝設計工具時，這些專案項目和功能不會封裝。  
  
#### <a name="to-overwrite-packaged-manifest-file-by-disabling-the-designer"></a>若要覆寫封裝資訊清單的檔案，藉由停用設計工具  
  
1.  在 [ **Package Designer**，選擇**資訊清單**] 索引標籤。  
  
2.  依序展開**編輯選項**節點，選擇**覆寫產生 XML 和編輯資訊清單 XML 編輯器中的**連結，然後選擇**是** 按鈕。  
  
     此範本會更新目前的封裝資訊清單檔案。  
  
## <a name="enable-the-package-designer"></a>啟用封裝設計工具  
 您可以重新啟動封裝設計工具來自訂*manifest.xml*檔案。  
  
#### <a name="to-re-enable-the-designer"></a>若要重新啟用設計工具  
  
1.  在 [**封裝設計工具**，選擇**捨棄資訊清單編輯和重新啟用設計工具**連結，然後選擇**是**] 按鈕。  
  
     範本會使用原始的文字、 重新整理，而且 XML 的任何變更都會遺失。  
  
## <a name="see-also"></a>另請參閱
 [封裝和部署 SharePoint 方案](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
