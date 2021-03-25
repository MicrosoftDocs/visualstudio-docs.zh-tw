---
title: 建立延伸模組套件
description: 瞭解如何使用延伸模組套件專案範本建立延伸模組套件
ms.custom: SEO-VS-2020
ms.date: 07/27/2018
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - extensions
ms.assetid: 5388EEBA-211D-4114-8CD9-70C899919F7E
author: leslierichardson95
ms.author: lerich
manager: Meng
ms.workload:
- vssdk
ms.openlocfilehash: 57b447be3ee411b737c1aea5b0a4be5ef966c8c6
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105062144"
---
# <a name="walkthrough-create-an-extension-pack"></a>逐步解說：建立延伸模組組件

擴充功能套件是一組可一起安裝的延伸模組。 延伸模組套件可讓您輕鬆地與其他使用者共用您最愛的擴充功能，或將一組延伸模組組合在一組特定案例中。

## <a name="prerequisites"></a>必要條件

從 Visual Studio 2015 開始，Visual Studio SDK 在 Visual Studio 安裝程式中包含為選用功能。 您也可以稍後再安裝 VS SDK。 如需詳細資訊，請參閱 [安裝 VISUAL STUDIO SDK](../extensibility/installing-the-visual-studio-sdk.md)。

從 Visual Studio 15.8 Preview 2 開始，可以使用擴充功能套件功能。

## <a name="create-an-extension-with-an-extension-pack-item-template"></a>使用延伸模組套件專案範本建立延伸模組

延伸模組套件專案範本會建立延伸模組套件，其中包含可一起安裝的延伸模組集合。

1. 在 [ **新增專案** ] 對話方塊中，搜尋 "vsix" 並選取 [ **vsix 專案**]。 在 [ **專案名稱**] 中，輸入「測試擴充功能套件」。 選取 [建立]  。

2. 在 [**方案總管** 中，以滑鼠右鍵按一下專案節點，然後選取 [**加入**  >  **新專案**]。 移至 [ **Visual c #** 擴充性] 節點，然後選取 [擴充功能 **套件**]。 將預設的檔案名保留 (ExtensionPack1]) 。

3. 加入的 ExtensionPack1 vsext 檔案包含下列程式碼

   ```json
   {
    "id": "ExtensionPack1",
    "name": "ExtensionPack1",
    "description": "Read about creating extension packs at https://aka.ms/vsextpack",
    "version": "1.0.0.0",
    "extensions": [  // List of extensions that are included in the Extension Pack.
      {
        "vsixId": "41858b2d-ff0b-4a43-80b0-f1b2d6084935", // The vsix id of the extension you want to   include.
        "name": "AlignAssignments"
      },
      {
          "vsixId": "42374550-426a-400e-96f9-237682e8dea6",
        "name": "CopyAsHtml"
      }
    ]
   }
   ```

4. 延伸模組套件中包含的延伸模組 vsixid 可以在 [Visual Studio Marketplace](https://marketplace.visualstudio.com/)上找到。 尋找您想要包含的延伸模組，然後按一下 [ **複製識別碼**]。 您可以更新上述檔案中的現有 **vsixId** ，或將其他副檔名新增至清單。

    ![從 Marketplace 複製 VsixId](media/vsixid-marketplace.png)

5. 建立專案，並將您的延伸模組上傳至 Marketplace。 請參閱 [發行 Visual Studio 延伸](../extensibility/walkthrough-publishing-a-visual-studio-extension.md)模組。

> [!NOTE]
> 延伸模組套件只能安裝 [Visual Studio Marketplace](https://marketplace.visualstudio.com/) 或私用映射 [庫](../extensibility/how-to-create-an-atom-feed-for-a-private-gallery.md)中可用的擴充功能。

## <a name="install-the-extension-pack-from-the-visual-studio-marketplace"></a>從 Visual Studio Marketplace 安裝延伸模組套件

現在擴充功能已發佈，請將它安裝在 Visual Studio 中，並在該處進行測試。

::: moniker range="vs-2017"

1. 在 Visual Studio 中，按一下 [ **工具** ] 功能表上的 [ **擴充功能和更新**]。

::: moniker-end

::: moniker range=">=vs-2019"

1. 在 Visual Studio 的 [ **延伸** 模組] 功能表上，按一下 [ **受管理的延伸** 模組]。

::: moniker-end

2. 按一下 [ **線上** ]，然後搜尋「測試擴充功能套件」。

3. 按一下 [下載] 。 延伸模組及其內含的延伸模組清單，將會排程安裝。

4. 以下是 [ **管理擴充** 功能] 對話方塊的範例擴充功能套件下載視圖。 如果您只想要在延伸模組套件中安裝部分包含的延伸模組，您可以在 [ **排程安裝**] 中修改擴充功能清單。

    ![從 Marketplace 下載延伸模組套件](media/vside-extensionpack.png)

5. 若要完成安裝，請關閉 Visual Studio 的所有實例。

## <a name="remove-the-extension"></a>移除擴充功能

若要從電腦移除擴充功能：

::: moniker range="vs-2017"

1. 在 Visual Studio 中，按一下 [ **工具** ] 功能表上的 [ **擴充功能和更新**]。

::: moniker-end

::: moniker range=">=vs-2019"

1. 在 Visual Studio 的 [ **延伸** 模組] 功能表上，按一下 [ **受管理的延伸** 模組]。

::: moniker-end

2. 選取 [ **測試擴充功能套件** ]，然後按一下 [ **卸載**]。 延伸模組及其內含的延伸模組清單，將會排程卸載。

3. 若要完成卸載，請關閉 Visual Studio 的所有實例。
