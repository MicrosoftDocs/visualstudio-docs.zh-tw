---
title: "VSIX 資訊清單設計工具 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.Sdk.VsixManifestEditor
helpviewer_keywords:
- vsixmanifest
- vsix manifest
- manifest designer
ms.assetid: 5a691e77-cf91-430d-90ea-361d9031ef83
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 0d7af3ab109c922a8182a93db6852a331229ceca
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="vsix-manifest-designer"></a>VSIX 資訊清單設計工具
修改 VSIX 封裝資訊清單檔案設定 Visual Studio 擴充功能的安裝行為。  
  
 **VSIX 資訊清單設計工具**對應至基礎 VSIX 結構描述。 在設計工具中使用對應的控制項，可以設定每個結構描述中的項目。 如需結構描述的詳細資訊，請參閱[VSIX 延伸結構描述 2.0 參照](../extensibility/vsix-extension-schema-2-0-reference.md)。  
  
 若要開啟**VSIX 資訊清單設計工具**，找出 source.extension.vsixmanifest 檔案中的**方案總管 中**，並開啟檔案。 如果檔案未包含有效的 XML，不會開啟資訊清單設計工具。  
  
> [!NOTE]
>  Source.extension.vsixmanifest 建置套件時 extension.vsixmanifest 的輸出。  
  
## <a name="uielement-list"></a>UIElement 清單  
 **VSIX 資訊清單設計工具**包含對應至這些結構描述的最上層元素的四個區段：  
  
-   中繼資料  
  
-   安裝目標  
  
-   資產  
  
-   相依性  
  
 [標題] 區域包含下列控制項。  
  
 **產品名稱**  
 描述擴充功能名稱。  
  
 **產品識別碼**  
 指定此套件的唯一識別資訊。  
  
 **作者**  
 指定延伸模組的作者名稱。  
  
 **版本**  
 指定延伸模組的版本號碼。  
  
 **中繼資料** 索引標籤包含下列控制項。  
  
 **描述**  
 提供的擴充功能，在中顯示的文字描述**擴充管理員**。  
  
 **Language**  
 指定的預設語言套件，對應到資訊清單中的文字資料。 `Language`屬性會遵循 common language runtime (CLR) 地區設定程式碼慣例資源組件，例如，en-us-我們、 en-us、 為 fr-fr。 根據預設，此值是中性;這表示此封裝將在 Visual Studio 的任何語言版本上執行。  
  
 **授權**  
 指定的文字檔案，其中包含使用者授權合約中，如果有的話。  
  
 **圖示**  
 指定包含要顯示在圖示的圖形檔案 （.png、.bmp、.jpeg、.ico）**擴充管理員**，如果圖示。 圖示影像必須是 32 x 32 像素，或將這些維度調整大小。 如果未不指定任何圖示，**擴充管理員**會使用預設圖示。  
  
 **預覽影像**  
 指定包含要顯示在預覽影像的圖形檔案 （.png、.bmp、.jpeg、.ico）**擴充管理員**、 預覽影像是否存在。 預覽影像必須是 200 x 200 像素為單位。 如果指定沒有預覽影像，則**擴充管理員**會使用預設映像。  
  
 **標記**  
 新增要用於搜尋提示的文字標籤。  
  
 **版本資訊**  
 指定包含版本資訊的檔案 （.txt、.rtf）。 也會顯示版本資訊的網站 URL。  
  
 **使用者入門指南**  
 指定包含如何使用 VSIX 封裝中的擴充功能或內容的相關資訊的檔案 （.txt、.rtf）。 擴充功能安裝完成時，就會顯示本指南。 也會顯示快速入門的網站 URL。  
  
 **詳細資訊的 URL**  
 指定包含產品的其他資訊的網站 URL。  
  
 **安裝目標** 索引標籤包含下列控制項。  
  
 **安裝類型**  
 列出**Visual Studio 擴充功能**和**擴充功能 SDK**目標安裝類型。 選項會因您所選擇的類型而有所不同。  
  
 **Visual Studio 擴充功能**  
 列出**InstallationTarget**描述如何安裝此套件及到哪些 Visual Studio 產品中，您可以安裝此擴充功能的項目。 每項產品是個別識別名稱的版本或版本範圍。  可以加入至清單、 修改和刪除產品。 名稱和產品的版本對應至**識別碼**和**版本**屬性相關聯的**InstallationTarget**項目。  
  
 **版本範圍**是 [12.0，14.0]，並使用下列標記法：  
  
-   [-最小版本 （含）  
  
-   ]-（含） 的最大版本  
  
-   (-獨佔的最小版本  
  
-   )-獨佔的最大版本  
  
-   單一版本 #-指定的版本  
  
 **擴充功能 SDK**  
 指定不只限於特定的產品和版本的全域安裝。 **目標平台識別項**是平台，例如"Windows"，您的目標。 **平台版本為目標**是版本，例如 8.0、 的目標平台。 **SDK 名稱**和**SDK 版本**分別為名稱和 SDK 的版本號碼。  
  
 **針對所有使用者安裝此 VSIX （需要提高權限安裝）**核取方塊  
 如果選取此核取方塊，為所有使用者; 安裝此擴充功能否則，它會安裝僅針對目前的使用者。  
  
 **Windows Installer 會安裝此 VSIX**核取方塊  
 如果選取此核取方塊，這項擴充功能已安裝 Windows installer （.msi 檔案）;否則，它會安裝為一般的 VSIX 封裝 （.vsix 檔案）。  
  
 **資產** 索引標籤包含下列控制項。  
  
 **列出的資產清單**  
 列出資產項目描述的擴充功能或內容的項目，此封裝的介面。 每個擴充功能或內容項目會個別列出由來源、 類型和路徑。 可以加入至清單、 修改和刪除擴充功能和內容項目。 類型和擴充功能或內容項目的路徑對應至`Type`和`Path`屬性相關聯的`Asset`項目。 已知下列類型：  
  
-   Microsoft.VisualStudio.Package  
  
-   Microsoft.VisualStudio.MefComponent  
  
-   Microsoft.VisualStudio.ToolboxControl  
  
-   Microsoft.VisualStudio.Samples  
  
-   Microsoft.VisualStudio.ProjectTemplate  
  
-   Microsoft.VisualStudio.ItemTemplate  
  
-   Microsoft.VisualStudio.Assembly  
  
-   Microsoft.ExtensionSDK  
  
 要新增或編輯資產，您必須指定資產型別是否資產目前方案中的專案或檔案在檔案系統和專案的名稱。 您也可以指定要在其中內嵌資料夾的名稱。  
  
 您也可以建立自己的型別，並提供他們唯一的名稱。  
  
 **相依性** 索引標籤包含下列控制項。  
  
 **名稱、 來源和版本範圍**  
 相依性項目列出的這個封裝，也就是此封裝相依於其他封裝。 如果指定的相依性套件，則它必須先安裝此套件已安裝;否則，此套件必須安裝它。  
  
 指定相依性套件的識別碼、 名稱、 版本範圍、 來源和解析的相依性的方式。 每個相依性封裝會個別列出，依名稱、 版本，以及來源。 相依性套件可以新增至清單、 修改和刪除。  
  
 識別碼必須相符`ID`的相依性套件中繼資料屬性。 來源可以是目前的方案、 目前已安裝的擴充功能或檔案中的專案。 **的相依性解析方式**設定可以是巢狀的封裝相對路徑或相依性的下載位置的 URL。 識別碼、 版本和相依性套件的解析度對應至`Id`， `Version`，和`Location`屬性相關聯的`Dependency`項目。  
  
## <a name="see-also"></a>請參閱  
 [VSIX 擴充功能 2.0 結構描述參考](../extensibility/vsix-extension-schema-2-0-reference.md)   
 [VSIX 封裝的結構](../extensibility/anatomy-of-a-vsix-package.md)