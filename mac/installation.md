---
title: 安裝 Visual Studio 2019 for Mac
description: 如何安裝 Visual Studio 2019 for Mac 及其他跨平台開發所需元件的指示。
author: heiligerdankgesang
ms.author: dominicn
ms.date: 03/04/2021
ms.technology: vs-ide-install
ms.assetid: 22B1F2CD-32AE-464D-80AC-C8AB4786B015
ms.custom: video
ms.topic: how-to
ms.openlocfilehash: 653e653a0574da52c0030b06c7a8c13b436ed686
ms.sourcegitcommit: 4bf7d82eb3a837ad5d1ae5c110039cbf74258f18
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/03/2021
ms.locfileid: "106273410"
---
# <a name="install-visual-studio-2019-for-mac"></a>安裝 Visual Studio 2019 for Mac

若要開始在 macOS 上開發原生、跨平台的 .NET 應用程式，請遵循下方步驟安裝 Visual Studio 2019 for Mac。

 > [!div class="button"]
 > [下載 Visual Studio for Mac](https://visualstudio.microsoft.com/vs/mac/)

## <a name="requirements"></a>規格需求

- 具有 macOS High Sierra 10.13 或以上版本的 Mac。

若要建置適用於 iOS 或 macOS 的 Xamarin 應用程式，您還需要：

- 與最新版本的 Xcode 相容的 Mac。 請參閱 Apple 的 [最低需求檔](https://developer.apple.com/support/xcode/)
- 最新版本的 [Xcode](https://developer.apple.com/xcode)。 如果您的 Mac 與最新版本不相容，則可能會 [使用較舊版本的 Xcode](https://docs.microsoft.com/xamarin/ios/troubleshooting/questions/old-version-xcode) 。
- Apple ID。 如果您還沒有 Apple 識別碼，可以在 https://appleid.apple.com 建立一個新識別碼。 安裝及登入 Xcode 時需要有 Apple 識別碼。

## <a name="installation-instructions"></a>安裝指示

1. 從 [Visual Studio for Mac 下載頁面](https://visualstudio.microsoft.com/vs/mac/)下載安裝程式。
2. 下載完成後，按一下 **VisualStudioforMacInstaller.dmg** 裝載安裝程式，然後按兩下箭號標誌加以執行：

    [![按一下大型箭號以開始安裝](media/install-installer-sml.png)](media/install-installer.png#lightbox)

3. 您可能會看到要從網際網路下載應用程式的相關警告。 按一下 [開啟]。
4. 等候安裝程式檢查您的系統：

    [![安裝程式會檢查您的系統是否有安裝的元件](media/install-checking-sml.png)](media/install-checking.png#lightbox)

5. 系統會出現要求您確認隱私權和授權條款的警示。 請前往連結並加以閱讀；如果您同意即可按 [繼續]：

    [![遵循隱私權和條款的連結，如果您同意，請繼續進行](media/install-privacy.png)](media/install-privacy.png#lightbox)

6. 即會顯示可用工作負載的清單。 選取您想要使用的元件：

    [![螢幕擷取畫面： Visual Studio Mac 安裝程式中的 [您要安裝什麼？] 畫面，其中顯示可供安裝的元件清單。](media/install-selection.png)](media/install-selection.png#lightbox)

   如果您不想要安裝所有平台，請使用以下指南以協助您決定要安裝的平台：

   |應用程式類型  |目標  |選取  |備註  |
   |---------|---------|---------|---------|
   |**使用 Xamarin 的應用程式**| Xamarin.Forms|選取 **Android** 和 **iOS** 平臺 |您將需要安裝 [ **Xcode**](https://developer.apple.com/xcode/) |
   ||僅限 iOS|選取 **iOS** 平臺|您將需要安裝 [ **Xcode**](https://developer.apple.com/xcode/)|
   ||僅 Android|選取 **Android** 平臺|請注意，您也應該選取相關的相依性|
   ||僅限 Mac|選取 **macOS (Cocoa)** platform|您將需要安裝 [ **Xcode**](https://developer.apple.com/xcode/)|
   |**.NET Core 應用程式**|         |選取 [ **.Net Core** 平臺]。|         |
   |**ASP.NET Core Web 應用程式**|         |選取 [ **.Net Core** 平臺]。|         |
   |**Azure Functions**|         |選取 [ **.Net Core** 平臺]。|         |
   |**跨平台 Unity 遊戲開發**|         |除了 Visual Studio for Mac 之外，不需要安裝其他平臺。| 如需安裝 Unity 延伸模組的詳細資訊，請參閱 [Unity 安裝指南](./setup-vsmac-tools-unity.md)。|

7. 選取完成之後，請按 [安裝] 按鈕。
8. 安裝程式會顯示下載和安裝 Visual Studio for Mac 的進度，並顯示選取的工作負載。 系統會提示您輸入密碼，以授與安裝所需的許可權。：

    [![Visual Studio Mac 安裝程式的螢幕擷取畫面，其中顯示適用于 Mac 的 .NET 開發人員工具組的安裝進度畫面。](media/installation-progress.png)](media/installation-progress.png#lightbox)

9. 安裝之後，Visual Studio for Mac 將會提示您登入並選取您想要使用的金鑰系結，以個人化您的安裝：

    [![登入 IDE](media/ide-tour-2019-start-signin.png)](media/ide-tour-2019-start-signin.png#lightbox)

    [![選擇您想要使用的鍵盤快速鍵](media/ide-tour-2019-keyboard-shortcut.png)](media/ide-tour-2019-keyboard-shortcut.png#lightbox)

如果您在公司環境安裝時發生網路問題，請檢閱[在防火牆或 Proxy 後方安裝](#install-visual-studio-for-mac-behind-a-firewall-or-proxy-server)指示。

深入了解[版本資訊](/visualstudio/releasenotes/vs2019-mac-relnotes)中的變更。

> [!NOTE]
> 如果您在原始安裝期間選擇不安裝平台或工具 (在步驟 #6 中取消選取它)，當您稍後想要新增元件時，必須再次執行安裝程式。

## <a name="install-visual-studio-for-mac-behind-a-firewall-or-proxy-server"></a>將 Visual Studio for Mac 安裝在防火牆或 Proxy 伺服器後方

若要將 Visual Studio for Mac 安裝在防火牆後方，某些端點必須設為可供存取，才能允許下載您軟體所需的工具和更新。

將您的網路設定為允許存取下列位置：

- [Visual Studio 端點](./install-behind-a-firewall-or-proxy-server.md)

## <a name="next-steps"></a>下一步

安裝 Visual Studio for Mac 可讓您開始撰寫應用程式的程式碼。 以下指示提供您下一步撰寫及部署專案的逐步指示。

### <a name="ios"></a>iOS

1. [Hello, iOS](https://docs.microsoft.com//xamarin/ios/get-started/hello-ios/)
2. [裝置部署](https://docs.microsoft.com/xamarin/ios/get-started/installation/device-provisioning/) \(英文\) (在裝置上執行您的應用程式)。

### <a name="android"></a>Android

1. [Hello, Android](https://docs.microsoft.com/xamarin/android/get-started/hello-android/)
2. [使用 Xamarin Android SDK 管理員](https://docs.microsoft.com/xamarin/android/get-started/installation/android-sdk?tabs=macos)
3. [Android SDK 模擬器](https://docs.microsoft.com/xamarin/android/get-started/installation/android-emulator/)
4. [設定裝置以進行開發](https://docs.microsoft.com/xamarin/android/get-started/installation/set-up-device-for-development)

### <a name="xamarinforms"></a>Xamarin.Forms

使用 Xamarin 建立原生跨平臺應用程式：

1. [Xamarin. 表單快速入門](https://docs.microsoft.com/xamarin/get-started/quickstarts/)

### <a name="net-core-apps-aspnet-core-web-apps-unity-game-development"></a>.NET Core 應用程式、ASP.NET Core Web 應用程式、Unity 遊戲開發

對於其他工作負載，請參閱[工作負載](workloads.md)頁面。

## <a name="related-video"></a>相關影片

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Acquisition/player]

## <a name="see-also"></a>另請參閱

- [安裝 Visual Studio (在 Windows 上)](/visualstudio/install/install-visual-studio)
