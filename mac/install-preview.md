---
title: 安裝預覽版本
description: 針對更新 Visual Studio for Mac 以及存取預覽版本的指示，包括 Visual Studio 2019 for Mac 預覽版。
zone_pivot_groups: mac-ide-version
author: conceptdev
ms.author: crdun
ms.date: 11/03/2018
ms.topic: article
ms.technology: vs-ide-install
ms.assetid: 0E1EF257-9DE4-4653-9DF4-805CE007A1A1
ms.openlocfilehash: b5eea8c2c894b7eeaa13c83ae6698d1297de9297
ms.sourcegitcommit: ae46be4a2b2b63da7e7049e9ed67cd80897c8102
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2018
ms.locfileid: "52896753"
---
# <a name="install-a-preview-release"></a>安裝預覽版本

::: zone pivot="vsmac2019"

> [!TIP]
> Visual Studio 2019 for Mac 預覽版現已可供使用。 其首度可與最新穩定版本的 Visual Studio for Mac 並存安裝。

## <a name="requirements-for-the-visual-studio-2019-for-mac-preview"></a>Visual Studio 2019 for Mac 預覽版的需求

* 具有 macOS High Sierra 10.13 或以上版本的 Mac。

若要建置適用於 iOS 或 macOS 的 Xamarin 應用程式，您還需要：

* Xcode 10.0 或以上版本。 通常建議使用最新穩定版本。
* Apple ID。 如果您還沒有 Apple 識別碼，可以在 https://appleid.apple.com 建立一個新識別碼。 安裝及登入 Xcode 時需要有 Apple 識別碼。

## <a name="installing-the-preview"></a>安裝預覽版

1. 從 [Visual Studio for Mac 預覽版頁面](https://aka.ms/vs4mac-preview)下載預覽版安裝程式。
2. 下載完成後，按一下 **VisualStudioforMacPreviewInstaller.dmg** 裝載安裝程式，然後按兩下箭號標誌以執行：

    [![按一下大型箭號，開始安裝](media/install-preview-installer-sml.png)](media/install-preview-installer.png#lightbox)

3. 您可能會看到要從網際網路下載應用程式的相關警告。 按一下 [開啟]。
4. 等候安裝程式檢查您的系統：

    [![安裝程式會檢查您系統的已安裝元件](media/install-preview-checking-sml.png)](media/install-preview-checking.png#lightbox)

5. 系統會出現要求您確認隱私權和授權條款的警示。 請前往連結並加以閱讀；如果您同意即可按 [繼續]：

    [![前往隱私權和條款的連結；如果您同意，請繼續執行](media/install-preview-privacy-sml.png)](media/install-preview-privacy.png#lightbox)

6. 即會顯示可用工作負載的清單。 選取您想要使用的項目：

    [![選擇您想要安裝的選擇性工作負載功能](media/install-preview-selection-sml.png)](media/install-preview-selection.png#lightbox)

    如果您目前使用的 Visual Studio for Mac 2017 版本比 7.7 版還舊，系統會要求您核准升級至最新的穩定版本 (其為支援並存安裝的必要條件)。 按 [繼續] 核准升級：

    ![您也必須將穩定版本升級至 7.7](media/install-preview-older-upgrade.png)

7. 選取完成之後，請按 [安裝] 按鈕。
8. 安裝程式會顯示下載和安裝 Visual Studio for Mac 的進度，並顯示選取的工作負載。 系統可能會提示您輸入密碼，授與安裝所需的權限。
9. 您可以隨時使用 **Visual Studio (Preview)** 測試預覽版本，或切換回最新的穩定 Visual Studio 進行生產工作。 下列為這兩個圖示：

    ![穩定版和預覽版的圖示差異](media/install-preview-icons-sml.png)

如果您在公司環境安裝時發生網路問題，請檢閱[在防火牆或 Proxy 後方安裝](https://docs.microsoft.com/visualstudio/mac/installation#install-visual-studio-for-mac-behind-a-firewall-or-proxy-server)指示。

深入了解[版本資訊](https://docs.microsoft.com/visualstudio/releasenotes/vs2019-mac-preview-relnotes)中的變更。

::: zone-end
::: zone pivot="vsmac2017"

## <a name="install-an-update-for-visual-studio-2017-for-mac"></a>安裝 Visual Studio 2017 for Mac 的更新

Visual Studio for Mac 的新版本正式發行之前，會先提供預覽版本。 預覽版本讓您有機會嘗試新功能並獲得最新的 Bug 修正，再將其完整納入產品中。

預覽版本會散發至 Visual Studio for Mac 作為更新，而非透過個別下載。 如[更新](update.md)一文中所述，Visual Studio for Mac 有三個更新程式通道：穩定版、搶鮮版 (Beta) 和 Alpha 版。

大部分的預覽版本將可透過**搶鮮版 (Beta)** 和 **Alpha** 通道取得，但請經常檢查[預覽版本資訊](/visualstudio/releasenotes/vs2017-mac-preview-relnotes)以取得最精確的資訊。

若要安裝 Visual Studio for Mac 的預覽版本，請使用下列步驟：

1. 移至 [Visual Studio] > [檢查更新]。
2. 在更新通道下拉式方塊中，選取 [Beta]。
3. 選取 [切換通道] 按鈕切換至選取的通道，並開始下載新的更新。
4. 選取 [重新啟動和安裝更新] 按鈕開始安裝更新。

如需在 Visual Studio for Mac 中更新的詳細資訊，請參閱[更新](update.md)一文。

::: zone-end