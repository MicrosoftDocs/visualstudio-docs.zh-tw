---
title: Visual Studio 中的跨平台行動裝置應用程式開發 | Microsoft Docs
description: 在本文中，您將瞭解如何使用 Visual Studio 來建立適用于 Android、iOS 和 Windows 裝置的應用程式。
titleSuffix: ''
ms.custom: SEO-VS-2020
ms.date: 10/17/2019
ms.technology: vs-ide-mobile
ms.topic: conceptual
ms.assetid: 8202717a-e990-45cf-b092-438651ccb38a
author: conceptdev
ms.author: crdun
manager: crdun
ms.workload:
- multiple
ms.openlocfilehash: 2f3c611ae157be4f2ea89254856bdd3b6fba448d
ms.sourcegitcommit: 63cb90e8cea112aa2ce8741101b309dbc709e393
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2021
ms.locfileid: "110687683"
---
# <a name="cross-platform-mobile-development-in-visual-studio"></a>Visual Studio 中的跨平台行動裝置應用程式開發

您可以使用 Visual Studio 建置 Android、iOS 和 Windows 裝置的應用程式。  當您設計應用程式時，請使用 Visual Studio 中的工具，輕鬆地加入已連線的服務，例如 Microsoft 365、Azure App Service 和 Application Insights。

使用 C# 和 .NET Framework、HTML 和 JavaScript 或 C++ 建置您的應用程式。 共用程式碼、字串、影像，甚至在某些情況下，共用使用者介面。

如果您要建置遊戲或沈浸式圖形化應用程式，請安裝 Visual Studio Tools for Unity，並享受搭配 Unity 提供的各種功能強大且具生產力的 Visual Studio 功能，這個熱門的跨平台遊戲/圖形引擎與開發環境適用於在 iOS、Android、Windows 及其他平台上執行的應用程式。

## <a name="build-an-app-for-android-ios-and-windows-net-framework"></a>建置 Android、iOS 和 Windows 的應用程式 (.NET Framework)

![裝置](../cross-platform/media/homedevices.png "HomeDevices")

使用 Visual Studio Tools for Xamarin，您可以在同一個解決方案中將目標設為 Android、iOS 及 Windows，來共用程式碼，甚至共用 UI。

|**深入了解**|
|--------------------|
|[安裝 Visual Studio](https://visualstudio.microsoft.com/vs/community/) (VisualStudio.com)|
|[了解 Visual Studio 中的 Xamarin](https://visualstudio.microsoft.com/xamarin/) (VisualStudio.com)|
|[Xamarin 行動應用程式開發文件](/xamarin/) |
|[使用 Xamarin 應用程式進行 DevOps](/xamarin/tools/ci/devops/) |
|[瞭解 Visual Studio (VisualStudio.com 中的通用 Windows 應用程式](https://visualstudio.microsoft.com/vs/universal-windows-platform/)) |
|[了解 Swift 與 C# 之間的相似性](https://aka.ms/scposter) (download.microsoft.com)|

### <a name="target-android-ios-and-windows-from-a-single-code-base"></a><a name="AndroidHTML"></a> 以 Android、iOS 和 Windows 為目標的單一程式碼基底

 您可以使用 c # 或 F # 來建立 Android、iOS 和 Windows 的原生應用程式，這一次) 不支援 Visual Basic (。  若要開始使用，請安裝 Visual Studio，請在安裝程式中選取 [ **使用 .net 進行** 行動裝置開發] 選項。

 如果您已經安裝 Visual Studio，請重新執行 **Visual Studio 安裝程式** ，然後針對 Xamarin (選取相同的 [ **使用 .Net 進行行動開發** ] 選項) 。

 當您完成時，專案範本會出現在 [新增專案] 對話方塊中。 尋找 Xamarin 範本的最簡單方式是只需搜尋「Xamarin」。

 Xamarin 會以 .NET 類別和方法形式公開 Android、iOS 和 Windows 的原生功能。 這表示您的應用程式具備原生 API 和原生控制項的完整存取權；而且，它們與以原生平台語言撰寫的應用程式一樣回應靈敏。

 建立專案之後，您將可以利用 Visual Studio 的所有生產力功能。 例如，您將使用設計工具來建立頁面，並使用 IntelliSense 來瀏覽行動裝置平台的原生 API。 當您準備好要執行應用程式及查看其外觀時，您可以使用 Android SDK 模擬器，並以原生方式執行 Windows 應用程式。 您也可以直接使用已連接到開發電腦的 Android 和 Windows 裝置。 針對 iOS 專案，請連線到網路上的 Mac，然後從 Visual Studio 啟動 iOS 模擬器，或者連線到已連接到開發電腦的裝置。

#### <a name="design-one-set-of-pages-that-render-across-all-devices-by-using-xamarinforms"></a>設計一組頁面，使用 Xamarin.Forms 在所有裝置上轉譯

 根據您應用程式設計的複雜度，您可能會考慮使用專案範本之 [行動應用程式] 群組中的 **Xamarin.Forms** 範本，來建置應用程式。 Xamarin.Forms 是可讓您建立單一使用者介面的 UI 工具組，您可以跨 Android、iOS 和 Windows 共用該介面。  當您編譯 Xamarin.Forms 方案時，將取得 Android 應用程式、iOS 應用程式和 Windows 應用程式。 如需詳細資訊，請參閱[了解如何使用 Xamarin 進行行動裝置應用程式開發](/xamarin/cross-platform/get-started/introduction-to-mobile-development/)和 [Xamarin.Forms 文件](/xamarin/xamarin-forms/)。

#### <a name="share-code-between-android-ios-and-windows-apps"></a><a name="ShareHTML"></a> 在 Android、iOS 和 Windows 應用程式之間共用程式碼

 如果您不使用 Xamarin.Forms，並選擇針對每個平台個別設計，您可以在平台專案 (Android、iOS 和 Windows) 之間共用大部分的非 UI 程式碼。 這包括任何商務邏輯、雲端整合、資料庫存取，或以 .NET Framework 為目標的其他任何程式碼。 唯一無法共用的程式碼是以特定平台為目標的程式碼。

 ![在 Windows、iOS 和 Android Ui 之間共用程式碼](../cross-platform/media/sharecode.png "ShareCode")

 您可以使用共用專案和 (或) 可攜式類別庫專案來共用您的程式碼。 您可能會發現某些程式碼最適合用於共用專案，而某些程式碼在可攜式類別庫專案內較有意義。

|**深入了解**|
|--------------------|
|[共用程式碼選項 (英文)](/xamarin/cross-platform/app-fundamentals/code-sharing/) (Xamarin) |
|[.NET 的程式碼共用選項](/dotnet/standard/cross-platform/) |

### <a name="target-windows-10-devices"></a><a name="WindowsHTML"></a> 目標 Windows 10 裝置

 ![Windows 裝置](../cross-platform/media/windowsdevices.png "Windows 裝置")

 如果您想要建立以 Windows 10 裝置的完整範圍為目標的單一應用程式，請建立通用 Windows 應用程式。 您會使用單一專案來設計應用程式，您的網頁將正確轉譯，無論是使用哪一種裝置來檢視。

 請從通用 Windows 平台 (UWP) 應用程式專案範本開始。 以視覺化的方式，設計您的網頁，然後在預覽視窗中開啟它們，以查看它們在各種裝置上的外觀。 如果您不喜歡網頁在裝置上的外觀，您可以最佳化成更適合螢幕大小、解析度或不同的方向，例如橫向或縱向模式。 您可以使用直覺式的工具視窗和 Visual Studio 中容易存取的功能表選項來完成這些操作。 當您準備好要執行應用程式並逐步執行程式碼時，會發現所有裝置模擬器和不同類型的裝置的模擬器一起位在 [標準] 工具列上的一個下拉式清單。

|**深入了解**|
|--------------------|
|[通用 Windows 平台簡介](/windows/uwp/get-started/universal-application-platform-guide)|
|[建立您的第一個應用程式](/windows/uwp/get-started/your-first-app)|
|[開發適用於通用 Windows 平台 (UWP) 的應用程式](../cross-platform/develop-apps-for-the-universal-windows-platform-uwp.md)|

::: moniker range="vs-2017"

## <a name="build-an-app-for-android-ios-and-windows-htmljavascript"></a><a name="HTML"></a> 建立適用于 Android、iOS 和 Windows 的應用程式 (HTML/JavaScript) 

 ![Windows、iOS 和 Android 裝置](../cross-platform/media/homedevices.png "Windows、iOS 和 Android 裝置")

 如果您是熟悉 HTML 和 JavaScript 的 Web 開發人員，則可使用 Visual Studio Tools for Apache Cordova，以 Windows、Android 和 iOS 為目標。 這些應用程式可以全部三個平台為目標，且您可以使用最熟悉的技巧和程序來建置它們。

 Apache Cordova 是一種包含外掛程式模型的架構。 此外掛程式模型提供單一 JavaScript API，讓您可用來存取這三個平台 (Android、iOS 和 Windows) 的原生裝置功能。

 因為這些 API 是跨平台的，您可以在所有三個平台之間共用您撰寫的大部分內容。 這會降低開發與維護的成本。 另外，也不需要從頭開始。 如果您已建立其他類型的 Web 應用程式，可以與 Cordova 應用程式共用那些檔案，而不需要以任何方式修改或重新設計。

 ![使用 JavaScript 的多重裝置混合式應用程式](../cross-platform/media/multidevicehybridapps.png "使用 JavaScript 的多重裝置混合式應用程式")

 首先，安裝 Visual Studio，然後在設定期間選擇 [使用 JavaScript 進行行動開發] 功能。 Cordova 工具會自動安裝建置多重平台應用程式所需的所有協力廠商軟體。

 安裝延伸模組之後，請開啟 Visual Studio 並建立 **空白應用程式 (Apache Cordova)** 專案。 然後，您可以使用 JavaScript 或 TypeScript 來開發應用程式。 您也可以加入外掛程式以擴充應用程式的功能，而外掛程式中的 API 會在您撰寫程式碼時出現在 IntelliSense 中。

 當您準備好要執行應用程式並逐步執行程式碼時，請選擇模擬器，例如 Apache Ripple 模擬器或 Android 模擬器、瀏覽器或您已直接連接到電腦的裝置。 然後啟動您的應用程式。 如果您正在 Windows PC 上開發應用程式，您甚至可以在其上執行。 系統會將這些選項全都建置到 Visual Studio 中，以做為 Visual Studio Tools for Apache Cordova 的一部分。

 Visual Studio 仍然提供用於建立通用 Windows 平台 (UWP) 應用程式的專案範本；因此，請只在想要以 Windows 裝置為目標時使用它們。 如果您之後決定以 Android 和 iOS 為目標，一律可將程式碼移植到 Cordova 專案。

|**深入了解**|
|--------------------|
|[安裝 Visual Studio](https://visualstudio.microsoft.com/vs/community/) (VisualStudio.com)|
|[開始使用 Visual Studio Tools for Apache Cordova](/previous-versions/visualstudio/cross-platform/tools-for-cordova/)|
|[了解 Visual Studio Emulator for Android](https://visualstudio.microsoft.com/vs/msft-android-emulator/) (VisualStudio.com)|

::: moniker-end

<a name="CPP"></a>

## <a name="build-an-app-for-android-ios-and-windows-c"></a>建立適用于 Android、iOS 和 Windows (c + + 的應用程式) 

![使用 C&#43;&#43; 建立 Android、iOS 和 Windows 版](../cross-platform/media/cross_plat_cpp_intro_image.png "Cross_Plat_CPP_Intro_Image")

 首先，安裝 Visual Studio 和 **使用 c + +** 的行動裝置開發工作負載。 然後，您可以建立適用于 Android 的原生活動應用程式，或以 Windows 或 iOS 為目標的應用程式。 如果您想要的話，您可以在相同的方案中以 Android、iOS 和 Windows 為目標，然後使用跨平臺靜態或動態共用程式庫在兩者之間共用程式碼。

 如果您必須建置需要任何進階圖形操作類型 (例如遊戲) 的 Android 應用程式，可使用 C++ 來執行此動作。 從 **(Android) 專案的原生活動應用程式** 開始。 這個專案提供對 Clang 工具鏈的完整支援。

 ![Native Activity 專案範本](../cross-platform/media/cross-plat_cpp_native.png "Native Activity 專案範本")

 當您準備好要執行應用程式及查看其外觀時，請使用適用於 Android 模擬器。 這項工具不僅快速可靠，而且容易安裝及設定。

 您也可以使用 C++ 和通用 Windows 平台 (UWP) 應用程式專案範本，建置以 Windows 10 裝置的完整範圍為目標的應用程式。 在本主題稍早的[以 Windows 10 裝置為目標](#WindowsHTML)一節中進一步了解。

 您可以藉由建立靜態或動態共用程式庫，在 Android、iOS 和 Windows 之間共用 c + + 程式碼。

 ![靜態和動態共用程式庫](../cross-platform/media/cross_plat_cpp_libraries.png "靜態和動態共用程式庫")

 您可以在 Windows、iOS 或 Android 專案中使用該程式庫，如本節稍早所述。 您也可以在使用 Xamarin、Java 或任何語言建置的應用程式中使用該程式庫，讓您叫用 Unmanaged DLL 中的函式。

 當您在這些程式庫中撰寫程式碼時，您可以使用 IntelliSense 來瀏覽 Android 和 Windows 平台的原生 API。 這些程式庫專案與 Visual Studio 偵錯工具完全整合，因此您可以使用偵錯工具的所有進階功能，來設定中斷點、逐步執行程式碼，以及尋找和修正問題。

|**深入了解**|
|--------------------|
|[下載 Visual Studio](https://visualstudio.microsoft.com/downloads/) (VisualStudio.com) |
|[安裝 C++ 的跨平台行動裝置應用程式開發](/cpp/cross-platform/install-visual-cpp-for-cross-platform-mobile-development)|
|[深入瞭解如何使用 c + + 以多個平臺為目標](https://visualstudio.microsoft.com/vs/cplusplus-mdd/) (VisualStudio.com) |
|[安裝您需要的內容，然後建立適用于 Android 的 c + + 原生活動應用程式](/cpp/cross-platform/create-an-android-native-activity-app)|
|[深入了解如何與 Android 和 Windows 應用程式共用 C++ 程式碼](https://visualstudio.microsoft.com/vs/cplusplus-mdd/) (VisualStudio.com)|
|[C + + 的跨平臺行動開發範例](/cpp/cross-platform/cross-platform-mobile-development-examples)|

<a name="Unity"></a>

## <a name="build-a-cross-platform-game-for-android-ios-and-windows-by-using-visual-studio-tools-for-unity"></a>使用 Visual Studio Tools for Unity 建置 Android、iOS 和 Windows 的跨平台遊戲

 Visual Studio Tools for Unity 是將 Visual Studio 的強大程式碼編輯、生產力和偵錯工具與 *Unity* 整合的免費 Visual Studio 延伸模組，這個熱門的跨平台遊戲/圖形引擎和開發環境適用於以 Windows、iOS、Android 和其他平台為目標的沉浸式應用程式。

 ![VSTU 開發環境](../cross-platform/media/vstu_overview.png "Visual Studio Tools for Unity 總覽")

 透過 Visual Studio Tools for Unity (VSTU)，您可以在 C# 中使用 Visual Studio 來撰寫遊戲和編輯器指令碼，然後使用其強大的偵錯工具來尋找及修正錯誤。 最新版的 VSTU 包含對 Unity 2018.1 的支援，且包括 Unity 的 ShaderLab 著色器語言的語法著色、與 Unity 的更佳同步化、更豐富的偵錯，以及 MonoBehavior 精靈的改善式程式碼產生。 VSTU 也會將您的 Unity 專案檔案、主控台訊息和啟動遊戲的功能整合到 Visual Studio 中，以便您可以在撰寫程式碼時，花較少的時間來切換 Unity Editor。

|**深入了解**|
|--------------------|
|[進一步了解如何使用 Visual Studio 來建置 Unity 遊戲](https://visualstudio.microsoft.com/vs/features/game-development/#tab-4b0d0be8de5f65564ad)|
|[深入了解 Visual Studio Tools for Unity](/gamedev/unity/get-started/visual-studio-tools-for-unity.md) |
|[開始使用 Visual Studio Tools for Unity](/gamedev/unity/get-started/getting-started-with-visual-studio-tools-for-unity.md) |
|[了解 Visual Studio Tools for Unity 2.0 Preview 的最新增強功能](https://devblogs.microsoft.com/visualstudio/visual-studio-tools-for-unity-2-0-preview/) (Visual Studio 部落格)|
|[觀賞 Visual Studio Tools for Unity 2.0 Preview 的介紹影片](https://www.bing.com/videos/search?q=visual+studio+tools+for+unity&qs=n&form=QBVLPG&pq=visual+studio+tools+for+unity&sc=6-29&sp=-1&sk=#view=detail&mid=0A13177F0BC7463A24080A13177F0BC7463A2408&preserve-view=true) (影片)|
|[了解 Unity](https://unity.com/) (Unity 網站)|

## <a name="see-also"></a>另請參閱

- [將 Microsoft 365 Api 新增至 Visual Studio 專案](/office/developer-program/office-365-developer-program)
- [Azure App Service - Mobile Apps](https://azure.microsoft.com/services/app-service/mobile/)
- [Visual Studio App Center](/appcenter)
