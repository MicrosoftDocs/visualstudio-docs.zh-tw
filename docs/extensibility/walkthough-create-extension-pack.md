---
title: 使用延伸套件項目樣本建立擴充套件 |微軟文件
ms.date: 07/27/2018
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - extensions
ms.assetid: 5388EEBA-211D-4114-8CD9-70C899919F7E
author: acangialosi
ms.author: anthc
manager: Meng
ms.workload:
- vssdk
ms.openlocfilehash: fa1c141e18a3870eaad4b155d816e30ee207f45d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697754"
---
# <a name="walkthrough-create-an-extension-pack"></a>逐步解說：建立延伸模組組件

擴展包是一組可以一起安裝的擴展。 擴展包使您能夠輕鬆地與其他使用者共用您最喜愛的擴展,或針對特定方案將一組擴展捆綁在一起。

## <a name="prerequisites"></a>Prerequisites

從 Visual Studio 2015 開始,Visual Studio SDK 將作為可選功能包含在可視化工作室設置中。 以後還可以安裝 VS SDK。 有關詳細資訊,請參閱[安裝可視化工作室 SDK](../extensibility/installing-the-visual-studio-sdk.md)。

擴展包功能可從視覺工作室 15.8 預覽 2 開始。

## <a name="create-an-extension-with-an-extension-pack-item-template"></a>使用延伸套件項目樣本建立擴充

擴展包項目範本創建一個擴展包,其中包含一組可以一起安裝的擴展。

1. 在**新項目對話**框中,搜尋「vsix」並選擇**VSIX 專案**。 對於**專案名稱**,鍵入"測試擴展包"。 選取 [建立]  。

2. 在**解決方案資源管理器**中,右鍵單擊專案節點並選擇「**添加新** > **項**」。 跳到視覺化 C#**擴充性**節點並選擇**延伸套件**。 保留預設檔名 (ExtensionPack1.cs)。

3. 延伸套件1.vsext檔被新增,其中包含以下代碼

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

4. 要包含在擴展包中的擴展的 vsixid 可以在[可視化工作室應用商店](https://marketplace.visualstudio.com/)中找到。 尋找要包含的副檔名,然後按下 **「複製 ID」。。** 您可以在上述檔中更新現有**vsixId,** 或向清單中添加另一個副檔名。

    ![從應用程式商店複製 VsixId](media/vsixid-marketplace.png)

5. 生成專案並將擴展上載到應用商店。 請參閱[發佈視覺化工作室擴展](../extensibility/walkthrough-publishing-a-visual-studio-extension.md)。

> [!NOTE]
> 擴展包只能安裝[在可視化工作室市場](https://marketplace.visualstudio.com/)或[專用庫](../extensibility/how-to-create-an-atom-feed-for-a-private-gallery.md)上可用的擴展。

## <a name="install-the-extension-pack-from-the-visual-studio-marketplace"></a>從視覺化工作室市場安裝擴充套件

現在,擴展已發佈,請將其安裝在 Visual Studio 中並在那裡進行測試。

::: moniker range="vs-2017"

1. 在可視化工作室中,在 **「工具」** 功能表上,按一下 **「擴展和更新**」。

::: moniker-end

::: moniker range=">=vs-2019"

1. 在可視化工作室中,在 **「擴展」** 功能表上,按一下 **「託管擴展**」。。

::: moniker-end

2. 按下 **「連線」 然後**搜尋「測試擴展包」。

3. 按一下 [下載]  。 然後,將安排擴展包中包含的擴展及其擴展清單進行安裝。

4. 下面是 **「管理擴展」** 對話方塊的範例延伸套件下載檢視。 如果只想在擴展包中安裝某些包含的擴展,則可以修改 **「計畫安裝」** 中的延伸清單。

    ![從應用商店下載擴展包](media/vside-extensionpack.png)

5. 要完成安裝,關閉可視化工作室的所有實例。

## <a name="remove-the-extension"></a>移除擴充功能

要從電腦中移除副檔名,請:

::: moniker range="vs-2017"

1. 在可視化工作室中,在 **「工具」** 功能表上,按一下 **「擴展和更新**」。

::: moniker-end

::: moniker range=">=vs-2019"

1. 在可視化工作室中,在 **「擴展」** 功能表上,按一下 **「託管擴展**」。。

::: moniker-end

2. 測試**延伸套件**,然後單擊 **「卸載**」。。 然後,擴展包中包含的擴展及其擴展清單將安排卸載。

3. 要完成卸載,關閉可視化工作室的所有實例。
