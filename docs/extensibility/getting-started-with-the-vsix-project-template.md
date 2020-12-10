---
title: 使用 VSIX 專案範本消費者入門 |Microsoft Docs
description: 瞭解如何使用 VSIX 專案範本來建立擴充功能，或封裝現有的延伸模組以進行部署。
ms.custom: SEO-VS-2020
ms.date: 3/16/2019
ms.topic: how-to
helpviewer_keywords:
- Visual Studio SDK, VSIX project template
ms.assetid: 89fac33e-9380-4723-9b45-048a6e16f0ed
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c6c7c2e12f01b008be6937a8c974f2eea183d594
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "96994338"
---
# <a name="get-started-with-the-vsix-project-template"></a>開始使用 VSIX 專案範本

您可以使用 VSIX 專案範本來建立擴充功能，或封裝現有的延伸模組以進行部署。 VSIX 專案範本同時包含 Visual Basic 和 Visual c # 版本，並且會安裝為 Visual Studio SDK 的一部分。

 VSIX 專案範本只包含 *extension.vsixmanifest* 檔案，其中包含延伸模組及其所附資產的相關資訊。

 若要尋找 VSIX 專案範本，您必須安裝 Visual Studio SDK。 如需詳細資訊，請參閱 [VISUAL STUDIO SDK](../extensibility/visual-studio-sdk.md)。

## <a name="deploy-a-custom-project-template-using-the-vsix-project-template"></a>使用 VSIX 專案範本部署自訂專案範本

 下列步驟示範如何使用 VSIX 專案封裝可與其他開發人員共用的專案範本，或上傳至 Visual Studio 資源庫。

1. 建立專案範本。

    1. 開啟要從中建立範本的專案。 這個專案可以是任何專案類型。

    2. 按一下 [專案] 功能表上的 [匯出範本]。 完成 wizard 的步驟。

         *%USERPROFILE%\My Documents\Visual Studio {version} \My 匯出的 \\ 範本* 中會建立一個 *.zip* 檔案。

2. 建立空的 VSIX 專案。

     選取 [File] \(檔案\) >  [New] \(新增\) >  [Project] \(專案\)。 在搜尋方塊中，輸入 "vsix"，然後選取 **c #** 或 **Visual Basic** 版本的 **vsix 專案**。

3. 將 *.zip* 檔加入至專案。 將其 [ **複製到輸出目錄** ] 屬性設定為 `Copy Always` 。

4. 在 **方案總管** 中，按兩下 *extension.vsixmanifest* 檔案，在 **VSIX 資訊清單設計** 工具中開啟檔案，然後進行下列變更：

    - 將 [ **產品名稱** ] 欄位設定為 [ **我的專案] 範本**。

    - 將 [ **產品識別碼** ] 欄位設定為 **MyProjectTemplate-1**。

    - 將 [ **作者** ] 欄位設定為 [ **Fabrikam**]。

    - 將 [ **描述** ] 欄位設定為 [ **我的專案] 範本**。

    - 在 [ **資產** ] 區段中，新增 **VisualStudio ProjectTemplate** 類型，並將其路徑設定為 *.zip* 檔案的名稱。

5. 儲存並關閉 *extension.vsixmanifest* 檔案。

6. 建置專案。

7. 在輸出目錄中，按兩下 *.vsix* 檔案。

8. **VSIX 安裝程式** 訊息方塊隨即出現。 遵循指示來安裝擴充功能。

9. 結束再重新開啟 Visual Studio。

::: moniker range="vs-2017"

10. 選取 [**工具**] 功能表上的 [**擴充功能和更新** (]) ，然後選取 [**範本**] 類別。 其中一個可用的擴充功能應該是 **我的專案範本**。

::: moniker-end

::: moniker range=">=vs-2019"

10. 選取 [**延伸** 模組] 功能表上的 [**管理擴充** 功能 (]) 然後選取 [**範本**] 類別。 其中一個可用的擴充功能應該是 **我的專案範本**。

::: moniker-end

11. 新的專案範本會出現在 [ **新增專案** ] 對話方塊中，與原始專案範本相同的位置。 例如，如果您從 Visual Basic 主控台應用程式建立名為 **VB 主控台** 的範本， **VB 主控台** 會出現在與 Visual Basic **主控台應用程式** 範本相同的窗格中。

### <a name="to-specify-the-location-of-the-template-in-the-new-project-dialog-box"></a>在 [新增專案] 對話方塊中指定範本的位置

1. 範本資料夾位於 *{Visual Studio 安裝路徑} \Common7\IDE\ProjectTemplates* 和 *{Visual Studio 安裝路徑} \Common7\IDE\ItemTemplates* 目錄。 [ **新增專案** ] 對話方塊中最上層區段的名稱與範本資料夾的名稱不完全相符。 如果不同，請使用範本資料夾的名稱。

    將 *.vsix* 副檔名變更為 *.zip*，然後開啟檔案。

2. 使用與 [ **新增專案** ] 對話方塊中的區段相同的名稱建立新資料夾，範本應該會出現在中。

3. 如果範本要出現在子區段中，請建立相同名稱的子資料夾。

4. 將範本 *.zip* 檔案移至新的資料夾。

5. 將 *.zip* 副檔名變更為 *.vsix*。

6. 開啟 VSIX 資訊清單。

7. 在 VSIX 資訊清單中，更新範本的 **資產** 路徑，使其指向包含範本檔案之目錄樹狀結構的根目錄。 例如，如果範本是在 *\CSharp\Windows* 中，則參考應指向 *\CSharp*。
