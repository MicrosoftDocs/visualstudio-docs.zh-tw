---
title: 了解 Xamarin 的行動裝置開發 | Microsoft Docs
ms.custom: ''
ms.date: 03/30/2018
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e970d936-1df4-4c0c-96e3-ef6191295882
ms.technology: vs-ide-mobile
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- xamarin
ms.openlocfilehash: 30d2bf7dbcacec6490bf36584b62c200bfab0da8
ms.sourcegitcommit: a0a49cceb0fdc1465ddf76d131c6575018b628b8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/05/2018
---
# <a name="learn-about-mobile-development-with-xamarin"></a>了解 Xamarin 的行動應用程式開發

本文列出數個概觀，可協助您了解如何使用 Xamarin 來開發跨平台行動應用程式。 如果您尚未安裝 Visual Studio 和 Xamarin，請先開始進行 [設定和安裝](../cross-platform/setup-and-install.md) 程序，然後在安裝程式執行時，返回此處以檢閱這些資源。  
  
> [!NOTE]
> 除非另有註明，否則一開始您可以只閱讀此處直接連結的頁面，而不閱讀附屬頁面。 如果閱讀完這份清單後安裝程序仍在執行，您可以隨時返回並探索其他主題。  
>   
> 您也可以隨時檢閱標示為「基本概念」的主題，並於稍後回顧「深入探討」主題。  
  
## <a name="essentials-introduction-to-xamarin"></a>基本概念：Xamarin 簡介  

*10-20 分鐘*  
  
1.  [在 Visual Studio 中使用 Xamarin 建置行動應用程式](https://www.visualstudio.com/xamarin/) (visualstudio.com) 提供了 Xamarin 主要特性的簡短概要。  
  
2.  Xamarin 推廣人員 James Montemagno 的[使用 C# 和 Visual Studio 建置跨平台行動應用程式](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2015-Final-Release-Event/Building-cross-platform-mobile-apps-using-C-and-Visual-Studio-2015) (Channel9，15 分 16 秒)。 前三分鐘是 Xamarin 概觀，後面接著程式碼示範。  
  
## <a name="essentials-overview-of-the-visual-studio-and-xamarin-environment"></a>基本概念：Visual Studio 和 Xamarin 環境概觀  

*5-15 分鐘*  
  
-   您將在已安裝 Visual Studio 和 Xamarin 的 Windows 電腦上執行大部分工作。 在這部電腦上，您將直接建置 Windows 和 Android 應用程式，然後在桌面、裝置或模擬器上執行這些應用程式並進行偵錯。 您也可以透過 Mac，從遠端建置、執行 iOS 應用程式並進行偵錯。 Windows 電腦上的 Visual Studio 也可以連線到 iOS 分鏡腳本設計工具與 iOS 模擬器。  
  
-   已安裝 Xcode 和 Visual Studio for Mac 的 Mac 可作為 iOS 應用程式的組建主機、簽署主機及執行階段環境。 Windows 電腦會將 iOS 組建委派給這部 Mac。 應用程式會在 Mac 的 iOS 模擬器上執行，或直接在連接至 Mac 的行動網卡上執行。 您可以與 Mac 上的應用程式互動，但在 Visual Studio 中進行偵錯體驗。
  
以下說明這些關聯性。  
  
![Windows 和 Mac 開發電腦之間在 Xamarin 環境中的關聯性](../cross-platform/media/crossplat-xamarin-learn-1.png "CrossPlat Xamarin Learn 1")  

> [!NOTE]
> 此圖是基於完整性而顯示 Windows Phone。 使用 Xamarin 平台時，建議的程式碼共用選項是 .NET Standard 2.0 程式庫，此程式庫與 Windows Phone 或「Windows 10 行動裝置版」裝置並不相容。 

您可以從[適用於 Visual Studio 的 Xamarin.iOS 簡介](/xamarin/ios/get-started/installation/windows/introduction-to-xamarin-ios-for-visual-studio/)來進一步了解如何使用 iOS 應用程式。
  
## <a name="essentials-how-projects-are-structured"></a>基本概念：專案的結構方式  

*10-30 分鐘*  
  
1.  [共用程式碼選項](/xamarin/cross-platform/app-fundamentals/code-sharing/)。 針對新的應用程式，您應該使用 .NET Standard 程式庫來共用程式碼。 大多數商務邏輯程式碼都將位於 .NET Standard 程式庫中，包括對資料庫的存取、對 REST API 的呼叫，以及對可攜式 Xamarin 元件的呼叫。 (請參閱本文結尾的[深入探討：Xamarin 元件](#components))。 使用 Xamarin.Forms 來撰寫的通用 UI 程式碼也位於 .NET Standard 程式庫中。  
  
2.  (選擇性) [案例研究：Tasky](/xamarin/cross-platform/app-fundamentals/building-cross-platform-applications/case-study-tasky/) 針對完整功能應用程式的設計和結構說明一些最佳做法，例如使用會將資料、資料存取及商務層分隔的共用程式碼來設計專案結構。  
  
## <a name="essentials-native-and-xamarinforms-ui-layers"></a>基本概念：原生和 Xamarin.Forms UI 層  

*10-40 分鐘*  
  
Xamarin 提供兩種方法來建置絕佳的應用程式：Xamarin Native 和 Xamarin.Forms。  
  
使用 Xamarin Native 時，您可以為下列每個目標平台撰寫個別的 UI 程式碼：iOS、Android 和 Windows。  採用這種方法時，您可以直接存取平台專屬的 API，以依據平台設計自訂的 UI 體驗。  您也可以完整存取每個平台的原生設計工具和控制項，以協助建置各自的 UI。  
  
Xamarin.Forms 提供一組通用的 API，可讓您在 .NET Standard 程式庫中為所有平台撰寫共用的 UI 層。  Xamarin.Forms 會在每個目標平台上轉譯成原生控制項，以提供原生的外觀與風格。  您會使用 C# 和 XAML 來建置 UI，而不是使用設計工具。  

大多數開發人員都使用 Xamarin.Forms。 這是針對 Xamarin 新手開發人員建議採用的路徑。 Xamarin Native 方法較複雜，而需要對目標平台有更詳細的了解。
  
您不需要決定要優先採取哪種方法，應用程式可以使用 Xamarin Native 和 Xamarin.Forms 的組合來實作：  
  
-   使用 Xamarin.Forms 來建置一般用途畫面。 這些畫面會在不同平台之間提供類似的使用者介面和功能，例如登入、連絡人表單及搜尋結果。  
  
-   使用 Xamarin.Forms 中的各種自訂功能以根據個別平台來調整 UI。 最簡單的自訂選項牽涉到 `OnPlatform` API。 您也可以建立自訂檢視、延伸現有的轉譯器，以及建立自訂轉譯器。  
  
-   必要時，可使用 Xamarin Native 來建置使用每個平台獨特 UI 功能的畫面。 其中一個範例是使用原生相機擷取和影像操作的畫面。  
  
通常，您應該一開始使用 Xamarin.Forms 方案來設定跨平台的 UI 程式碼共用。 接著，再使用自訂功能來進行平台專屬的調整。 如果您需要完全為平台專屬的螢幕，您可以使用 Xamarin Native 個別加入這些螢幕。  
  
若要進一步了解：  
  
1.  [Xamarin.Forms](/xamarin/xamarin-forms/) 提供 Xamarin.Forms 與原生 UI 層 (亦即 Xamarin.iOS 和 Xamarin.Android) 的簡要概觀和優缺點比較。  
  
2.  James Montemagno 的影片 [Xamarin.Forms: Native iOS, Android & Windows apps with C# & XAML](https://channel9.msdn.com/events/Visual-Studio/Connect-event-2015/704) (Xamarin.Forms：使用 C# 和 XAML 建置原生 iOS、Android 和 Windows 應用程式) (Channel9，13 分 3 秒) 的前 3 分鐘提供另一個概觀，您可以繼續觀賞示範。  
  
3.  (選擇性) [Xamarin.Forms 簡介](/xamarin/xamarin-forms/get-started/introduction-to-xamarin-forms/)  
  
4.  (選擇性) 請參閱[裝置類別](/xamarin/xamarin-forms/platform/device/)文件中有關使用 `OnPlatform` 進行自訂的範例
  
5.  (選擇性) Jason Smith (MSDN Magazine) 的 [跨平台 - 跨行動平台與 Xamarin.Forms 共用 UI 程式碼](https://msdn.microsoft.com/magazine/dn904669.aspx) 概述 Xamarin.Forms 中的不同自訂選項，其詳細資訊則包含在[自訂轉譯器](/xamarin/xamarin-forms/app-fundamentals/custom-renderer/)中。  
  
## <a name="deeper-dive-debugging-with-emulators"></a>深入探討：使用模擬器偵錯  

*10-15 分鐘*  
  
若要在不需使用實體裝置的情況下對跨平台應用程式進行偵錯，您將必須使用以下討論的模擬器：  
  
### <a name="microsofts-android-emulator"></a>Microsoft 的 Android 模擬器 

建議您使用 Microsoft [Visual Studio 的 Android 模擬器](~/cross-platform/visual-studio-emulator-for-android.md)，這會隨 Visual Studio 一起安裝。  [Visual Studio Emulator for Android](https://channel9.msdn.com/events/Visual-Studio/Connect-event-2015/711) 影片 (Channel9，5 分 55 秒) 提供概觀和示範。  
  
### <a name="apples-ios-simulator"></a>Apple 的 iOS 模擬器

若要深入了解，請閱讀 [iOS 模擬器使用者入門](https://developer.apple.com/library/prerelease/content/documentation/IDEs/Conceptual/iOS_Simulator_Guide/GettingStartedwithiOSSimulator/GettingStartedwithiOSSimulator.html#//apple_ref/doc/uid/TP40012848-CH5-SW1) (apple.com)。  
  
### <a name="microsofts-windows-phone-emulator"></a>Microsoft 的 Windows Phone 模擬器。

若要深入了解，請參閱[使用適用於 Windows 10 行動裝置版的 Microsoft 模擬器來進行測試](/windows-uwp/windows-apps-src/debug-test-perf/test-with-the-emulator/)。  
  
<a name="components" /> 

## <a name="deeper-dive-xamarin-components"></a>深入探討：Xamarin 元件  

*10 分鐘*  
  
Xamarin 應用程式中的許多擴充功能是透過 Xamarin 元件來提供。 您可以在 [http://components.xamarin.com/](http://components.xamarin.com/)上找到可供下載的完整目錄，其中包括其他 UI 控制項、驗證、各種不同雲端服務 (例如 Microsoft Azure) 等等的元件。