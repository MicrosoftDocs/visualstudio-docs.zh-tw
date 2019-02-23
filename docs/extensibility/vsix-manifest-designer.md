---
title: VSIX 資訊清單設計工具 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VS.Sdk.VsixManifestEditor
helpviewer_keywords:
- vsixmanifest
- vsix manifest
- manifest designer
ms.assetid: 5a691e77-cf91-430d-90ea-361d9031ef83
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 85b9d20dd67ff11f5bded7060440f2e768a205a9
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2019
ms.locfileid: "56722859"
---
# <a name="vsix-manifest-designer"></a>VSIX 資訊清單設計工具
修改 VSIX 封裝資訊清單檔，它會設定 Visual Studio 擴充功能的安裝行為。

 **VSIX 資訊清單設計工具**對應至基礎 VSIX 結構描述。 使用對應的控制項設計工具中，可以設定結構描述中的每個項目。 如需有關結構描述的詳細資訊，請參閱[VSIX 延伸結構描述 2.0 參考](../extensibility/vsix-extension-schema-2-0-reference.md)。

 若要開啟 [ **VSIX 資訊清單設計工具**，找出*source.extension.vsixmanifest*中的檔案**方案總管] 中**，並開啟檔案。 如果檔案不包含有效的 XML，將不會開啟資訊清單設計工具。

> [!NOTE]
>  *Source.extension.vsixmanifest*檔案輸出至*extension.vsixmanifest*建置封裝時。

## <a name="uielement-list"></a>UIElement 清單
 **VSIX 資訊清單設計工具**包含對應至結構描述的下列最上層元素的四個區段：

- 中繼資料

- 安裝目標

- 資產

- 相依性

  [標題] 區域包含下列控制項。

  **產品名稱**描述擴充功能名稱。

  **產品識別碼**指定此套件的唯一識別資訊。

  **作者**指定延伸模組的作者名稱。

  **版本**指定延伸模組的版本號碼。

  **中繼資料** 索引標籤包含下列控制項。

  **描述**提供的延伸模組，在要顯示的文字描述**延伸模組管理員**。

  **語言**指定套件，其對應至資訊清單中的文字資料的預設語言。 `Language`屬性會遵循 common language runtime (CLR) 地區設定程式碼慣例，資源組件，例如，en-us-我們、 en、 fr-fr。 根據預設，值為中性，這表示此封裝將所有語言版本的 Visual Studio 上執行。

  **授權**指定文字檔案，其中包含使用者授權合約中，如果有的話。

  **圖示**指定的圖形檔 (*.png*， *.bmp*， *.jpeg*， *.ico*)，其中包含要在中顯示的圖示**延伸模組管理員**，如果圖示。 圖示影像必須是 32 x 32 像素，或調整大小的維度。 如果指定的圖示，則**延伸模組管理員**會使用預設圖示。

  **預覽影像**指定的圖形檔 (*.png*， *.bmp*， *.jpeg*， *.ico*) 包含的預覽影像顯示在**延伸模組管理員**、 預覽影像是否存在。 預覽影像必須是 200 x 200 像素為單位。 如果指定沒有預覽影像，則**延伸模組管理員**會使用預設映像。

  **標記**新增要用於搜尋提示的文字標籤。

  **版本資訊**指定的檔案 (*.txt*， *.rtf*)，包含版本資訊。 也會顯示版本資訊的網站 URL。

  **開始使用手冊**指定的檔案 (*.txt*， *.rtf*)，其中包含如何使用 VSIX 封裝中的 擴充功能或內容的相關資訊。 擴充功能安裝完成時，會顯示本指南。 也會顯示快速入門的網站 URL。

  **詳細資訊 URL**指定包含產品的其他資訊的網站 URL。

  **安裝目標** 索引標籤包含下列控制項。

  **安裝的型別**列出**Visual Studio 擴充功能**並**延伸模組 SDK**目標安裝類型。 選項會因您所選擇的類型而有所不同。

  **Visual Studio 擴充功能**列出**InstallationTarget**說明如何安裝此套件，並到哪一個 Visual Studio 產品中，您可以安裝此擴充功能的項目。 名稱和版本或版本範圍會分別識別每項產品。 產品可以新增至清單、 修改和刪除。 名稱和產品的版本對應至**識別碼**並**版本**相關聯的屬性**InstallationTarget**項目。

  **版本範圍**是 [12.0，14.0]，並使用下列標記法：

- [-最低版本內含

- ]-最高版本 （含）

- (-獨佔的最低版本

- )-獨佔的最大版本

- 單一版本 #-指定的版本

  **擴充功能 SDK**指定不限於特定產品和版本的全域安裝。 **目標平台識別項**是平台，例如"Windows"設為目標。 **目標平台版本**是版本，例如 8.0 的目標平台。 **SDK 名稱**並**SDK 版本**分別為名稱和 SDK 的版本號碼。

  **針對所有使用者安裝此 VSIX （需要提高權限安裝）** 如果您選取此核取方塊，為所有使用者安裝的擴充功能; 它只針對目前使用者的安裝，否則為。

  **Windows 安裝程式會安裝此 VSIX**如果您選取此核取方塊時，Windows 安裝程式所安裝的擴充功能 (*.msi*檔案)，否則它會安裝為一般的 VSIX 套件 (*.vsix*檔案)。

  **資產** 索引標籤包含下列控制項。

  **列出的資產清單**列出資產項目描述的擴充功能或內容的項目，這個封裝的介面。 每個擴充功能或內容項目，則是依來源、 類型和路徑分別列出。 擴充功能和內容的項目可以加入至清單、 修改和刪除。 型別和擴充功能或內容項目的路徑對應至`Type`並`Path`相關聯的屬性`Asset`項目。 已知下列類型：

- Microsoft.VisualStudio.Package

- Microsoft.VisualStudio.MefComponent

- Microsoft.VisualStudio.ToolboxControl

- Microsoft.VisualStudio.Samples

- Microsoft.VisualStudio.ProjectTemplate

- Microsoft.VisualStudio.ItemTemplate

- Microsoft.VisualStudio.Assembly

- Microsoft.ExtensionSDK

  若要新增或編輯資產中,，您必須指定資產類型，不論資產是目前方案中的專案或檔案在檔案系統和專案的名稱。 您也可以指定要在其中內嵌資料夾的名稱。

  您也可以建立自己的型別，並且給予它們唯一的名稱。

  **相依性** 索引標籤包含下列控制項。

  **名稱、 來源和版本範圍**列出的相依性元素的這個封裝，也就是此封裝相依於其他封裝。 如果指定的相依性套件，則它必須先安裝此套件已安裝;否則，此套件必須安裝它。

  識別項、 名稱、 版本範圍、 來源和解析的相依性有何所指定相依性套件。 每個相依性封裝會分別列，依名稱、 版本和原始檔。 相依性套件可以新增至清單、 修改和刪除。

  識別項必須符合`ID`的相依性套件中繼資料的屬性。 來源可以是目前的方案、 目前已安裝的延伸模組或檔案中的專案。 **解析的相依性有何**設定可以是巢狀的封裝相對路徑或相依性的下載位置的 URL。 識別碼、 版本和相依性套件的解決方式對應至`Id`， `Version`，並`Location`相關聯的屬性`Dependency`項目。

## <a name="see-also"></a>另請參閱
- [VSIX 延伸結構描述 2.0 參考](../extensibility/vsix-extension-schema-2-0-reference.md)
- [VSIX 封裝的結構](../extensibility/anatomy-of-a-vsix-package.md)