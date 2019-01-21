---
title: 安裝 Visual Studio 2019 for Mac 預覽版
description: 如何安裝 Visual Studio 2019 for Mac 預覽版和跨平台開發所需之其他元件的指示。
author: conceptdev
ms.author: crdun
ms.date: 11/03/2018
ms.technology: vs-ide-install
ms.assetid: 22B1F2CD-32AE-464D-80AC-C8AB4786B015
ms.openlocfilehash: acd8f3bc4f5fefa0a0c8b273856579067fb33c6a
ms.sourcegitcommit: 5a65ca6688a2ebb36564657d2d73c4b4f2d15c34
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/15/2019
ms.locfileid: "54315896"
---
# <a name="install-visual-studio-2019-for-mac-preview"></a>安裝 Visual Studio 2019 for Mac 預覽版

> [!NOTE]
> Visual Studio 2019 for Mac 預覽版可與最新穩定版本的 Visual Studio for Mac 並存安裝。 系統將在安裝期間提示您更新現有的 Visual Studio (如果它不是最新穩定版本)。

## <a name="requirements-for-the-visual-studio-2019-for-mac-preview"></a>Visual Studio 2019 for Mac 預覽版的需求

- 具有 macOS High Sierra 10.13 或以上版本的 Mac。

若要建置適用於 iOS 或 macOS 的 Xamarin 應用程式，您還需要：

- Xcode 10.0 或以上版本。 通常建議使用最新穩定版本。
- Apple ID。 如果您還沒有 Apple 識別碼，可以在 https://appleid.apple.com 建立一個新識別碼。 安裝及登入 Xcode 時需要有 Apple 識別碼。

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

    如果您目前使用的 Visual Studio 2017 for Mac 版本比 7.7 版還舊，系統將要求您核准升級至最新穩定版本 (其為支援並存安裝的必要條件)。 按 [繼續] 核准升級：

    ![您也必須將穩定版本升級至 7.7](media/install-preview-older-upgrade.png)

7. 選取完成之後，請按 [安裝] 按鈕。
8. 安裝程式會顯示下載和安裝 Visual Studio for Mac 的進度，並顯示選取的工作負載。 系統可能會提示您輸入密碼，授與安裝所需的權限。
9. 您可以隨時使用 **Visual Studio (Preview)** 測試預覽版本，或切換回最新的穩定 Visual Studio 進行生產工作。 下列為這兩個圖示：

    ![穩定版和預覽版的圖示差異](media/install-preview-icons-sml.png)

如果您在公司環境安裝時發生網路問題，請檢閱[在防火牆或 Proxy 後方安裝](https://docs.microsoft.com/visualstudio/mac/installation#install-visual-studio-for-mac-behind-a-firewall-or-proxy-server)指示。

深入了解[版本資訊](https://docs.microsoft.com/visualstudio/releasenotes/vs2019-mac-preview-relnotes)中的變更。

> [!NOTE]
> 如果您在原始安裝期間選擇不安裝平台或工具 (在步驟 #6 中取消選取它)，當您稍後想要新增元件時，必須再次執行安裝程式。

## <a name="install-visual-studio-for-mac-behind-a-firewall-or-proxy-server"></a>將 Visual Studio for Mac 安裝在防火牆或 Proxy 伺服器後方

若要將 Visual Studio for Mac 安裝在防火牆後方，某些端點必須設為可供存取，才能允許下載您軟體所需的工具和更新。

將您的網路設定為允許存取下列位置：

- [Visual Studio 端點](/visualstudio/install/install-visual-studio-behind-a-firewall-or-proxy-server)

## <a name="next-steps"></a>後續步驟

安裝 Visual Studio for Mac 可讓您開始撰寫應用程式的程式碼。 以下指示提供您下一步撰寫及部署專案的逐步指示。

### <a name="ios"></a>iOS

1. [Hello, iOS](https://developer.xamarin.com/guides/ios/getting_started/hello,_iOS/)
2. [裝置部署](https://developer.xamarin.com/guides/ios/getting_started/installation/device_provisioning) \(英文\) (在裝置上執行您的應用程式)。

### <a name="android"></a>Android

1. [使用 Xamarin Android SDK 管理員](https://developer.xamarin.com/guides/android/getting_started/installation/android-sdk/?ide=xs) \(英文\)
2. [Android SDK 模擬器](https://developer.xamarin.com/guides/android/getting_started/installation/android-emulator/) \(英文\)
4. [設定您的裝置以進行開發](https://developer.xamarin.com/guides/android/getting_started/installation/set_up_device_for_development/) \(英文\)

### <a name="net-core-apps-aspnet-core-web-apps-unity-game-development"></a>.NET Core 應用程式、ASP.NET Core Web 應用程式、Unity 遊戲開發

對於其他工作負載，請參閱[工作負載](/visualstudio/mac/workloads)頁面。

## <a name="see-also"></a>另請參閱

- [安裝 Visual Studio 2017 (Windows 上)](/visualstudio/install/install-visual-studio)
