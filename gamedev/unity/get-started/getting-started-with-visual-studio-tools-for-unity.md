---
title: Visual Studio Tools for Unity 使用者入門 | Microsoft Docs
description: 瞭解如何安裝及設定適用于 Unity 開發的 Visual Studio。
ms.custom: acquisition
ms.date: 01/27/2021
ms.technology: vs-unity-tools
ms.prod: visual-studio-dev16
ms.topic: how-to
ms.assetid: 66b5b4eb-13b5-4071-98d2-87fafa4598a8
author: therealjohn
ms.author: johmil
manager: crdun
ms.workload:
- unity
zone_pivot_groups: platform
ms.openlocfilehash: 8eea998731c4d29e533d1e6bf21d4a2870a81ff5
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2021
ms.locfileid: "112386692"
---
# <a name="get-started-with-visual-studio-and-unity"></a>開始使用 Visual Studio 和 Unity

> [!NOTE]
> 本指南假設您已使用 Unity 中樞程式安裝 Unity。 如果您是 Unity 新手，建議先造訪 Unity 學習，並完成 [Unity Essentials 學習路徑](https://learn.unity.com/pathway/unity-essentials) 。

## <a name="install-unity-support-for-visual-studio"></a>安裝 Visual Studio 的 Unity 支援

Visual Studio Tools for Unity 是免費的延伸模組，可支援撰寫和偵測 c # 和其他更多的功能。 請流覽適用 [于 Unity 的工具總覽](./visual-studio-tools-for-unity.md) ，以取得延伸模組包含內容的完整清單。

:::zone pivot="windows"

> [!NOTE]
> 本安裝指南適用于 Visual Studio。 如果您是使用 Visual Studio Code，請流覽 [Unity 開發與 VS Code 檔](https://code.visualstudio.com/docs/other/unity)。

1. [下載 Visual Studio 安裝程式](/visualstudio/install/install-visual-studio.md)，或在已安裝的情況下執行。
2. 針對您想要的 Visual Studio 版本按一下 (若已安裝) 或 [安裝] (針對新安裝)。
3. 在 [ **工作負載** ] 索引標籤上，選取 [ **遊戲** ] 區段，然後選取 [ **使用 Unity 工作負載進行遊戲開發** ]。

    ![安裝程式中使用 Unity 的遊戲開發工作負載方塊](../media/vs/unity-workload.png)

:::zone-end
:::zone pivot="macos"

> [!NOTE]
> 本安裝指南適用于 Visual Studio for Mac。 如果您是使用 Visual Studio Code，請流覽 [Unity 開發與 VS Code 檔](https://code.visualstudio.com/docs/other/unity)。

適用于 Unity 的工具隨附于安裝 Visual Studio for Mac，且不需要個別的安裝步驟。 您可以在 **Visual Studio for Mac > 擴充功能 > 遊戲開發** 功能表中確認這項功能。 應啟用 **適用于 Unity 的 Visual Studio for Mac 工具**。

![顯示已啟用 Visual Studio for Mac Tools for Unity 的 [擴充管理員] 視圖](../media/vsm/unity-workload.png)

:::zone-end

## <a name="check-for-updates"></a>檢查更新

建議您保持 Visual Studio 並 Visual Studio for Mac 更新，以取得最新的 bug 修正、功能和 Unity 支援。 這不需要更新 Unity 版本。

:::zone pivot="windows"

1. 按一下 [說明] **> 檢查 [更新** ] 功能表。

    ![Visual Studio 2019 中的 [檢查更新] 功能表](../media/vs/check-for-updates.png)

2. 如果有可用的更新，Visual Studio 安裝程式將會顯示新的版本。 按一下 [更新] 按鈕。

:::zone-end
:::zone pivot="macos"

1. 按一下 [ **Visual Studio for Mac] > 檢查更新 ...** 功能表以開啟 **Visual Studio 更新** ] 對話方塊。
2. 如果有可用的更新，請按一下 [ **安裝** ] 按鈕。

:::zone-end

## <a name="configure-unity-to-use-visual-studio"></a>設定 Unity 以使用 Visual Studio

根據預設，Unity 應該已設定為使用 Visual Studio 或 Visual Studio for Mac 作為腳本編輯器。 您可以從 Unity 編輯器確認這項變更，或將外部腳本編輯器變更為特定版本的 Visual Studio。

:::zone pivot="windows"

1. 在 Unity 編輯器中，選取 [ **編輯 > 喜好** 設定] 功能表。
2. 選取左側的 [ **外部工具** ] 索引標籤。
3. [ **外部腳本編輯器** ] 下拉式清單提供一種方式，讓您選擇不同的 Visual Studio 安裝。 您也可以按一下下拉式清單中的 **[流覽 ...]** ，以新增未列出的版本。

    ![Windows 上 Unity 編輯器中的 [外部工具喜好設定] 功能表](../media/vs/preferences-external-tools.png)

4. 若已選取 [瀏覽]，請瀏覽到您 Visual Studio 安裝目錄中的 **Common7/IDE** 目錄，然後選取 [devenv.exe]。 然後按一下 [ **開啟**]。
5. 在 [External Script Editor] \(外部指令碼編輯器\) 清單中選取 Visual Studio 之後，請確認已選取 [Editor Attaching] \(編輯器附加\) 核取方塊。
6. 關閉 [喜好設定] 對話方塊以完成設定程序。

:::zone-end
:::zone pivot="macos"

1. 在 Unity 編輯器中，選取 [ **unity > 喜好** 設定] 功能表。
2. 選取左側的 [ **外部工具** ] 索引標籤。
3. [ **外部腳本編輯器** ] 下拉式清單提供一種方式，讓您選擇不同的 Visual Studio 安裝。 您也可以按一下下拉式清單中的 **[流覽 ...]** ，以新增未列出的版本。

    ![MacOS 上 Unity 編輯器中的 [外部工具喜好設定] 功能表](../media/vsm/preferences-external-tools.png)

4. 關閉 [喜好設定] 對話方塊以完成設定程序。

:::zone-end

## <a name="next-steps"></a>後續步驟

 若要瞭解如何在 Visual Studio 中使用和偵測您的 Unity 專案，請流覽 [使用 Visual Studio Tools for Unity](using-visual-studio-tools-for-unity.md)。
