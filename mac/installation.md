---
title: 安裝 Visual Studio 2019 for Mac
description: 如何安裝 Visual Studio 2019 for Mac 及其他跨平台開發所需元件的指示。
author: conceptdev
ms.author: crdun
ms.date: 04/02/2019
ms.technology: vs-ide-install
ms.assetid: 22B1F2CD-32AE-464D-80AC-C8AB4786B015
ms.custom: video
ms.openlocfilehash: 92b8fdceb1f4cfcfc54f9e37aea3a93f765976a3
ms.sourcegitcommit: 77b4ca625674658d5c5766e684fa0e2a07cad4da
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2019
ms.locfileid: "65615466"
---
# <a name="install-visual-studio-2019-for-mac"></a>安裝 Visual Studio 2019 for Mac

若要開始在 macOS 上開發原生、跨平台的 .NET 應用程式，請遵循下方步驟安裝 Visual Studio 2019 for Mac。

## <a name="requirements"></a>需求

- 具有 macOS High Sierra 10.12 或更高版本的 Mac。

若要建置適用於 iOS 或 macOS 的 Xamarin 應用程式，您還需要：

- Xcode 10.0 或以上版本。 通常建議使用最新穩定版本。
- Apple ID。 如果您還沒有 Apple 識別碼，可以在 https://appleid.apple.com 建立一個新識別碼。 安裝及登入 Xcode 時需要有 Apple 識別碼。

## <a name="installation-instructions"></a>安裝指示

1. 從 [Visual Studio for Mac 下載頁面](https://aka.ms/vsmac)下載安裝程式。
2. 下載完成後，按一下 **VisualStudioforMacInstaller.dmg** 裝載安裝程式，然後按兩下箭號標誌加以執行：

    [![按一下大型箭號，開始安裝](media/install-installer-sml.png)](media/install-installer.png#lightbox)

3. 您可能會看到要從網際網路下載應用程式的相關警告。 按一下 [開啟]。
4. 等候安裝程式檢查您的系統：

    [![安裝程式會檢查您系統的已安裝元件](media/install-checking-sml.png)](media/install-checking.png#lightbox)

5. 系統會出現要求您確認隱私權和授權條款的警示。 請前往連結並加以閱讀；如果您同意即可按 [繼續]：

    [![前往隱私權和條款的連結；如果您同意，請繼續執行](media/install-privacy-sml.png)](media/install-privacy.png#lightbox)

6. 即會顯示可用工作負載的清單。 選取您想要使用的項目：

    [![選擇您想要安裝的選擇性工作負載功能](media/install-selection-sml.png)](media/install-selection.png#lightbox)

7. 選取完成之後，請按 [安裝] 按鈕。
8. 安裝程式會顯示下載和安裝 Visual Studio for Mac 的進度，並顯示選取的工作負載。 系統可能會提示您輸入密碼，授與安裝所需的權限。

如果您在公司環境安裝時發生網路問題，請檢閱[在防火牆或 Proxy 後方安裝](https://docs.microsoft.com/visualstudio/mac/installation#install-visual-studio-for-mac-behind-a-firewall-or-proxy-server)指示。

深入了解[版本資訊](https://docs.microsoft.com/visualstudio/releasenotes/vs2019-mac-relnotes)中的變更。

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

對於其他工作負載，請參閱[工作負載](workloads.md)頁面。

## <a name="related-video"></a>相關影片

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Acquisition/player]

## <a name="see-also"></a>另請參閱

- [安裝 Visual Studio (在 Windows 上)](/visualstudio/install/install-visual-studio)
