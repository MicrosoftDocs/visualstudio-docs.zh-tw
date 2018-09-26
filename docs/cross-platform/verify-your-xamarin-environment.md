---
title: 驗證您的 Xamarin 環境 | Microsoft Docs
ms.custom: ''
ms.date: 03/30/2018
ms.topic: conceptual
ms.assetid: fd39882e-06d1-4b39-80d2-4d07b6e4f8f5
ms.prod: visual-studio-dev15
ms.technology: vs-ide-mobile
author: conceptdev
ms.author: crdun
manager: crdun
ms.workload:
- xamarin
ms.openlocfilehash: e46da7cf39ad816f70454983c56dd5751981f741
ms.sourcegitcommit: 9765b3fcf89375ca499afd9fc42cf4645b66a8a2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2018
ms.locfileid: "46495751"
---
# <a name="verify-your-xamarin-environment"></a>驗證您的 Xamarin 環境

安裝程式完成之後 (請參閱 [Setup and install](../cross-platform/setup-and-install.md))，請花幾分鐘的時間來確認一切就緒，以便體驗 Xamarin 開發。

 完成安裝驗證之後，請嘗試下列其中一個或兩個逐步解說：

-   [了解在 Visual Studio 中建置 Xamarin.Forms 應用程式的基本概念](../cross-platform/learn-app-building-basics-with-xamarin-forms-in-visual-studio.md)，以建置 Xamarin.Forms 應用程式。

-   [使用 Visual Studio 的 Xamarin 建置具有原生 UI 的應用程式](../cross-platform/build-apps-with-native-ui-using-xamarin-in-visual-studio.md)，以在每個平台上使用原生使用者介面，但共用 .NET Standard 程式庫中的一些程式碼。

## <a name="all-platforms"></a>所有平台

在 Visual Studio 中，先選取 [工具] > [擴充功能和更新]，然後檢查是否有任何 Xamarin 元件需要更新。

接著，在 Visual Studio 中使用 [檔案] > [新增專案] 來建立新的 Xamarin.Forms 方案。 在對話方塊中，展開 [Visual C#] > [跨平台]，選取 [行動應用程式 (Xamarin.Forms)]，然後按一下 [確定]。 在下一個對話方塊中，選取 [空白應用程式]。 在 [程式碼共用策略] 底下，選取 [.NET Standard]。 按一下 [確定 **Deploying Office Solutions**]。

這些動作會建立一個含有四個專案的方案：共用的 .NET Standard 2.0 程式庫專案，以及 Android、iOS 和「通用 Windows 平台」(UWP) 的應用程式專案：

![從空白應用程式 Xamarin.Forms 範本建立新專案的結果](../cross-platform/media/crossplat-xamarin-verify-1.png "CrossPlat Xamarin 驗證 1")

## <a name="android"></a>Android

1. 移至 [工具] > [Android] > [Android SDK 管理員] 來確認您已安裝最新的 Android SDK Tools。 安裝最新版的 Android SDK Tools、Android SDK 平台工具，以及 Android SDK 建置工具。 並不一定要安裝最新的 Android API 層級。 您所需的 API 層級取決於要作為目標的平台層級。 通常，安裝 Xamarin 就會安裝它所需的 Android 平台層級。

2.  在裝置或模擬器上驗證建置與偵錯：

    -   以滑鼠右鍵按一下方案總管中的 Android 專案，然後選取 [設定為啟始專案] 。

    -   在工具列中，您應該會看到一個下拉式清單，其中含有可用的 Android 裝置和模擬器清單。

    在裝置 [設定] 頁面的 [開發人員選項] 中，必須針對 USB 偵錯啟用 Android 裝置。 接著，透過 USB 纜線將此裝置連結至電腦。

    此外，也會列出模擬器。 請選取其中一個裝置或 Visual Studio 模擬器：

  ![選取 Android 版 Visual Studio 模擬器作為偵錯目標](../cross-platform/media/crossplat-xamarin-verify-3.png "CrossPlat Xamarin 驗證 3")

  如需詳細資訊，請參閱 Microsoft DevOps 部落格上的 [Introducing Visual Studio's Emulator for Android](https://blogs.msdn.microsoft.com/devops/2014/11/12/introducing-visual-studios-emulator-for-android/) (Visual Studio 的 Android 模擬器簡介)。 若在讓模擬器運作時發生問題，請參閱[針對 Android 版 Visual Studio 模擬器進行疑難排解](../cross-platform/troubleshooting-the-visual-studio-emulator-for-android.md)。 您也可以選取 [工具] > [Android] > [Android 模擬器管理員]，為模擬器建立新的裝置設定檔。

3. 按 **F5** 來編譯程式並部署至 Android 裝置或模擬器。

## <a name="windows"></a>Windows

1.  在 [方案總管] 中的 [通用 Windows] 專案上按一下滑鼠右鍵，然後選取 [設定為啟始專案]。

2.  在 [方案平台] 下拉式清單中，選取 [x86] 或 [x64]。 選取 [本機電腦]。

3.  按 **F5** 將程式部署至桌面。

## <a name="ios"></a>iOS

1.  確定您的 Mac 在網路上可用並已與 Visual Studio 配對，如[連線到 Mac](/xamarin/ios/get-started/installation/windows/connecting-to-mac/)所述。

2.  以滑鼠右鍵按一下方案總管中的 iOS 專案，然後選取 [設定為啟始專案] 。

3.  如下所示，從 Visual Studio 的 [組建] 下拉式清單中選取 [iPhoneSimulator] 目標；如果具有繫連至 Mac 的行動網卡，請選取 [iPhone] 目標。

 ![選取 iPhoneSimulator 建置目標](../cross-platform/media/crossplat-xamarin-verify-5.png "CrossPlat Xamarin 驗證 5")

 如果未列出任何模擬器，請在您的 Mac 上啟動 Xcode，選取 [Xcode] >  [喜好設定]，然後按一下 [下載]。 在 [元件] 標題底下，您應該會看到可供下載的模擬器版本。 您可以在 [iOS 偵錯](/xamarin/ios/deploy-test/debugging-in-xamarin-ios)頁面上找到其他偵錯指示。

4.  從 Visual Studio 下拉式清單中選取一個模擬器裝置目標：

 ![選取 iPhone 偵錯目標](../cross-platform/media/crossplat-xamarin-verify-6.png "CrossPlat Xamarin 驗證 6")

5. 按 **F5** 來啟動偵錯工具。 模擬器會在 Mac 上啟動，您將在該處與應用程式進行互動，而在 Visual Studio 中進行偵錯。 如果您有連接到 Mac 的實體 iPhone 或 iPad，清單上也會顯示這些裝置，您可以改為選取它們。 如果您沒有看到列出任何裝置或模擬器，請檢查與 Mac 的連線。 請檢閱上面步驟 1 中所列的文章，或移至 [工具] > [iOS] > [與 Mac 配對]

6.  如果您在連線到 Mac 時發生問題，請參閱[連線疑難排解](/xamarin/ios/get-started/installation/windows/connecting-to-mac/troubleshooting/)。

7.  如果您看到錯誤指出「沒有任何已安裝的佈建設定檔符合已安裝的 iOS 簽署金鑰」，請嘗試下列建議：

  - 依照[將您的帳戶加入 Xcode 中](https://developer.apple.com/library/content/documentation/IDEs/Conceptual/AppStoreDistributionTutorial/AddingYourAccounttoXcode/AddingYourAccounttoXcode.html#//apple_ref/doc/uid/TP40013839-CH40-SW1) (apple.com) 所述，檢查您在 Mac 上的 Apple ID 帳戶是否已加入 Xcode 中。  加入您的帳戶之後，請務必重新啟動 Visual Studio 和 Xcode。

  - 確認在 [iOS 套件組合簽署] 索引標籤的 iOS 專案屬性中，使用中偵錯組態的 [自訂權益] 欄位是空的。  注意：如果遇到上述錯誤訊息，只能嘗試移除此設定。

  ![CrossPlat Xamarin 驗證 8](../cross-platform/media/crossplat-xamarin-verify-8.png "CrossPlat Xamarin 驗證 8")
