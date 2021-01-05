---
title: VSIX 資訊清單設計工具 |Microsoft Docs
description: 瞭解 VSIX 資訊清單設計工具如何修改 VSIX 套件資訊清單檔，此檔案會設定 Visual Studio 擴充功能的安裝行為。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VS.Sdk.VsixManifestEditor
helpviewer_keywords:
- vsixmanifest
- vsix manifest
- manifest designer
ms.assetid: 5a691e77-cf91-430d-90ea-361d9031ef83
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6323b4330279848bc0453bdc7413904e2582d13a
ms.sourcegitcommit: dd96a95d87a039525aac86abe689c30e2073ae87
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/04/2021
ms.locfileid: "97863967"
---
# <a name="vsix-manifest-designer"></a>VSIX 資訊清單設計工具
修改 VSIX 套件資訊清單檔，此檔案會設定 Visual Studio 擴充功能的安裝行為。

 **Vsix 資訊清單設計** 工具會對應到基礎 VSIX 架構。 您可以使用設計工具中的對應控制項來設定架構中的每個元素。 如需架構的詳細資訊，請參閱 [VSIX 延伸架構2.0 參考](../extensibility/vsix-extension-schema-2-0-reference.md)。

 若要開啟 **VSIX 資訊清單設計** 工具，請在 **方案總管** 中找出 *extension.vsixmanifest* 檔案，然後開啟檔案。 如果檔案不包含有效的 XML，資訊清單設計工具就不會開啟。

> [!NOTE]
> *Extension.vsixmanifest* 檔案會在建立封裝時輸出至 *extension.vsixmanifest* 。

## <a name="uielement-list"></a>UIElement 清單
 **VSIX 資訊清單設計** 工具組含四個對應至架構之最上層元素的區段：

- 中繼資料

- 安裝目標

- Assets

- 相依性

  標題區域包含下列控制項。

  **產品名稱** 描述延伸模組名稱。

  **產品識別碼** 指定此封裝的唯一識別資訊。

  **作者** 指定擴充功能的作者名稱。

  **版本** 指定擴充功能的版本號碼。

  [ **中繼資料** ] 索引標籤包含下列控制項。

  **描述** 提供要在 [ **擴充管理員**] 中顯示之延伸模組的文字描述。

  **語言** 指定封裝的預設語言，這會對應到資訊清單中的文字資料。 `Language`屬性會遵循通用語言執行時間， (CLR) 適用于資源元件的地區設定程式碼慣例，例如 en-us、en、fr。 根據預設，這個值是中性的，這表示封裝將會在 Visual Studio 的任何語言版本上執行。

  **授權** 指定包含使用者授權（如果有的話）的文字檔。

  **圖示** 指定圖形檔案 (*.png*、 *.bmp*、 *jpeg*、 *.ico*) ，其中包含要在 [ **擴充管理員**] 中顯示的圖示（如果有圖示的話）。 圖示影像必須為32x32 圖元，否則會調整大小為這些維度。 如果未指定圖示， **延伸模組管理員** 會使用預設圖示。

  **預覽影像** 指定圖形檔案 (*.png*、 *.bmp*、 *jpeg*、 *.ico*) ，其中包含要在 [ **擴充管理員**] 中顯示的預覽影像（如果有預覽影像）。 預覽映射必須是200x200 圖元。 如果未指定預覽影像， **擴充管理員** 會使用預設映射。

  **標記** 新增要用於搜尋提示的文字標記。

  **版本** 資訊指定包含版本資訊 (*.txt*、 *.rtf*) 的檔案。 也會取得顯示版本資訊的網站 URL。

  **消費者入門指南** 指定 (*.txt*， *.rtf*) 的檔案，其中包含如何在 VSIX 封裝中使用擴充功能或內容的相關資訊。 當擴充功能安裝完成時，即會顯示此指南。 也會取得顯示指南之網站的 URL。

  **詳細資訊 URL** 指定網站的 URL，其中包含產品的其他相關資訊。

  [ **安裝目標** ] 索引標籤包含下列控制項。

  **安裝類型** 列出 **Visual Studio 擴充** 功能和 **擴充功能 SDK** 做為目標安裝類型。 選項不同，視您選擇的類型而定。

  **Visual Studio 擴充** 功能列出 **InstallationTarget** 元素，描述如何安裝封裝，以及可以安裝此延伸模組 Visual Studio 產品。 每個產品都會依名稱和版本或版本範圍分別加以識別。 產品可以加入至清單、修改和刪除。 產品的名稱和版本會對應到相關聯 **InstallationTarget** 專案的 **Id** 和 **version** 屬性。

  **版本範圍** 是 [12.0，14.0]，並使用下列標記法：

- [-最小版本（含）

- ]-最大版本（含）

-  (-最小版本專屬

- ) -最大版本專屬

- 單一版本 #-僅限指定的版本

  **擴充功能 SDK** 指定範圍不限於特定產品和版本的全域安裝。 **目標平臺識別碼** 是您要設為目標的平臺，例如 "Windows"。 **目標平臺版本** 是目標平臺的版本，例如8.0。 **Sdk 名稱** 和 **sdk 版本** 分別是 sdk 的名稱和版本號碼。

  **此 VSIX 會針對所有使用者安裝 (需要在安裝時提高許可權)** 如果您選取此核取方塊，則會為所有使用者安裝此延伸模組。否則，它只會針對目前的使用者進行安裝。

  **此 VSIX 由 Windows Installer 安裝** 。如果您選取此核取方塊，此延伸模組會由 Windows Installer (*.msi* 檔案安裝) ;否則，它會安裝為 (*.vsix* 檔案) 的一般 vsix 套件。

  [ **資產** ] 索引標籤包含下列控制項。

  **資產清單** 列出描述此封裝所呈現之延伸模組或內容元素的資產專案。 每個延伸模組或內容元素都會依來源、類型和路徑分別列出。 擴充功能和內容專案可以新增至清單、修改和刪除。 延伸模組或內容專案的類型和路徑會對應至 `Type` 相關聯專案的和 `Path` 屬性 `Asset` 。 下面列出已知類型：

- VisualStudio 封裝

- Microsoft.VisualStudio.MefComponent

- VisualStudio. ToolboxControl

- VisualStudio 範例

- VisualStudio. ProjectTemplate

- VisualStudio

- VisualStudio. 元件

- ExtensionSDK

  若要新增或編輯資產，您必須指定資產類型、資產是否為目前方案中的專案或檔案系統中的檔案，以及專案的名稱。 您也可以指定要內嵌的資料夾名稱。

  您也可以建立自己的類型，並提供它們唯一的名稱。

  [相依 **性] 索引** 標籤包含下列控制項。

  **名稱、來源和版本範圍** 列出此封裝的相依性元素，也就是此封裝相依的其他封裝。 如果已指定相依性套件，則必須先安裝它，才能安裝此封裝;否則，此封裝必須安裝它。

  相依性套件是依識別碼、名稱、版本範圍、來源，以及如何解析相依性的方式來指定。 每個相依性套件都是依名稱、版本和來源分別列出。 您可以將相依性套件新增至清單、修改和刪除。

  識別碼必須符合相依性 `ID` 套件中繼資料的屬性。 來源可以是目前方案中的專案、目前安裝的副檔名或檔案。 [ **如何解決** 相依性] 設定可以是嵌套封裝的相對路徑，或相依性下載位置的 URL。 相依性套件的識別碼、版本及解析，會對應至 `Id` 相關聯專案的、 `Version` 和 `Location` 屬性 `Dependency` 。

## <a name="see-also"></a>請參閱
- [VSIX 延伸架構2.0 參考](../extensibility/vsix-extension-schema-2-0-reference.md)
- [VSIX 封裝的剖析](../extensibility/anatomy-of-a-vsix-package.md)
