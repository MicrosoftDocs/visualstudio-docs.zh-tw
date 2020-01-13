---
title: 針對 Mac 使用者的設定、安裝和驗證 | Microsoft Docs
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: 22725520-59ba-4f6f-80e4-097b1287a34b
caps.latest.revision: 14
ms.author: crdun
manager: crdun
ms.openlocfilehash: 5a3a05e50cfa17432bb2f31274c9b62c6b843687
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/13/2020
ms.locfileid: "75917952"
---
# <a name="setup-install-and-verifications-for-mac-users"></a>針對 Mac 使用者的設定、安裝和驗證
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題適用於主要在 Mac 上工作的開發人員，這些開發人員會選擇性地在 Mac 上的 Windows 虛擬機器中使用 Visual Studio。 如果您是主要在 Windows 電腦上工作的開發人員，並且需要設定以 iOS 為目標的次要 Mac，請參閱主要的[設定和安裝](../cross-platform/setup-and-install.md)主題。  
  
 若要在 Mac 上使用 Xamarin，您需要下列項目：  
  
- Xamarin 帳戶。 移至[https://www.xamarin.com/](https://www.xamarin.com/) ，然後按一下頁面右上方的 [登**入**]，然後在出現的頁面上按一下 [**建立新帳戶**]。 針對您的 Xamarin 帳戶選取電子郵件地址和密碼。  
  
- 具有 OSX Yosemite 10.10 (含) 以上版本的 Mac，並已安裝 Xcode 7 和 Xamarin 4。  
  
- 下列其中一項設定：  
  
  - **若要在 Mac 上直接執行 Xamarin Studio：** Xamarin Studio 是 Xamarin 的開發環境，可使用 C# 建置 Android、iOS 和 Windows 應用程式。  若要取得 Xamarin Studio 的快速概觀，請參閱 [Xamarin Studio 概觀](https://xamarin.com/studio) (xamarin.com)。  
  
  - **如果您已在 Mac 上設定 Parallels 或 VMWare：** 在 Parallels 或 VMWare 中執行 Windows 以及 Visual Studio 2015 和 Xamarin 4。  在這項設定中，Xamarin 是 Visual Studio 隨附安裝的擴充功能，可讓您使用 Visual Studio 作為開發環境，以使用 C# 建置 Android、iOS 和 WinPhone 應用程式。  請注意，您可以參加 Visual Studio Developer Essentials 計畫，以免費取得 3 個月的 Parallels 訂閱。 請參閱 [Microsoft Visual Studio Dev Essentials 將包含 Parallels Desktop Pro 和 Parallels Access](https://www.parallels.com/blogs/) (Parallels 部落格)。  
  
  本主題提供這些需求的指示。  在安裝程序執行期間，您可以檢閱[了解 Xamarin 的行動裝置開發](../cross-platform/learn-about-mobile-development-with-xamarin.md)主題，以閱讀並留意必要的背景資料。  
  
  **本主題內容：**  
  
- [Mac 設定 (Apple ID、Xcode 和 Xamarin)](#mac)  
  
- [在 Parallels 內設定 Windows (Visual Studio 和 Xamarin)](#windows)  
  
- [驗證您的環境](#verify)  
  
## <a name="mac"></a> Mac 設定 (Apple ID、Xcode 和 Xamarin)  
  
1. 如果您還沒有 Apple ID，請在 [我的 Apple ID](https://appleid.apple.com/) 免費建立一個 ID。 安裝及登入 Xcode 時需要這個 ID。  
  
2. 從 [https://developer.apple.com/xcode/](https://developer.apple.com/xcode/) 下載並安裝 Xcode。  
  
3. 遵循 [安裝和設定 Xamarin.iOS](/xamarin/ios/get-started/installation/mac) (xamarin.com) 上的指示，下載並安裝 Xamarin。  
  
4. 當您在 Windows 和 Mac 電腦上完成安裝 Xamarin 之後，請依照[使用 XMA 連線到 Mac (英文)](/xamarin/ios/get-started/installation/windows/connecting-to-mac) (xamarin.com) 上的指示執行，如此就能在 Windows 電腦上透過 Visual Studio 使用 iOS 和 Mac。  
  
## <a name="windows"></a> 在 Parallels 內設定 Windows (Visual Studio 和 Xamarin)  
  
1. 使用您在 Parallels/VMWare 內設定的 Windows 桌面， [下載並啟動任何 Visual Studio 2015 版本的安裝程式](https://www.visualstudio.com/downloads/download-visual-studio-vs.aspx) (Community、Professional 或 Enterprise)。 Visual Studio 2015 Community 是免費版本，而 Professional 和 Enterprise 版則可試用 30 天。  
  
2. 在安裝程式中，選取 [自訂] 安裝：  
  
     ![選擇 Visual Studio 安裝中的自訂選項](../cross-platform/media/cross-plat-xamarin-setup-1.png "跨平臺 Xamarin 設定1")  
  
3. 核取/取消核取下列方塊：  
  
    1. 核取 [跨平台行動開發] > [C#/.NET (Xamarin)]。 這樣做也會自動選取 [常用工具及軟體開發套件] 下的各種 Android 工具。  
  
         ![選取 [跨&#45;平臺行動開發] 底下的 [Xamarin] 選項](../cross-platform/media/cross-plat-xamarin-setup-2.png "跨平臺 Xamarin 設定2")  
  
    2. 取消核取 [跨平台行動開發] > [Android 版 Microsoft Visual Studio 模擬器]。  
  
4. 按一下 [安裝] 按鈕，允許處理序執行。 同樣地，這需要一些時間才能完成，在這段期間，您可以繼續進行本主題，並瀏覽[了解 Xamarin 的行動裝置開發](../cross-platform/learn-about-mobile-development-with-xamarin.md)。  
  
5. 安裝完成之後，請啟動 Visual Studio，並在出現提示時，以您的 Microsoft 帳戶進行登入 (這是您用於 Windows 的相同帳戶)。 然後透過 [工具] > [選項] > [Xamarin] 或 [工具] > [選項] > [Xamarin] > [其他] 檢查是否有 Xamarin 更新，您會在此找到 [立即檢查] 連結：  
  
     ![在 Visual Studio 選項中檢查 Xamarin 更新](../cross-platform/media/cross-plat-xamarin-setup-3.png "跨平臺 Xamarin 設定3")  
  
    > [!NOTE]
    > 請確定將 Xamarin 更新為版本 4.0.3.214 或更高版本，以避免發生舊版 Xamarin 授權的問題。  如果您嘗試檢查更新，並看到關於 Microsoft 建置工具的錯誤，請參閱 [Xamarin 論壇](https://forums.xamarin.com/discussion/69015/xamarin-update-on-vs-2013-says-i-need-the-build-tools-for-vs-2015)上的討論。
  
6. 當您在 Windows 和 Mac 電腦上完成安裝 Xamarin 之後，請依照[使用 XMA 連線到 Mac (英文)](/xamarin/ios/get-started/installation/windows/connecting-to-mac) (xamarin.com) 上的指示執行，如此就能透過 Visual Studio 使用 iOS。  
  
## <a name="verify"></a> 驗證您的環境  
 安裝程式完成之後，請花幾分鐘的時間來確認一切就緒，以便體驗 Xamarin 開發。  
  
### <a name="xamarin-studio"></a>Xamarin Studio  
 首先，請確定當您巡覽至所提供的連結時，選取了右上角的 [Xamarin Studio] ，以查看 Xamarin 文件的正確版本：  
  
 ![選取 Xamarin Studio 以查看 Xamarin.com 上的正確檔](../cross-platform/media/crossplat-xamarin-mac-1.png "CrossPlat Xamarin Mac 1")  
  
 **Android**  
  
1. 遵循 [建立 Android 專案](https://github.com/xamarin/docs-archive/tree/master/Recipes/android/general/projects/create_an_android_project) (xamarin.com) 上的指示，驗證 Android 專案的建立作業。  
  
2. 透過 [Android Player > 與 Xamarin Studio 整合文件](https://developer.xamarin.com/guides/android/getting_started/installation/android-player/#Integration_with_Xamarin_Studio) (xamarin.com)，來驗證 Android Player 中的偵錯作業。  
  
   **iOS**  
  
3. 遵循 [建立 iOS](https://github.com/xamarin/docs-archive/tree/master/Recipes/ios/general/projects/create_an_ios_project) (xamarin.com) 上的指示，驗證 iOS 專案的建立作業。  
  
4. 透過 [在模擬器中偵錯文件](https://developer.xamarin.com/guides/ios/deployment,_testing,_and_metrics/debugging_in_xamarin_ios/#Debugging_on_the_Simulator) (xamarin.com)，驗證 iOS 模擬器中的偵錯作業。  
  
### <a name="visual-studio"></a>Visual Studio  
 首先，請確定當您巡覽至所提供的連結時，選取了右上角的 [Visual Studio] ，以查看 Xamarin 文件的正確版本：  
  
 ![選取 Visual Studio 以查看 Xamarin.com 上的正確檔](../cross-platform/media/crossplat-xamarin-mac-2.png "CrossPlat Xamarin Mac 2")  
  
 同時透過 [工具] > [Xamarin 帳戶...] 來登入您的 Xamarin 帳戶。  
  
 **Android**  
  
1. 遵循 [建立 Android 專案](https://github.com/xamarin/docs-archive/tree/master/Recipes/android/general/projects/create_an_android_project) (xamarin.com) 上的指示，驗證 Android 專案的建立作業。  
  
2. 驗證 Android 設計工具：在 [方案總管] 的 Android 專案中，開啟 [資源] > [配置] > [Main.axml] 檔案。  
  
   - 如果您收到錯誤，指出「安裝的 Android SDK 太舊」，請在該訊息中按一下 [開啟 Android SDK]，然後選取可用的最新 SDK 版本。 請注意，您必須以系統管理員身分執行 Visual Studio，來更新 SDK。  
  
3. 驗證您可以從 Visual Studio 連接到 Mac 上所安裝的模擬器。  這項驗證的結果是您會在模擬器清單中看見 Xamarin Player，您可以從 Visual Studio 中選取此項目以進行偵錯。  若要這樣做，請遵循 [將 Visual Studio 連接到 Xamarin Android Player](/xamarin/android/deploy-test/debugging/debug-on-emulator?tabs=windows) (xamarin.com) 上的指示。  
  
   **iOS**  
  
4. 請確定您的 Mac 在網路上可用並搭配 Visual Studio，如 [使用 XMA 連接到到 Mac](/xamarin/ios/get-started/installation/windows/connecting-to-mac) (xamarin.com) 中所述。  
  
5. 遵循 [建立 iOS](https://github.com/xamarin/docs-archive/tree/master/Recipes/ios/general/projects/create_an_ios_project) (xamarin.com) 上的指示，驗證 iOS 專案的建立作業。  
  
6. 驗證分鏡腳本設計工具：在方案總管的 iOS 專案中，開啟 **MainStoryboard.storyboard** 檔案。 在此，Visual Studio 會裝載在 Mac 上遠端執行的設計工具。  
  
7. 驗證建置與偵錯：  
  
   1. 以滑鼠右鍵按一下方案總管中的 iOS 專案，然後選取 [設定為啟始專案]。  
  
   2. 如下所示，從 Visual Studio 的 [組建] 下拉式清單中選取 [iPhoneSimulator] 目標。 如果未列出任何模擬器，請在您的 Mac 上啟動 Xcode，選取 [Xcode] -> [喜好設定]，然後按一下 [下載]。 在 [元件] 下，您應該會看到可供下載的模擬器版本。 您可以在 Xamarin 的 [偵錯](https://developer.xamarin.com/guides/ios/deployment,_testing,_and_metrics/debugging_in_xamarin_ios/#Debugging_on_the_Simulator) 頁面 (xamarin.com) 上找到偵錯的其他指示。  
  
        ![選取 Iphonesimulator; 組建目標](../cross-platform/media/crossplat-xamarin-verify-5.png "CrossPlat Xamarin 驗證5")  
  
   3. 如下所示，從 Visual Studio 的 [偵錯] 下拉式清單中選取 [iPhone] 目標，然後按 F5 鍵啟動偵錯工具。 這會在 Mac 上啟動模擬器，以在 Visual Studio 中偵錯時與應用程式進行互動。  
  
        ![選取 iPhone debug 目標](../cross-platform/media/crossplat-xamarin-verify-6.png "CrossPlat Xamarin 驗證6")
