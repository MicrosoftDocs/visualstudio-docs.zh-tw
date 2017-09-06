---
title: "Visual Studio for Mac 簡介"
description: 
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.assetid: 3A130EC1-DD8C-4125-9034-B08D7AF7EA65
ms.translationtype: HT
ms.sourcegitcommit: f6c7e290f0abc2c32456e076420a7695ae868ba6
ms.openlocfilehash: ffbd08a4a6765c2cc38329325e91f4aed12d88d5
ms.contentlocale: zh-tw
ms.lasthandoff: 09/04/2017

---

# <a name="introducing-visual-studio-for-mac"></a>Visual Studio for Mac 簡介

Visual Studio for Mac 是現代化的尖端 IDE，具備建立行動裝置、桌面和 Web 應用程式的許多功能。 它支援下列開發：

* 使用 .NET 的行動裝置：Android、iOS、tvOS、watchOS
* Mac 桌面應用程式
* .NET Core 應用程式
* ASP.NET Core Web 應用程式
* 跨平台 Unity 遊戲

它擁有許多功能，包含多功能編輯器、偵錯、整合 iOS、Mac 及 Android 的原生平台，以及整合式原始檔控制等等，只是其眾多功能的一小部分。

本主題審視 Visual Studio for Mac 的各個部分，提供一些功能的相關資訊，讓它成為建立跨平台應用程式的強大工具。

## <a name="installation"></a>安裝

請遵循[安裝](~/installation.md)指南下載並安裝 Visual Studio for Mac。

## <a name="language-support"></a>語言支援

根據預設，Visual Studio for Mac 支援以 C# 和 F# 進行開發。

### <a name="c"></a>C#

C# 是在 Visual Studio for Mac 中建立跨平台應用程式最常用的語言。 這包括對所有 C# 7 功能的完整支援。

### <a name="f"></a>F#

F# 是專為在 .NET 上執行所設計的強型別功能性程式設計語言。 它可供 Visual Studio for Mac 使用者在 Android、Mac 和 iOS 上作為程式設計語言之用。 如需使用 F# 的詳細資訊，以及檢視以該語言建立的範例，請瀏覽 [F#](https://developer.xamarin.com/guides/cross-platform/fsharp/) 指南。

## <a name="platform-support"></a>平台支援

## <a name="net-core"></a>.NET 核心

[.NET Core](https://www.microsoft.com/net/core#macos) 是一種平台，用於建立在 Windows、Linux 和 Mac 上執行的應用程式。 Visual Studio for Mac 支援載入、建立、執行和偵錯 .NET Core 專案。

若要執行 .NET Core 專案，應該下載和安裝 .NET Core SDK。

.NET Core 支援包括：

* C# 和 F# IntelliSense。
* 適用於主控台、程式庫和 Web 應用程式的 .NET Core 專案範本。
* 完整偵錯支援，包括中斷點、呼叫堆疊、監看式視窗等等。
* NuGet PackageReferences 和 MSBuild 還原。
* 整合式單元測試支援，可使用 .NET Core SDK 隨附的 Visual Studio 測試平台來執行和偵錯測試。
* 從舊的 project.json 格式進行移轉。

若要開始，請參閱 ASP.NET Core Web 應用程式[實際操作實驗室](https://github.com/Microsoft/vs4mac-labs/tree/master/Web/Getting-Started)。

## <a name="xamarin"></a>Xamarin

[Xamarin](https://developer.xamarin.com/) 的第一級支援可讓您開發 Android、macOS、iOS、tvOS 和 watchOS 的豐富原生體驗。 Xamarin.Forms 跨平台應用程式可協助您在 Android、iOS 與 macOS 之間共用 XAML UI 程式碼，而不限制原生功能的存取權。

若要開始，請參閱行動裝置應用程式[實際操作實驗室](https://github.com/Microsoft/vs4mac-labs/tree/master/Mobile/Getting-Started)。

### <a name="android"></a>Android

Visual Studio 有自己的整合式 Android SDK Manager。

對於 Android 應用程式，Visual Studio for Mac 包括自己的設計工具，可使用 Android 的 `.axml` 檔案，以視覺化方式建構使用者介面。 Visual Studio for Mac 會在自己的 Android 設計工具中開啟這些檔案，如下所示：

![](media/intro-image31.png)

如需 Android 設計工具的詳細資訊，請參閱[設計工具概觀](https://developer.xamarin.com/Android/Guides/User_Interface/Designer_Overview)文件。

### <a name="ios"></a>iOS

iOS 設計工具已與 Visual Studio for Mac 完全整合在一起，以視覺化編輯 .xib 和分鏡腳本檔案來建立 iOS、tvOS 和 WatchOS UI 和轉換。 整個使用者介面都可以使用工具箱和設計介面之間的拖放功能建置，同時使用直覺式方法來處理事件。 iOS 設計工具也利用設計階段轉譯支援[自訂控制項](https://developer.xamarin.com/guides/ios/user_interface/designer/ios_designable_controls_overview/)。

![](media/intro-image30.png)

如需使用 iOS 設計工具的詳細資訊，請參閱[設計工具](https://developer.xamarin.com/guides/ios/user_interface/designer)文件。

### <a name="mac"></a>Mac

Xamarin 提供可讓您建立美觀 Mac 應用程式的原生 Mac API 繫結。

如需使用 Visual Studio for Mac 撰寫 Mac 應用程式的詳細資訊，請參閱 [Xamarin.Mac](https://developer.xamarin.com/guides/#mac) 文件。

## <a name="gaming"></a>遊戲

Visual Studio for Mac 支援 Unity 5.6.1 的跨平台遊戲開發。

若要開始，請參閱 Unity [實際操作實驗室](https://github.com/Microsoft/vs4mac-labs/tree/master/Unity/Getting-Started)。

## <a name="enterprise-features"></a>企業功能

> [!Note]
> 這些產品只能搭配 Visual Studio Enterprise 訂閱使用。

### <a name="profiler"></a>程式碼剖析工具

Xamarin Profiler 有三種工具可供分析所用。 [Xamarin Profiler 簡介](https://developer.xamarin.com/guides/cross-platform/deployment,_testing,_and_metrics/xamarin-profiler/)指南探討這些工具測量的內容，以及它們如何分析您的應用程式，並釐清每個畫面上顯示的資料意義。

### <a name="inspector"></a>檢查程式

Xamarin Inspector 為使用者提供互動式的 C# 主控台和工具。 檢查即時應用程式時，它可作為教學工具、記錄工具或試驗工具，用為偵錯或診斷輔助工具。

![](media/intro-inspector.png)

它包含的獨立應用程式，提供以各種程式設計平台 (Android、iOS、Mac 和 Windows) 為目標的多功能 C# 主控台，以及整合到 IDE 的偵錯工作流程中。

如需詳細資訊，請參閱 [Xamarin Inspector](https://developer.xamarin.com/guides/cross-platform/inspector/) 指南。

## <a name="next-steps"></a>後續步驟

* **了解全貌** - 若要概要了解 Visual Studio for Mac 中的主要功能，請參閱 Visual Studio for Mac [IDE 導覽](~/ide-tour.md)。
* **安裝** - 若要了解如何下載並安裝 Visual Studio，請參閱[安裝](~/installation.md)指南。
* **Xamarin 教學課程** - 若要深入了解如何使用 Xamarin 開發程式碼，請移至 Xamarin [開發人員中心](https://developer.xamarin.com)。
* **影片** - 若要深入了解 Visual Studio for Mac 的其他功能和各種層面，請觀看 [Xamarin University](https://university.xamarin.com) (Xamarin 大學) 網站的影片。
* **實際操作實驗室** - 若要開始使用 Visual Studio for Mac 包含的各種工作負載，請參閱[實際操作實驗室](https://github.com/Microsoft/vs4mac-labs)。
