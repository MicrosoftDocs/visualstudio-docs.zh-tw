---
title: 設定和安裝 | Microsoft Docs
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: 2cfcad00-352c-4161-814c-f5ae32d8ada8
caps.latest.revision: 19
ms.author: crdun
manager: crdun
ms.openlocfilehash: 6f0282e94d252040f05091ddb25c17857c3a74b6
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/17/2019
ms.locfileid: "59663855"
---
# <a name="setup-and-install"></a>設定和安裝
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

若要建置 Xamarin 從通用 C#/.NET 程式碼基底建置原生 iOS、Android 和 Windows 應用程式，您需要下列項目：  
  
- 若要使用 Windows 和 Android 應用程式：一部已安裝 Visual Studio 2015 和 Xamarin 4 的 Windows 開發電腦 (請參閱下列注意事項) (您也可以依照[直接安裝 Xamarin (英文)](https://developer.xamarin.com/guides/cross-platform/getting_started/requirements/#install) (xamarin.com) 的指示來使用 Visual Studio 2013)。   
  
- 若要使用 iOS 應用程式：一部具有 OS X Yosemite 10.10.5 (含) 以上版本的 Mac，並已安裝 XCode 和 Xamarin。  
  
  您可以同時設定 Windows 和 Mac 電腦，並在安裝程式執行期間瀏覽[了解 Xamarin 的行動裝置開發](../cross-platform/learn-about-mobile-development-with-xamarin.md)，以閱讀並留意必要的背景資料。  
 
如果您在執行此設定和安裝之後遇到使用 Xamarin 的問題，請在 [forums.xamarin.com](http://forums.xamarin.com/) 上提出您的問題。
  
> [!NOTE]
>  截至 2016 年 3 月 31 日，所有 Visual Studio 版本中都會免費隨附所有的 Xamarin，不需要個別授權。 適用於 Mac 的 Xamarin Studio 社群也是對於學生、OSS 開發人員和小型團隊而言，也是一項免費資源。 請注意，如果您目前安裝的 Visual Studio 是以較早的 Xamarin 授權所設定，則您必須將 Xamarin 更新到版本 4.0.3.214 或更高版本。 若要執行此動作，移至 [工具] > [選項] > [Xamarin] > [其他]、按一下 [立即檢查] 連結，然後下載 4.0.3.214 更新。 當您重新啟動 Visual Studio 時，移至 [工具] > [Xamarin 帳戶...]，您應該會看到更新的狀態。  
  
 **本主題內容：**  
  
-   [必要條件](#prereq)  
  
-   [Windows 設定 (Visual Studio 和 Xamarin)](#windows)  
  
-   [Mac 設定 (Apple ID、Xcode 和 Xamarin)](#mac)  
  
##  <a name="prereq"></a> 必要條件  
  
1.  以 Windows 和 Android 為目標：  
  
    1.  建議使用：執行 Windows 8 (含) 以後版本的 Windows 實體電腦 (而不是 VM)，如果您沒有 Android 裝置，可允許使用快速、Hyper-V 架構的 Android 版 Visual Studio 模擬器。 (我們是否曾提到您需要實體電腦，而不是 VM？)  
  
    1.  您可以使用 Windows 7 或舊版電腦，在此情況下，您將使用 Android 版的 Xamarin Player 做為模擬器。 
    
    1. 不論是何種組態，您一律都能在連接的實體裝置上直接執行應用程式。  
  
1.  以 iOS 為目標：  
  
    1.  網路上具有 OS X Yosemite 並執行 OS X 10.10.5 (含) 以後版本 (Xcode 7.1 的必要項) 的 Mac 或 Mac mini。  
  
    1.  在 Windows (7+) 電腦上使用 Visual Studio 做為主要開發環境時，只有在編譯和偵錯 iOS 應用程式、連接到 iOS 模擬器或行動網卡，以及在 Visual Studio 中使用分鏡腳本設計工具來設計使用者介面時，才需要用到網路上的 Mac。 舊版 Mac 模型就能完全滿足這個次要角色。  
  
##  <a name="windows"></a> Windows 設定 (Visual Studio 和 Xamarin)  
  
> [!TIP]
>  這些指示適用於 Visual Studio 2015。 若要使用 Xamarin 搭配 Visual Studio 2013 (Update 2 是必要項)，請依照[直接安裝 Xamarin (英文)](https://developer.xamarin.com/guides/cross-platform/getting_started/requirements/#install) (xamarin.com) 的指示執行。  
  
1. [下載並啟動任何 Visual Studio 2015 版本的安裝程式](https://www.visualstudio.com/downloads/download-visual-studio-vs.aspx) (Community、Professional 或 Enterprise)。 Visual Studio 2015 Community 是免費版本，而 Professional 和 Enterprise 版則可試用 30 天，之後您必須購買授權。  
  
   1.  如果您已經安裝 Visual Studio，請開啟 [控制台] > [程式和功能]、選擇 [Visual Studio 2015] 項目，然後按一下 [變更]。 當安裝程式開啟時，按一下 [修改]，直接跳到以下的步驟 3。  
  
2. (僅限新的安裝) 在安裝程式中，選取 [自訂]  安裝：  
  
    ![在 Visual Studio 安裝中選擇 [自訂] 選項](../cross-platform/media/cross-plat-xamarin-setup-1.png "跨平台 Xamarin 設定 1")  
  
3. 核取下列方塊：  
  
   1.  [跨平台行動開發] > [C#/.NET (Xamarin)]。 這樣做也會自動選取 [常用工具及軟體開發套件] 下的各種 Android 工具。 此選項應該也會更新任何現有的 Xamarin 安裝。  
  
        ![在 [跨平台行動開發] 下選取 Xamarin 選項](../cross-platform/media/cross-plat-xamarin-setup-2.png "跨平台 Xamarin 設定 2")  
  
   2.  適用於 Windows 8 +:**跨平台行動開發 > Microsoft Visual Studio Emulator for Android**。 注意：如果您要使用 Windows 7 或舊版電腦，或在 Mac 上執行 Windows，請務必「取消核取」這個選項。 請參閱步驟 5 之後的＜Windows 電腦上的模擬器相關注意事項＞。 如果您只想在 Android 實體裝置上進行偵錯，也可以讓此選項保留未核取狀態。  
  
   3.  (選擇性) 如果您打算以 Windows 裝置為目標，也要核取 [Windows 及 Web 程式開發] > [通用 Windows 應用程式開發工具] 及 (或) [Windows 8.1 及 Windows Phone 8.0/8.1 工具]。 其中包括安裝模擬器映像的選項，需要較長的時間下載；您可以稍後隨時返回 Visual Studio 安裝程式以加入這些選項。  
  
4. 按一下 [安裝] 按鈕，允許處理序執行。 同樣地，這需要一些時間才能完成，在這段期間，您可以繼續進行 Mac 設定指示，並瀏覽[了解 Xamarin 的行動裝置開發](../cross-platform/learn-about-mobile-development-with-xamarin.md)。  
  
5. 安裝完成之後，請啟動 Visual Studio，並在出現提示時，以您的 Microsoft 帳戶進行登入 (這是您用於 Windows 的相同帳戶)。 然後透過 [工具] > [選項] > [Xamarin] 或 [工具] > [選項] > [Xamarin] > [其他] 檢查是否有 Xamarin 更新，您會在此找到 [立即檢查] 連結：  
  
    ![在 Visual Studio 選項中檢查 Xamarin 更新](../cross-platform/media/cross-plat-xamarin-setup-3.png "跨平台 Xamarin 設定 3")  
  
   > [!NOTE]
   >  如先前所述，請確定將 Xamarin 更新為版本 4.0.3.214 或更高版本，以避免發生舊版 Xamarin 授權的問題。  

   如果您未在 [工具] > [選項] 中看見 Xamarin 的選項，請仔細檢查您的安裝，或嘗試重新啟動 Visual Studio。 您也可以在 [選項] 對話方塊中搜尋 Xamarin。
      
6. 針對 Windows 7 (含) 之前版本，或是在 Mac 上執行 Windows，如果您沒有實體裝置，請使用 [Android SDK 模擬器 (英文)](https://developer.xamarin.com/guides/android/deployment,_testing,_and_metrics/debug-on-emulator/android-sdk-emulator/)。 請參閱下列注意事項。  
  
   **請注意在 Windows 上的模擬器相關電腦：** 由於 Cpu 一次支援只有一個虛擬化技術，因此最好在開發電腦上有一個使用中。 虛擬化技術主要有三種：Hyper-V (供 Android 版 Visual Studio 模擬器和 Windows Phone 模擬器使用)、Virtual Box (供 Genymotion 使用) 和 Intel HAXM (供 Android SDK 模擬器使用)。 由於 Hyper-V 和 Virtual Box 之間有各種問題，最好是在任何指定的電腦上只使用一種模擬器類型，因此上述建議在 Windows 8 (含) 以上版本的電腦上使用 Hyper-V，但在 Windows 7 (含) 以前版本上以及在 Mac 上執行 Windows 時，則使用 Intel HAXM 模擬器。  
  
##  <a name="mac"></a> Mac 設定 (Apple ID、Xcode 和 Xamarin)  
  
1.  如果您還沒有 Apple ID，請在 [https://appleid.apple.com](https://appleid.apple.com/) 建立免費的 Apple ID。 安裝及登入 Xcode 時需要這個 ID。  
  
2.  從 [https://developer.apple.com/xcode/](https://developer.apple.com/xcode/) 下載並安裝 Xcode，然後遵循[將您的帳戶新增至 XCode](https://developer.apple.com/library/content/documentation/IDEs/Conceptual/AppStoreDistributionTutorial/AddingYourAccounttoXcode/AddingYourAccounttoXcode.html#//apple_ref/doc/uid/TP40013839-CH40-SW1) (apple.com) 中所述，新增您的 Apple 識別碼。  
  
3.  遵循 [安裝和設定 Xamarin.iOS](http://developer.xamarin.com/guides/ios/getting_started/installation/mac/) (xamarin.com) 上的指示，下載並安裝 Xamarin。  
  
4.  當您在 Windows 和 Mac 電腦上完成安裝 Xamarin 之後，請依照[連線到 Mac (英文)](http://developer.xamarin.com/guides/ios/getting_started/installation/windows/xamarin-mac-agent/) (xamarin.com) 上的指示執行，如此就能在 Windows 電腦上透過 Visual Studio 使用 iOS 和 Mac。  
  
     請注意，這兩部電腦必須位於相同的區域網路中。
