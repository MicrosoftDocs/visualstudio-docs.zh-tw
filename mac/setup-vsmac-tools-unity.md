---
title: 設定 Visual Studio for Mac Tools for Unity
author: dantogno
ms.author: v-davian
ms.date: 07/17/2017
ms.assetid: 83FDD7A3-5D16-4B4B-9080-078E3FB5C623
ms.openlocfilehash: a1d6d523de9a5a57cf6b4c696a68dbdde1428156
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
---
# <a name="setup-visual-studio-for-mac-tools-for-unity"></a>設定 Visual Studio for Mac Tools for Unity

本節說明如何開始使用 Visual Studio for Mac Tools for Unity。

## <a name="install-visual-studio-for-mac"></a>安裝 Visual Studio for Mac

下載和安裝 Visual Studio for Mac。 所有 Visual Studio for Mac 版本都支援 Visual Studio for Mac Tools for Unity，包含免費 Community Edition：

* 從 [visualstudio.com](https://www.visualstudio.com/) 下載 Visual Studio for Mac。
* 在安裝程序期間，會自動安裝 Visual Studio for Mac Tools for Unity。
* 如需其他安裝說明，請遵循[安裝指南](/visualstudio/mac/installation)中的步驟。

## <a name="confirm-that-the-visual-studio-for-mac-tools-for-unity-extension-is-enabled"></a>確認已啟用 Visual Studio for Mac Tools for Unity 延伸模組

預設應該啟用 Visual Studio for Mac Tools for Unity 延伸模組時，您可以進行這項確認，並檢查已安裝的版本號碼：

1.  從 Visual Studio 功能表中，選取 [延伸模組]。

  ![選取 [延伸模組]](media/setup-vsmac-tools-unity-image1.png)

2.  展開 [遊戲開發] 區段，並確認 Visual Studio for Mac Tools for Unity 項目。

  ![檢視 Unity 項目](media/setup-vsmac-tools-unity-image2.png)

## <a name="install-unity"></a>安裝 Unity

Visual Studio for Mac Tools for Unity 需要 Unity 版本 5.6.1 或更新版本。 所有 Unity 計劃都會使用 Visual Studio Tools for Unity，包含免費的個人計劃。 從 [store.unity.com](https://store.unity.com/) 下載 Unity。

> [!NOTE]
> 若要確認 Unity 版本中已啟用 Visual Studio Tools for Unity，請從 Unity 功能表中選取 [About Unity] (關於 Unity) 功能表，並在對話方塊左下方尋找「已啟用 Microsoft Visual Studio Tools for Unity」文字。
>
>   ![關於 Unity](media/setup-vsmac-tools-unity-image3.png)

## <a name="configure-unity-for-use-with-visual-studio-for-mac"></a>設定 Unity 以與 Visual Studio for Mac 搭配使用

Visual Studio 必須設定為 Unity 中的外部指令碼編輯器：

1.  從 Unity 功能表中，選取 [喜好設定]。

  ![選取 [喜好設定]](media/setup-vsmac-tools-unity-image4.png)

2.  在 [喜好設定] 對話方塊中，選取 [外部工具] 索引標籤。

3.  從 [External Script Editor] (外部指令碼編輯器) 下拉式清單中，選擇列出的 [Visual Studio]，否則請選取 [瀏覽...]。

  ![選取 [Visual Studio]](media/setup-vsmac-tools-unity-image5.png)

4.  如果已選取 [瀏覽...]，請巡覽至 [應用程式] 目錄，並選取 [Visual Studio]，然後按一下 [開啟]。

  ![選取 [開啟]](media/setup-vsmac-tools-unity-image6.png)

5.  在 [External Script Editor] (外部指令碼編輯器) 清單中選取 Visual Studio 之後，請關閉 [喜好設定] 對話方塊，以完成設定程序。
