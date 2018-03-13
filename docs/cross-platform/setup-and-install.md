---
title: "安裝 Xamarin for Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 04/13/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2cfcad00-352c-4161-814c-f5ae32d8ada8
ms.technology: vs-ide-mobile
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- xamarin
ms.openlocfilehash: bcaa49552c0e904b07cc90f3ae7e44aaa58a3895
ms.sourcegitcommit: 8cbe6b38b810529a6c364d0f1918e5c71dee2c68
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2018
---
# <a name="setup-and-install"></a>設定和安裝

若要建置 Xamarin 從通用 C#/.NET 程式碼基底建置原生 iOS、Android 和 Windows 應用程式，您需要下列項目：

-   若要使用 Windows 和 Android 應用程式：一部已安裝 Visual Studio 2017 或 2015 和 Xamarin 的 Windows 開發電腦。 您也可以遵循[直接安裝 Xamarin](https://developer.xamarin.com/guides/cross-platform/getting_started/requirements/#install) (xamarin.com) 的指示使用 Visual Studio 2013。

-   若要使用 iOS 應用程式：具有 macOS Sierra 10.12 或更新版本的 Mac，並已安裝 XCode 和 Xamarin。

 您可以同時設定 Windows 和 Mac 電腦，並在安裝程式執行期間瀏覽[了解 Xamarin 的行動裝置開發](../cross-platform/learn-about-mobile-development-with-xamarin.md)，以閱讀並留意必要的背景資料。

如果您在執行此設定和安裝之後遇到使用 Xamarin 的問題，請在 [forums.xamarin.com](http://forums.xamarin.com/) 上提出您的問題。

> [!NOTE]
> 截至 2016 年 3 月 31 日，所有 Visual Studio 版本中都會免費隨附所有的 Xamarin，不需要個別授權。 適用於 Mac 的 Xamarin Studio 社群也是對於學生、OSS 開發人員和小型團隊而言，也是一項免費資源。 請注意，如果您目前安裝的 Visual Studio 是以較早的 Xamarin 授權所設定，則您必須將 Xamarin 更新到版本 4.0.3.214 或更高版本。 若要執行此動作，移至 [工具] > [選項] > [Xamarin] > [其他]、按一下 [立即檢查] 連結，然後下載 4.0.3.214 更新。 當您重新啟動 Visual Studio 時，移至 [工具] > [Xamarin 帳戶...]，您應該會看到更新的狀態。

##  <a name="prereq"></a> 必要條件

###  <a name="for-targeting-windows-and-android"></a>以 Windows 和 Android 為目標

1.  建議︰執行 Windows 8 或更新版本的實體 Windows 電腦 (不是 VM)，以取得最佳的 Android 模擬器效能。 (我們是否曾提到您需要實體電腦，而不是 VM？)

2.  您可以使用 Windows 7 或舊版電腦，在此情況下，您將使用 Android 版的 Xamarin Player 作為模擬器。

3. 不論是何種組態，您一律都能在連接的實體裝置上直接執行應用程式。

### <a name="for-targeting-ios"></a>以 iOS 為目標

1.  具有 macOS Sierra 並執行 macOS 10.12 或更新版本 (需要 Xcode 8.3) 的已連網 Mac 或 Mac mini。

2.  在 Windows (7+) 電腦上使用 Visual Studio 做為主要開發環境時，只有在編譯和偵錯 iOS 應用程式、連接到 iOS 模擬器或行動網卡，以及在 Visual Studio 中使用分鏡腳本設計工具來設計使用者介面時，才需要用到網路上的 Mac。 舊版 Mac 模型就能完全滿足這個次要角色。

##  <a name="windows"></a> Windows 設定 (Visual Studio 和 Xamarin)

> [!TIP]
> 這些指示適用於 Visual Studio 2017。 若為 Visual Studio 2015，請參閱 [MSDN](setup-and-install.md)。 若要使用 Xamarin 搭配 Visual Studio 2013 (必須有 Update 2)，請遵循[直接安裝 Xamarin (英文)](https://developer.xamarin.com/guides/cross-platform/getting_started/requirements/#install) (xamarin.com) 的指示。

1.  [下載並啟動任何 Visual Studio 2017 版本的安裝程式](https://www.visualstudio.com/downloads/) (Community、Professional 或 Enterprise)。 Visual Studio 2017 Community 是免費版本，而 Professional 和 Enterprise 版則可試用 30 天，之後您必須購買授權。

    - 如已安裝 Visual Studio 2017，請從 [開始] 功能表執行 **Visual Studio 安裝程式**。

2.  在安裝程式中，按一下 [更多] 按鈕，然後選擇 [修改]：

    ![在 Visual Studio 安裝中選擇 [修改] 選項](../cross-platform/media/cross-plat-xamarin-setup-1a.png "跨平台 Xamarin 設定 1")

3.  核取下列方塊：

    - [行動裝置與遊戲] > [使用 .NET 進行行動開發]。 這樣做也會自動選取 [常用工具及軟體開發套件] 下的各種 Android 工具。 此選項應該也會更新任何現有的 Xamarin 安裝。

        ![選取 [遊戲與行動開發] 下的 [行動開發] 選項](../cross-platform/media/cross-plat-xamarin-setup-2a.png "跨平台 Xamarin 設定 2")

    - (選擇性) [Windows] > [通用 Windows 平台開發]。 這包括安裝模擬器映像的選項，需要較長的時間下載；您可以稍後隨時返回 Visual Studio 安裝程式以新增這些選項。

4.  按一下 [修改] 按鈕，允許處理序執行。 同樣地，這需要一些時間才能完成，在這段期間，您可以繼續進行 Mac 設定指示，並瀏覽[了解 Xamarin 的行動裝置開發](../cross-platform/learn-about-mobile-development-with-xamarin.md)。

5.  安裝完成之後，請啟動 Visual Studio，並在出現提示時，以您的 Microsoft 帳戶進行登入 (這是您用於 Windows 的相同帳戶)。

6.  若要測試 Android 應用程式但沒有實體裝置，請使用 [Android SDK 模擬器](https://developer.xamarin.com/guides/android/deployment,_testing,_and_metrics/debug-on-emulator/android-sdk-emulator/)。 請參閱下列注意事項。

> [!NOTE]
> **Windows 電腦上的模擬器**：由於 CPU 一次只支援一種虛擬化技術，因此建議在開發電腦上只使用一種技術。 虛擬化技術主要有三種：Hyper-V (供 Android 版 Visual Studio 模擬器和 Windows Phone 模擬器使用)、Virtual Box (供 Genymotion 使用) 和 Intel HAXM (供 Android SDK 模擬器使用)。 由於 Hyper-V 和 Virtual Box 之間有各種問題，最好是在任何指定的電腦上只使用一種模擬器類型，因此上述建議在 Windows 8 (含) 以上版本的電腦上使用 Hyper-V，但在 Windows 7 (含) 以前版本上以及在 Mac 上執行 Windows 時，則使用 Intel HAXM 模擬器。

##  <a name="mac"></a> Mac 設定 (Apple ID、Xcode 和 Xamarin)

1.  如果您還沒有 Apple ID，請前往 [https://appleid.apple.com](https://appleid.apple.com/) 免費建立一個 ID。 安裝及登入 Xcode 時需要這個 ID。

2.  從  [https://developer.apple.com/xcode/](https://developer.apple.com/xcode/)下載並安裝 Xcode，並依照 [Adding Your Account to XCode](https://developer.apple.com/library/content/documentation/IDEs/Conceptual/AppStoreDistributionTutorial/AddingYourAccounttoXcode/AddingYourAccounttoXcode.html#//apple_ref/doc/uid/TP40013839-CH40-SW1) (apple.com) 中所述，加入您的 Apple ID。

3.  遵循 [安裝和設定 Xamarin.iOS](http://developer.xamarin.com/guides/ios/getting_started/installation/mac/) (xamarin.com) 上的指示，下載並安裝 Xamarin。

4.  當您在 Windows 和 Mac 電腦上完成安裝 Xamarin 之後，請遵循[連線到 Mac](http://developer.xamarin.com/guides/ios/getting_started/installation/windows/xamarin-mac-agent/) (xamarin.com) 上的指示執行，如此就能在 Windows 電腦上透過 Visual Studio 使用 iOS 和 Mac。

    請注意，這兩部電腦必須位於相同的區域網路中。