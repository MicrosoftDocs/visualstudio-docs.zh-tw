---
title: 透過 Xamarin Studio 之 Visual Studio for Mac 的優點
description: 本文說明 Visual Studio for Mac 所提供超越 Xamarin Studio 的功能和優點
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.assetid: 6ACF5FD4-D5C1-4050-95E3-467C753F25F1
ms.openlocfilehash: 63f8e0f03797f08383ad3a1ec2b9303a405ed236
ms.sourcegitcommit: 33c954fbc8e05f7ba54bfa2c0d1bc1f9bbc68876
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
ms.locfileid: "33870642"
---
# <a name="benefits-of-visual-studio-for-mac-over-xamarin-studio"></a>透過 Xamarin Studio 之 Visual Studio for Mac 的優點 
 
Visual Studio for Mac 已取代 Xamarin Studio 成為 Mac 上的全功能 IDE。 它提供的功能可讓您用來開發 Web 應用程式和服務、跨平台行動及桌面應用程式和遊戲。 此外，它可讓與 Azure 的整合變得十分簡單，不論其是指發行到 Azure 還是建立 Azure 函式。 它具有您想要從現代 IDE 獲得的所有項目，包括功能完整的原始檔編輯器、功能強大的偵錯工具、可自訂的工作區、Git 整合，以及豐富的擴充系統，全都是針對 Mac 設計。

其他功能包括：

* 以 Roslyn 為基礎的 C# IntelliSense、重構、分析器和程式碼修正
* 以 NuGet 為基礎的套件管理
* Visual Studio 相容的專案格式
* MSBuild 組建引擎
* 整合式單元測試
* 預設支援 F#

## <a name="language-support"></a>語言支援

只有在 Visual Studio for Mac 上才提供於 Mac 中撰寫 C# 7 程式碼的功能。

## <a name="net-core"></a>.NET Core

[.NET Core](https://www.microsoft.com/net/core#macos) 是一種平台，用於建立在 Windows、Linux 和 Mac 上執行的應用程式。 Visual Studio for Mac 支援載入、建立、執行和偵錯 .NET Core 專案。

.NET Core 會隨 Visual Studio for Mac 一起安裝，而且立即可用。

.NET Core 支援包括：

* C# 和 F# IntelliSense。
* 適用於主控台、程式庫和 Web 應用程式的 .NET Core 專案範本。
* 完整偵錯支援，包括中斷點、呼叫堆疊、監看式視窗等等。 
* NuGet 套件參考和以 MSBuild 為基礎的還原。 
* 整合式單元測試支援，可使用 .NET Core SDK 隨附的 Visual Studio 測試平台來執行和偵錯測試。 
* 從舊的 project.json 格式進行移轉。 
* .NET 標準專案支援。

## <a name="web-development"></a>Web 程式開發  

### <a name="aspnet-core"></a>ASP.NET Core 

Visual Studio for Mac 包含現成的 MVC 和 Web API 專案的 ASP.NET Core 範本。
 
![HTML Intellisense](media/benefits-vsmac-over-xs-image3.png)

Visual Studio for Mac 也新增了 HTML、CSS 和 JSON 檔案的新 Web 工具支援。 

### <a name="html"></a>HTML 

* HTML 新 範本。 
* 改良的智慧縮排和格式化。 
* 改良的顏色標示。 
* 改良的 IntelliSense。 
* 程式碼摺疊功能 (必須予以啟用)。 
* 解除美化命令。 
* 改良的程式碼範本 (程式碼片段)。 
* 使用 `<div>` 括住選取範圍。 
* 上/下選項會上/下移動選取的文字。 

### <a name="css"></a>CSS 

* 改良的智慧縮排和格式化。 
* 改良的顏色標示。 
* 改良的 IntelliSense。 
* 程式碼摺疊功能。 
* 多個程式碼範本 (程式碼片段)。 
* 上/下選項會上/下移動選取的文字。 

### <a name="json"></a>JSON 
* 具有 schemastore.org 存取權的結構描述選擇器。 
* 透過結構描述的驗證。 
* 透過結構描述的 IntelliSense。 
* 改良的智慧縮排和格式化。 
* 改良的顏色標示。 
* 註解/取消註解。 
* 引號插入和括號對稱。 
* 上/下選項會上/下移動選取的文字。 

## <a name="publishing-to-azure"></a>發行至 Azure

使用 Visual Studio for Mac 便可將您的 ASP.NET Core Web 應用程式和服務發行至 Azure 應用程式服務。 

![發佈至 Azure](media/benefits-vsmac-over-xs-image1.png)

### <a name="azure-functions"></a>Azure Functions

Azure 函式是用來在雲端中輕鬆執行少量程式碼片段或函式的解決方案。 Visual Studio for Mac 可讓您撰寫 Azure 函式，並在本機上對 Azure 函式進行偵錯。 若要開始使用，請在 [新增專案] 對話方塊的 [雲端] 下尋找 Azure 函式。 

### <a name="docker-support"></a>Docker 支援

您現在可以將 ASP.NET Core 應用程式發行至 Docker 容器，並從 Azure 應用程式服務執行。 

若要在專案中啟用 Docker 支援，請以滑鼠右鍵按一下 ASP.NET Core Web 應用程式，然後選取 [新增] > [Add Docker Support] (新增 Docker 支援)。 

若要將 Web 應用程式發行至 Docker 容器，請使用 Visual Studio for Mac 中引進的 [發行] > [發行到 Azure] 工作流程。

## <a name="source-editor-improvements"></a>原始檔編輯器改善 

除了以 Roslyn 為基礎的 C# IntelliSense、重構、分析器和程式碼修正外，Visual Studio for Mac 原始檔編輯器還透過 Xamarin Studio 提供下列改善： 

### <a name="language-bundles"></a>語言套件組合 

Visual Studio for Mac 支援 TextMate (`.tmBundle`) 和 sublime 3 (`.sublime`) 語言套件組合，可用來新增： 

* 編輯器色彩佈景主題 
* 程式碼片段 
* 新語言、啟用醒目提示和基本 IntelliSense 的文法 

您可以在 [喜好設定] > [文字編輯器] > [語言套件組合] 中新增這些套件組合。 

### <a name="color-theme-support"></a>色彩佈景主題支援 

Visual Studio for Mac 中支援下列色彩佈景主題格式： 

* Visual Studio (`.vssettings`) 
* Xamarin studio (`.json`) 
* TextMate (`tmTheme`) 

## <a name="unity"></a>Unity 

[Unity](https://unity3d.com/) 是可用來為所有主要平台建立高品質跨平台 2D 和 3D 遊戲的遊戲建立工具：行動、桌面、主控台、AR 及 VR 裝置，甚至是網路。 

從 Unity 5.6.1 開始，您可以使用 Visual Studio for Mac 來撰寫和偵錯 Unity 遊戲。 若要開始使用，請將 Visual Studio 設定為 Unity 5.6.1 指令碼編輯器。 

Unity 的工具包括： 

* 支援以 C# 撰寫的指令碼。 
* Unity 解決方案板。 
* Unity 編輯器的單鍵偵錯。 
* Unity 訊息的 IntelliSense。 
* Unity 訊息的程式碼色彩。 
* 存取 Unity 文件。 

## <a name="xamarin"></a>Xamarin 

雖然 Xamarin 的跨平台功能已經是 Xamarin Studio 的頭等功能，但是有一些 Xamarin 功能只能在 Visual Studio for Mac 中使用 

### <a name="android"></a>Android 

* [Android SDK manager](https://developer.xamarin.com/guides/android/application_fundamentals/using-the-sdk-manager/)  
* 只有 Visual Studio for Mac (而不是 Xamarin Studio) 才支援 Android O 

### <a name="ios-and-mac"></a>iOS 和 Mac 

* [iOS 簽署工作流程更新](https://developer.xamarin.com/guides/cross-platform/macios/apple-account-management/) 
    * 建立簽署身分識別，然後將它們安裝至本機金鑰鏈。 
    * 建立佈建設定檔。 
    * 將簽署身分識別新增至現有設定檔。
    *  佈建裝置：在 Apple Developer 入口網站中註冊裝置，並將它們新增至佈建設定檔。
* 只有 Visual Studio for Mac (而不是 Xamarin Studio) 才支援 iOS 11、watchOS 4 和 tvOS 2 
* 只有 Visual Studio for Mac (而不是 Xamarin Studio) 才支援 MacOS High Sierra 

### <a name="cross-platform"></a>跨平台 

* [Xamarin Live Player](https://developer.xamarin.com/guides/cross-platform/live/)