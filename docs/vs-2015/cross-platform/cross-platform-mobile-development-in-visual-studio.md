---
title: 跨平台行動裝置程式開發
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8202717a-e990-45cf-b092-438651ccb38a
caps.latest.revision: 66
ms.author: crdun
manager: crdun
ms.openlocfilehash: c259a8c84a59f99f647f908ded8b272ed4e943a0
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53858827"
---
# <a name="cross-platform-mobile-development-in-visual-studio"></a>Visual Studio 中的跨平台行動裝置應用程式開發
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]


您可以使用 Visual Studio 建置 Android、iOS 和 Windows 裝置的應用程式。  設計應用程式時，請使用 Visual Studio 中的工具，輕鬆地加入已連線的服務，例如 Office 365、Azure App Service 和 Application Insights。

 使用 C# 和 .NET Framework、HTML 和 JavaScript 或 C++ 建置您的應用程式。 共用程式碼、字串、影像，甚至在某些情況下，共用使用者介面。

 如果您要建置遊戲或沈浸式圖形化應用程式，請安裝 Visual Studio Tools for Unity，並享受搭配 Unity 提供的各種功能強大且具生產力的 Visual Studio 功能，這個熱門的跨平台遊戲/圖形引擎與開發環境適用於在 iOS、Android、Windows 及其他平台上執行的應用程式。

 **本文內容：**

-   [建置 Android、iOS 和 Windows 的應用程式 (.NET Framework)](#NET)

    -   [以 Android、iOS 和 Windows 為目標的單一程式碼基底](../cross-platform/cross-platform-mobile-development-in-visual-studio.md#AndroidHTML)

    -   [以 Windows 10 裝置為目標](../cross-platform/cross-platform-mobile-development-in-visual-studio.md#WindowsHTML)

-   [建置 Android、iOS 和 Windows 的應用程式 (HTML/JavaScript)](#HTML)

-   [建置 Android 和 Windows 的應用程式 (C++)](#CPP)

-   [使用 Visual Studio Tools for Unity 建置 Android、iOS 和 Windows 的跨平台遊戲](#Unity)

##  <a name="NET"></a> 建置 Android、iOS 和 Windows 的應用程式 (.NET Framework)
 ![裝置](../cross-platform/media/homedevices.png "HomeDevices")

 利用 Xamarin，您可以在同一個方案中將目標設為 Android、iOS 及 Windows，來共用程式碼，甚至共用 UI。

|**深入了解**|
|--------------------|
|[安裝 Visual Studio](http://www.visualstudio.com/products/visual-studio-community-vs) (VisualStudio.com)|
|[了解 Visual Studio 中的 Xamarin](http://www.visualstudio.com/explore/xamarin-vs) (VisualStudio.com)|
|[Visual Studio 和 Xamarin](../cross-platform/visual-studio-and-xamarin.md) (MSDN Library)|
|[應用程式生命週期管理 (ALM) 與 Xamarin 應用程式](../cross-platform/application-lifecycle-management-alm-with-xamarin-apps.md) (MSDN Library)|
|[了解 Visual Studio 中的通用 Windows 應用程式](https://www.visualstudio.com/vs/universal-windows-platform/) (VisualStudio.com)|
|[了解 Swift 與 C# 之間的相似性](http://aka.ms/scposter) (download.microsoft.com)|
|[了解 Visual Studio 的 Android 模擬器](http://www.visualstudio.com/explore/msft-android-emulator-vs) (VisualStudio.com)|

###  <a name="AndroidHTML"></a> 以 Android、iOS 和 Windows 為目標的單一程式碼基底
 您可以使用 C# 或 F# (目前不支援 Visual Basic)，來建置 Android、iOS 和 Windows 的原生應用程式。  若要開始，請安裝 Visual Studio 2015、選取安裝程式中的 [自訂] 選項，然後選取 [跨平台行動開發] > [C#/.NET (Xamarin)] 下方的方塊。 您也可以開始使用 [Xamarin 安裝程式 (英文)](https://www.xamarin.com/download)，需要此安裝程式，才能安裝適用於 Visual Studio 2013 的 Xamarin。

 如果您已經安裝 Visual Studio 2015，請從[控制台] > [程式和功能] 中執行安裝程式，然後針對 Xamarin 選取上述的同一個 [自訂] 選項。

 當您完成時，專案範本會出現在 [新增專案] 對話方塊中。 尋找 Xamarin 範本的最簡單方式是只需搜尋「Xamarin」。

 Xamarin 會以 .NET 物件形式公開 Android、iOS 和 Windows 的原生功能。 由於您的應用程式具備原生 API 和原生使用者控制項的完整存取權，而且，它們與以原生平台語言撰寫的應用程式一樣回應靈敏。

 建立專案之後，您將可以發揮 Visual Studio 的所有生產力功能。 例如，您將使用設計工具來建立頁面，並使用 IntelliSense 來瀏覽行動裝置平台的原生 API。 當您準備好要執行應用程式並查看其外觀時，可以使用 Visual Studio 的 Android 模擬器或 Android SDK 模擬器，或是在 Windows Phone 模擬器上執行 Windows 應用程式。 您也可以直接使用已連接到開發電腦的 Android 和 Windows 裝置。 針對 iOS 專案，請連線到網路上的 Mac，然後從 Visual Studio 啟動 Mac 模擬器，或者連線到已連接到開發電腦的裝置。

#### <a name="design-one-set-of-pages-that-render-across-all-devices-by-using-xamarinforms"></a>設計一組頁面，使用 Xamarin.Forms 在所有裝置上轉譯
 根據您應用程式設計的複雜度，您可能會考慮使用專案範本之 [行動應用程式] 群組中的 **Xamarin.Forms** 範本，來建置應用程式。 Xamarin.Forms 是可讓您建立單一使用者介面的 UI 工具組，您可以跨 Android、iOS 和 Windows 共用該介面。  當您編譯 Xamarin.Forms 方案時，將取得 Android 應用程式、iOS 應用程式和 Windows 應用程式。 如需詳細資訊，請參閱[了解如何使用 Xamarin 進行行動裝置應用程式開發](../cross-platform/learn-about-mobile-development-with-xamarin.md)。

####  <a name="ShareHTML"></a> 在 Android、iOS 和 Windows 應用程式之間共用程式碼
 如果您不使用 Xamarin.Forms，並選擇針對每個平台個別設計，您可以在平台專案 (Android、iOS 和 Windows) 之間共用大部分的非 UI 程式碼。 這包括任何商務邏輯、雲端整合、資料庫存取，或以 .NET Framework 為目標的其他任何程式碼。 唯一無法共用的程式碼是以特定平台為目標的程式碼。

 ![在 Windows、iOS 和 Android UI 之間共用程式碼](../cross-platform/media/sharecode.png "ShareCode")

 您可以使用共用專案和 (或) 可攜式類別庫專案來共用您的程式碼。 您可能會發現某些程式碼最適合用於共用專案，而某些程式碼在可攜式類別庫專案內較有意義。

|**進一步了解**|
|--------------------|
|選擇是否使用共用專案和 (或) 可攜式類別庫專案，來共用程式碼。<br /><br /> [跨平台共用程式碼](http://blogs.msdn.com/b/dotnet/archive/2014/04/21/sharing-code-across-platforms.aspx) (.NET Framework 部落格)<br /><br /> [共用程式碼選項 (英文)](http://developer.xamarin.com/guides/cross-platform/application_fundamentals/building_cross_platform_applications/sharing_code_options/) (Xamarin)<br /><br /> [使用 .NET Framework 時的程式碼共用選項](http://msdn.microsoft.com/library/dn720832.aspx) (MSDN Library)|

###  <a name="WindowsHTML"></a> 以 Windows 10 裝置為目標
 ![Windows 裝置](../cross-platform/media/windowsdevices.png "WindowsDevices")

 如果您想要建立以 Windows 10 裝置的完整範圍為目標的單一應用程式，請建立通用 Windows 應用程式。 您會使用單一專案來設計應用程式，您的網頁將正確轉譯，無論是使用哪一種裝置來檢視。

 請從通用 Windows 應用程式專案範本開始。 以視覺化的方式，設計您的網頁，然後在預覽視窗中開啟它們，以查看它們在各種裝置上的外觀。 如果您不喜歡網頁在裝置上的外觀，您可以最佳化成更適合螢幕大小、解析度或不同的方向，例如橫向或縱向模式。 您可以使用直覺式的工具視窗和 Visual Studio 中容易存取的功能表選項來完成這些操作。 當您準備好要執行應用程式並逐步執行程式碼時，會發現所有裝置模擬器和不同類型的裝置的模擬器一起放在 [標準]  工具列上的一個下拉式清單。

 Windows 10 相當新，因此您會找到以 Windows 8.1 為目標的專案範本。 如果您想要您的應用程式在 Windows 10 手機、平板電腦和電腦上執行，您可以使用這些專案範本。 不過，執行 Windows 8.1 的所有裝置都能自動升級至 Windows 10，因此除非您有特定原因而以 Windows 8.1 為目標，否則我們建議您使用以 Windows 10 為目標的專案範本。

|**進一步了解**|
|--------------------|
|[了解通用 Windows 應用程式](https://msdn.microsoft.com/library/windows/apps/dn894631.aspx) (Windows 開發人員中心)|
|[建置您的第一個應用程式](http://msdn.microsoft.com/library/windows/apps/dn609832.aspx) (Windows 開發人員中心)|
|[開發適用於通用 Windows 平台 (UWP) 的應用程式](../cross-platform/develop-apps-for-the-universal-windows-platform-uwp.md)|
|[將應用程式移轉至通用 Windows 平台 (UWP)](../misc/migrate-apps-to-the-universal-windows-platform-uwp.md)|

##  <a name="HTML"></a> 建置 Android、iOS 和 Windows 的應用程式 (HTML/JavaScript)
 ![裝置](../cross-platform/media/homedevices.png "HomeDevices")

 如果您是熟悉 HTML 和 JavaScript 的 Web 開發人員，則可使用 Visual Studio Tools for Apache Cordova，以 Windows、Android 和 iOS 為目標。 這些應用程式能以全部三個平台為目標，且您可以使用最熟悉的技巧和程序來建置它們。

 Apache Cordova 是一種包含外掛程式模型的架構。 此外掛程式模型提供單一 JavaScript API，讓您可用來存取這三個平台 (Android、iOS 和 Windows) 的原生裝置功能。

 因為這些 API 是跨平台的，您可以在所有三個平台之間共用您撰寫的大部分內容。 這會降低開發與維護的成本。 另外，也不需要從頭開始。 如果您已建立其他類型的 Web 應用程式，可以與 Cordova 應用程式共用那些檔案，而不需要以任何方式修改或重新設計。

 ![多重裝置混合式應用程式](../cross-platform/media/multidevicehybridapps.png "MultiDeviceHybridApps")

 若要開始，請安裝 Visual Studio 2015，然後在安裝期間選擇 **HTML/JavaScript (Apache Cordova)** 功能。 如果您使用的是 Visual Studio 2013，請安裝 Visual Studio Tools for Apache Cordova 擴充功能。 無論何種方式，Cordova 工具都會自動安裝建置多重平台應用程式所需的所有協力廠商軟體。

 安裝擴充功能之後，請開啟 Visual Studio 並建立**空白應用程式 (Apache Cordova)** 專案。 然後，您可以使用 JavaScript 或 TypeScript 來開發應用程式。 您也可以加入外掛程式以擴充應用程式的功能，而外掛程式中的 API 會在您撰寫程式碼時出現在 IntelliSense 中。

 當您準備好要執行應用程式並逐步執行程式碼時，請選擇模擬器 (例如 Apache Ripple 模擬器或 Visual Studio 模擬器 (Android 或 Windows Phone))、瀏覽器或已直接連接到電腦的裝置。 然後啟動您的應用程式。 如果您正在 Windows PC 上開發應用程式，您甚至可以在其上執行。 系統會將這些選項全都建置到 Visual Studio 中，以做為 Visual Studio Tools for Apache Cordova 的一部分。

 Visual Studio 仍然提供用於建立通用 Windows 應用程式的專案範本，因此，請只在想要以 Windows 裝置為目標時使用它們。 如果您之後決定以 Android 和 iOS 為目標，一律可將程式碼移植到 Cordova 專案。 WinJS API 具有開放原始碼版本，因此您可以重複使用任何利用這些 API 的程式碼。 話雖如此，如果未來想要以其他平台為目標，則建議您從 Visual Studio Tools for Apache Cordova 開始。

|**進一步了解**|
|--------------------|
|[安裝 Visual Studio](http://www.visualstudio.com/products/visual-studio-community-vs) (VisualStudio.com)|
|[開始使用 Visual Studio Tools for Apache Cordova](http://taco.visualstudio.com/en-us/docs/get-started-vs-tools-apache-cordova/) (taco.visualstudio.com)|
|[了解 Visual Studio Emulator for Android](http://www.visualstudio.com/explore/msft-android-emulator-vs) (VisualStudio.com)|

##  <a name="CPP"></a> 建置 Android 和 Windows 的應用程式 (C++)
 ![使用 C&#43;&#43; 為 Android、 iOS 和 Windows 建置](../cross-platform/media/cross-plat-cpp-intro-image.png "Cross_Plat_CPP_Intro_Image")

 首先，安裝 Visual Studio 2015 和適用於跨平台行動裝置應用程式開發的 Visual C++ 工具。 然後，您可以建置 Android 的 Native-Activity 應用程式，或以 Windows 為目標的應用程式。 目前尚未提供以 iOS 為目標的 C++ 範本。 您可以視需要在同一個方案以 Android 和 Windows 為目標，然後使用跨平台靜態或動態共用程式庫，在這兩者間共用程式碼。

 如果您必須建置需要任何進階圖形操作類型 (例如遊戲) 的 Android 應用程式，可使用 C++ 來執行此動作。 從**原生活動應用程式 (Android)** 專案開始。 這個專案提供對 Clang 工具鏈的完整支援。

 ![Native-Activity 專案範本](../cross-platform/media/cross-plat-cpp-native.png "Cross-Plat_CPP_Native")

 當您準備好要執行應用程式及查看其外觀時，請使用 Visual Studio 的 Android 模擬器。 這項工具不僅快速可靠，而且容易安裝及設定。

 您也可以使用 C++ 和通用 Windows 應用程式專案範本，建置以 Windows 10 裝置的完整範圍為目標的應用程式。 在本主題稍早的[以 Windows 10 裝置為目標](#WindowsHTML)一節中進一步了解。

 您可以藉由建立靜態或動態共用程式庫，在 Android 和 Windows 之間共用 C++ 程式碼。

 ![靜態和動態共用程式庫](../cross-platform/media/cross-plat-cpp-libraries.png "Cross_Plat_CPP_Libraries")

 您可以如本節稍早所述，在 Windows 或 Android 專案中使用該程式庫。 您也可以在使用 Xamarin、Java 或任何語言建置的應用程式中使用該程式庫，讓您叫用 Unmanaged DLL 中的函式。

 當您在這些程式庫中撰寫程式碼時，您可以使用 IntelliSense 來瀏覽 Android 和 Windows 平台的原生 API。 這些程式庫專案與 Visual Studio 偵錯工具完全整合，因此您可以使用偵錯工具的所有進階功能，來設定中斷點、逐步執行程式碼，以及尋找和修正問題。

|**進一步了解**|
|--------------------|
|[下載 Visual Studio。](http://www.visualstudio.com/products/visual-studio-community-vs) (VisualStudio.com)|
|[安裝跨平台行動裝置開發適用的 Visual C++ 工具。](https://msdn.microsoft.com/library/dn872463\(v=vs.140\).aspx) (MSDN Library)。|
|[進一步了解如何使用 C++ 來將多個平台作為目標。](https://www.visualstudio.com/vs/cplusplus-mdd/) (VisualStudio.com)|
|[安裝所需項目，然後建立 Android 原生活動應用程式](https://msdn.microsoft.com/library/dn872463\(v=vs.140\).aspx) (MSDN Library)|
|[了解 Visual Studio Emulator for Android](http://www.visualstudio.com/explore/msft-android-emulator-vs) (VisualStudio.com)|
|[深入了解如何與 Android 和 Windows 應用程式共用 C++ 程式碼](http://www.visualstudio.com/explore/cplusplus-mdd-vs.aspx) (VisualStudio.com)|
|[適用於 C++ 的跨平台行動開發範例](https://msdn.microsoft.com/library/dn707596.aspx) (MSDN Library)|
|[其他適用於 C++ 的跨平台行動開發範例](https://code.msdn.microsoft.com/site/search?f%5B0%5D.Type=SearchText&f%5B0%5D.Value=android&f%5B1%5D.Type=ProgrammingLanguage&f%5B1%5D.Value=C%2B%2B&f%5B1%5D.Text=C%2B%2B) (code.msdn)|

##  <a name="Unity"></a> 使用 Visual Studio Tools for Unity 建置 Android、iOS 和 Windows 的跨平台遊戲
 Visual Studio Tools for Unity 是將 Visual Studio 的強大程式碼編輯、生產力和偵錯工具與 Unity 整合的免費 Visual Studio 擴充功能，這個熱門的跨平台遊戲/圖形引擎和開發環境適用於以 Windows、iOS、Android 和其他平台為目標的沈浸式應用程式。

 ![VSTU 開發環境](../cross-platform/media/vstu-overview.png "VSTU_Overview")

 透過 Visual Studio Tools for Unity (VSTU)，您可以在 C# 中使用 Visual Studio 來撰寫遊戲和編輯器指令碼，然後使用其強大的偵錯工具來尋找及修正錯誤。 最新版的 VSTU 包含對 Unity 5 的支援，且包括 Unity 的 ShaderLab 著色器語言的語法著色、與 Unity 的更佳同步化、更豐富的偵錯，以及 MonoBehavior 精靈的改良式程式碼產生。 VSTU 也會將您的 Unity 專案檔案、主控台訊息和啟動遊戲的功能整合到 Visual Studio 中，以便您可以在撰寫程式碼時，花較少的時間來切換 Unity Editor。

 立即開始使用 Unity 和 Visual Studio Tools for Unity 來建置遊戲。

|**進一步了解**|
|--------------------|
|[進一步了解如何使用 Visual Studio 來建置 Unity 遊戲](https://www.visualstudio.com/en-us/features/unitytools-vs.aspx)|
|[進一步了解 Visual Studio Tools for Unity](../cross-platform/visual-studio-tools-for-unity.md) (MSDN Library)|
|[開始使用 Visual Studio Tools for Unity](../cross-platform/getting-started-with-visual-studio-tools-for-unity.md) (MSDN Library)|
|[了解 Visual Studio Tools for Unity 2.0 Preview 的最新增強功能](http://blogs.msdn.com/b/visualstudio/archive/2014/12/03/visual-studio-tools-for-unity-2-0-preview.aspx) (Visual Studio 部落格)|
|[觀賞 Visual Studio Tools for Unity 2.0 Preview 的介紹影片](http://www.bing.com/videos/search?q=visual+studio+tools+for+unity&qs=n&form=QBVLPG&pq=visual+studio+tools+for+unity&sc=6-29&sp=-1&sk=#view=detail&mid=0A13177F0BC7463A24080A13177F0BC7463A2408) (影片)|
|[了解 Unity](http://unity3d.com/) (Unity 網站)|

## <a name="see-also"></a>請參閱

- [將 Office 365 API 加入 Visual Studio 專案中](http://msdn.microsoft.com/library/office/dn605899\(v=office.15\).aspx)
- [Azure 行動服務](http://msdn.microsoft.com/library/dn720832\(v=vs.110\).aspx)
- [Application Insights](/azure/application-insights/app-insights-overview)