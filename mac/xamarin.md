---
title: Xamarin
description: '使用 Visual Studio for Mac 中的 Xamarin 可讓您建立以 iOS、Mac、Android、tvOS 和 watchOS 為目標的跨平台應用程式 '
author: therealjohn
ms.author: johmil
ms.date: 06/18/2019
ms.assetid: 339F6051-5F90-48DC-8237-EBBC8A03A32B
ms.topic: overview
ms.openlocfilehash: 41b26eb75454299aed86a3cdb3905d6c66efb098
ms.sourcegitcommit: 35fa920126b34c8d3839da53e3a4c2c6f509968f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2021
ms.locfileid: "102473344"
---
# <a name="xamarin-mobile-app-development"></a>Xamarin 行動裝置應用程式開發

[Xamarin](/xamarin) 的第一級支援可讓您開發 Android、macOS、iOS、tvOS 和 watchOS 的豐富原生體驗。 Xamarin.Forms 跨平台應用程式可協助您在 Android、iOS 與 macOS 之間共用 XAML UI 程式碼，而不限制原生功能的存取權。

## <a name="xamarinforms"></a>Xamarin.Forms

適用于 Xamarin 的 XAML 熱重載已內建于 Visual Studio for Mac 8.3 版和更新版本中。 啟用這項功能之後，每次儲存檔案時，變更都會立即反映在執行中的應用程式中。

若要啟用 XAML 熱重載，請勾選 Visual Studio 的 [ **啟用 Xamarin 熱重載** ] 核取方塊， **> 喜好設定 > 專案 > Xamarin 熱重載**。

如需有關熱重載的詳細資訊，請參閱檔中的「 [適用于 Xamarin 的 XAML 熱重載」. 表單指南](/xamarin/xamarin-forms/xaml/hot-reload) 。

## <a name="android"></a>Android

Visual Studio for Mac 有其專屬整合式 Android SDK 管理員，可讓您存取您希望您應用程式作為目標的 SDK。

對於 Android 應用程式，Visual Studio for Mac 包括自己的設計工具，可使用 Android 的 `.axml` 檔案，以視覺化方式建構使用者介面。 Visual Studio for Mac 會在自己的 Android Designer 中開啟這些檔案，如下圖所示：

![Android UI 設計工具](media/intro-image31.png)

如需 Android Designer 的詳細資訊，請參閱 [Xamarin.Android Designer Overview](/xamarin/android/user-interface/android-designer/index) (Xamarin.Android 設計工具概觀) 指南。

## <a name="ios"></a>iOS

iOS 設計工具已與 Visual Studio for Mac 完全整合在一起，以視覺化編輯 .xib 和分鏡腳本檔案來建立 iOS、tvOS 和 WatchOS UI 和轉換。 整個使用者介面都可以使用工具箱和設計介面之間的拖放功能建置，同時使用直覺式方法來處理事件。 iOS 設計工具也利用設計階段轉譯支援[自訂控制項](/xamarin/ios/user-interface/designer/ios-designable-controls-overview)。

![iOS 分鏡腳本設計工具](media/intro-image30.png)

如需使用 iOS 詳細資訊，請參閱 [Designer](/xamarin/ios/user-interface/designer/?tabs=macos) (設計工具) 指南。

### <a name="mac"></a>Mac

Xamarin 提供可讓您建立美觀 Mac 應用程式的原生 Mac API 繫結。

如需使用 Visual Studio for Mac 撰寫 Mac 應用程式的詳細資訊，請參閱 [Xamarin.Mac](/xamarin/mac/get-started/index) 指南。

## <a name="xamarin-enterprise-features"></a>Xamarin 企業功能

> [!Note]
> 這些產品只能搭配 Visual Studio Enterprise 訂閱使用。

### <a name="profiler"></a>分析工具

Xamarin Profiler 有三種工具可供分析所用。 [Xamarin Profiler 簡介](/xamarin/tools/profiler/index?tabs=macos)指南探討這些工具測量的內容，以及它們如何分析您的應用程式，並釐清每個畫面上顯示的資料意義。

### <a name="inspector"></a>Inspector

Xamarin Inspector 提供互動式的 C# 主控台與使用者工具。 它可以當作檢查即時應用程式時的偵錯或診斷輔助工具、教學工具、記錄工具或試驗工具。

![Xamarin Inspector](media/intro-inspector.png)

其包含的獨立應用程式，提供以各種程式設計平台 (Android、iOS、Mac 和 Windows) 為目標的多功能 C# 主控台，並整合到您的 IDE 偵錯工作流程中。

如需詳細資訊，請參閱 [Xamarin Inspector](/xamarin/tools/inspector/release-notes/1.5) 指南。
