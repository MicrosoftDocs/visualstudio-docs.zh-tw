---
title: 設定 Visual Studio for Mac Tools for Unity
description: 設定和安裝 Unity 工具，以便在 Visual Studio for Mac 中使用
author: therealjohn
ms.author: johmil
ms.date: 05/25/2018
ms.assetid: 83FDD7A3-5D16-4B4B-9080-078E3FB5C623
ms.topic: how-to
ms.openlocfilehash: f423b77f8464b05b81be2ff7cdb08a2d8b007e0d
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2021
ms.locfileid: "98723058"
---
# <a name="set-up-visual-studio-for-mac-tools-for-unity"></a>設定 Visual Studio for Mac Tools for Unity

本節說明如何開始使用 Visual Studio for Mac Tools for Unity。

## <a name="install-visual-studio-for-mac"></a>安裝 Visual Studio for Mac

### <a name="unity-bundled-installation"></a>Unity 配套安裝

從 Unity 2018.1 開始，Visual Studio for Mac 是 Unity 的預設 C# 整合式開發環境 (IDE)，而且包含在 Unity 下載助理和 Unity 中樞安裝工具中。 從 [store.unity.com](https://store.unity.com/) 下載 Unity。

在安裝期間，請確定已核取要與 Unity 一起安裝之元件清單中的 Visual Studio for Mac：

#### <a name="unity-hub"></a>Unity 中樞

![unity 中樞安裝](media/setup-vsmac-tools-unity-image7.png)

#### <a name="unity-download-assistant"></a>Unity 下載小幫手

![unity 下載小幫手安裝](media/setup-vsmac-tools-unity-image8.png)

#### <a name="check-for-updates-to-visual-studio-for-mac"></a>檢查 Visual Studio for Mac 的更新

Unity 安裝所隨附的 Visual Studio for Mac 版本可能不是最新。 建議您檢查更新，以確保您可以存取最新工具和功能。

* [更新 Visual Studio for Mac](update.md)

### <a name="manual-installation"></a>手動安裝

如果您已經有 Unity 5.6.1 或更新版本，但沒有 Visual Studio for Mac，可以手動安裝 Visual Studio for Mac。 所有 Visual Studio for Mac 版本都與 Visual Studio for Mac Tools for Unity 配套，包含免費 Community Edition：

* 從 [visualstudio.microsoft.com](https://visualstudio.microsoft.com/) 下載 Visual Studio for Mac。
* 在安裝程序期間，會自動安裝 Visual Studio for Mac Tools for Unity。
* 如需其他安裝說明，請遵循[安裝指南](./installation.md?view=vsmac-2017&preserve-view=true)中的步驟。

> [!NOTE]
> Visual Studio for Mac Tools for Unity 需要 Unity 版本 5.6.1 或更新版本。 若要確認 Unity 版本中已啟用 Visual Studio Tools for Unity，請從 Unity 功能表中選取 [About Unity] (關於 Unity) 功能表，並在對話方塊左下方尋找「已啟用 Microsoft Visual Studio Tools for Unity」文字。
>
> ![關於 Unity](media/setup-vsmac-tools-unity-image3.png)

## <a name="confirm-that-the-visual-studio-for-mac-tools-for-unity-extension-is-enabled"></a>確認已啟用 Visual Studio for Mac Tools for Unity 延伸模組

預設應該啟用 Visual Studio for Mac Tools for Unity 延伸模組時，您可以進行這項確認，並檢查已安裝的版本號碼：

1. 從 Visual Studio 功能表中，選取 [延伸模組]。

   ![選取 [延伸模組]](media/setup-vsmac-tools-unity-image1.png)

2. 展開 [遊戲開發] 區段，並確認 Visual Studio for Mac Tools for Unity 項目。

   ![檢視 Unity 項目](media/setup-vsmac-tools-unity-image2.png)

## <a name="configure-unity-for-use-with-visual-studio-for-mac"></a>設定 Unity 以與 Visual Studio for Mac 搭配使用

從 Unity 2018.1 開始，Visual Studio 應該是 Unity 中的預設外部指令碼編輯器。 您可以確認這一點，或將外部指令碼編輯器變更為 Visual Studio：

1. 從 Unity 功能表中，選取 [喜好設定]。

   ![選取 [喜好設定]](media/setup-vsmac-tools-unity-image4.png)

2. 在 [喜好設定] 對話方塊中，選取 [外部工具] 索引標籤。

3. 從 [External Script Editor] (外部指令碼編輯器) 下拉式清單中，選擇列出的 [Visual Studio]，否則請選取 [瀏覽...]。

   ![選取 [Visual Studio]](media/setup-vsmac-tools-unity-image5.png)

4. 如果已選取 [瀏覽...]，請巡覽至 [應用程式] 目錄，並選取 [Visual Studio]，然後按一下 [開啟]。

   ![選取 [開啟]](media/setup-vsmac-tools-unity-image6.png)

5. 在 [External Script Editor] (外部指令碼編輯器) 清單中選取 Visual Studio 之後，請關閉 [喜好設定] 對話方塊，以完成設定程序。