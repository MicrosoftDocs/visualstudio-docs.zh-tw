---
title: 安裝 Visual Studio 2017 for Mac
description: 如何安裝 Visual Studio for Mac 和跨平台開發所需之其他元件的指示。
author: heiligerdankgesang
ms.author: dominicn
ms.date: 11/03/2018
ms.technology: vs-ide-install
ms.assetid: 22B1F2CD-32AE-464D-80AC-C8AB4786B015
ms.custom: video
ms.topic: how-to
ms.openlocfilehash: be799764c3d6913cd2a13c6d631fc3450f8875a0
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2021
ms.locfileid: "98719912"
---
# <a name="install-visual-studio-2017-for-mac"></a>安裝 Visual Studio 2017 for Mac

> [!NOTE]
> 適用于 Mac 的 Visual Studio 2019 [現在已可供使用](installation.md?view=vsmac-2019&preserve-view=true)。 針對舊版的 Visual Studio for Mac，請參閱 Visual Studio [下載頁面](https://my.visualstudio.com/Downloads?q=Visual%20Studio%202017%20for%20Mac)。

## <a name="downgrading-from-visual-studio-2019-for-mac"></a>從 Visual Studio 2019 for Mac 降級嗎？

為了獲得最佳體驗，在降級之前，您應該確定[解除安裝](uninstall.md) Visual Studio 2019 for Mac。 如果您遇到導致您下載的問題，請務必透過[回報問題](report-a-problem.md)讓我們知道。
 
## <a name="requirements"></a>需求

若要在下載 Visual Studio for Mac 時開始開發原生的跨平台應用程式，有必須安裝和設定以做為準備的數個項目。

若要在 Visual Studio 中使用 iOS，您需要下列各項：

- 具有 macOS High Sierra 10.13 或以上版本的 Mac。
- Xcode 9.3 或更新版本。 通常建議使用最新穩定版本。
- Apple ID。 如果您還沒有 Apple 識別碼，可以在 https://appleid.apple.com 建立一個新識別碼。 安裝及登入 Xcode 時需要有 Apple 識別碼。

## <a name="install"></a>安裝

1. 從 [my.visualstudio.com](https://my.visualstudio.com/Downloads?q=Visual%20Studio%202017%20for%20Mac) 下載 Visual Studio for Mac

2. 安裝程式套件下載後，按一下 **VisualStudioForMacInstaller.dmg** 檔案來裝載安裝程式，然後按兩下標誌加以執行，如下圖所示：

   ![[安裝程式] 對話方塊](media/installer-image1.png)

3. 您可能會看到類似下圖的警示對話方塊提示。 在此情況下，按一下 [開啟]：

   ![[警示] 對話方塊](media/installer-image2.png)

4. 安裝程式會檢查您的系統，以驗證哪些元件需要安裝或更新：

   ![評估您的系統](media/installer-image3.png)

5. 您接著會看到 [警示] 對話方塊，要求您確認隱私權和授權條款。 按 [繼續] 按鈕以確認條款：

   ![[授權] 對話方塊](media/installer-image4.png)

6. 安裝程式會顯示遺失且需要下載及安裝的必要元件清單。 從這裡選取您想要下載的產品：

   ![選取項目](media/installer-image5.png)

   如果您不想要安裝所有平台，請使用以下指南以協助您決定要安裝的平台：

   * **使用 Xamarin 的應用程式**：
      - Xamarin.Forms – 選取 [Android] 與 [iOS] 平台。
      - 僅 iOS – 選取 [iOS] 平台 (請注意，您必須安裝 [**Xcode**](https://developer.apple.com/xcode/))。
      - 僅 Android – 選取 [Android] 平台 (請注意，您也必須選取相關聯的相依性)。
      - 僅 Mac – 選取 [macOS] 平台 (請注意，您必須安裝 [**Xcode**](https://developer.apple.com/xcode/))。
      - 完整跨平台的 Xamarin 應用程式 – 選取 [Android]、[iOS] 與 [macOS] 平台。
   * **.NET Core 應用程式** – 選取 [.NET Core] 平台。
   * **ASP.NET Core Web 應用程式** – 選取 [.NET Core] 平台。
   * **跨平台 Unity 遊戲開發** – 除了 Visual Studio for Mac 以外，不需要安裝其他平台。 如需安裝 Unity 延伸模組的詳細資訊，請參閱 [Unity 安裝指南](./setup-vsmac-tools-unity.md)。

   此安裝畫面顯示每個個別的元件的版本和大小。 您可以按一下每個元件，顯示該元件的相依性清單 (適用於 Android)，查看它下載的其他套件 (適用於.NET Core)，或檢視所需的任何其他應用程式 (適用於 iOS 和 macOS)：

   ![Android 其他相依性](media/installer-image6.png)

7. 一旦您滿意您的選擇之後，選取 [安裝及更新] 按鈕以啟動安裝程序。

8. 安裝程式會開始所選取項目的下載與安裝程序：

   ![開始安裝](media/installer-image7.png)

   ![下載 Xamarin.Mac](media/installer-image8.png)

   ![完成安裝](media/installer-image9.png)

9. 您可能會被提示要提高完成安裝所需之個別元件的必要權限。 在這裡輸入您的系統管理員認證以繼續安裝程序：

   ![輸入權限以繼續安裝程式](media/installer-image10.png)

10. 安裝成功之後，您可以按 [開始]，開始在 Visual Studio 中開發應用程式：

    ![開啟 Visual Studio](media/installer-image11.png)

> [!NOTE]
> 如果您在原始安裝期間選擇不安裝平台或工具 (在步驟 #6 中取消選取它)，當您稍後想要新增元件時，必須再次執行[安裝程式](https://visualstudio.microsoft.com/vs/)。

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

1. [使用 Xamarin Android SDK 管理員](https://developer.xamarin.com/guides/android/getting_started/installation/android-sdk/?ide=xs)
2. [Android SDK 模擬器](https://developer.xamarin.com/guides/android/getting_started/installation/android-emulator/)
4. [設定裝置以進行開發](https://developer.xamarin.com/guides/android/getting_started/installation/set_up_device_for_development/)

### <a name="net-core-apps-aspnet-core-web-apps-unity-game-development"></a>.NET Core 應用程式、ASP.NET Core Web 應用程式、Unity 遊戲開發

對於其他工作負載，請參閱[工作負載](./workloads.md)頁面。

## <a name="related-video"></a>相關影片

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Acquisition/player]

## <a name="see-also"></a>另請參閱

- [安裝 Visual Studio 2017 (在 Windows 上)](/visualstudio/install/install-visual-studio)