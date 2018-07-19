---
title: 安裝 Xamarin for Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 03/30/2018
ms.topic: conceptual
ms.assetid: 2cfcad00-352c-4161-814c-f5ae32d8ada8
ms.prod: visual-studio-dev15
ms.technology: vs-ide-mobile
author: charlespetzold
ms.author: chape
manager: crdun
ms.workload:
- xamarin
ms.openlocfilehash: a0f9240cd729d26eecd3c098c28799369b48cea6
ms.sourcegitcommit: db680e8fa8066f905e7f9240342ece7ab9259308
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/09/2018
ms.locfileid: "37924365"
---
# <a name="setup-and-install"></a>設定和安裝

若要使用 Xamarin 從通用 C#/.NET 程式碼基底建置原生的 iOS、Android 和 Windows 應用程式，您會需要以下硬體和軟體：

-   對於 Windows 和 Android 應用程式：已安裝 Visual Studio 2017 (含 Xamarin 開發功能) 的 Windows 開發電腦 (非虛擬機器)。

-   對於 iOS 應用程式：已安裝 Xcode 的 macOS Sierra 10.12 或更新版本的 Mac，且已安裝 Visual Studio for Mac。

使用 Xamarin 平台不需要個別的授權。

您可以同時設定 Windows 和 Mac 電腦，並在安裝程式執行期間瀏覽[了解 Xamarin 的行動裝置開發](../cross-platform/learn-about-mobile-development-with-xamarin.md)，以閱讀並留意必要的背景資料。

如果您在執行此設定和安裝之後有使用 Xamarin 平台的問題，請在 [forums.xamarin.com](http://forums.xamarin.com/) \(英文\) 上張貼您的問題。

<a name="prereq" />

## <a name="pre-requisites"></a>必要條件

###  <a name="for-targeting-windows-and-android"></a>以 Windows 和 Android 為目標

如需安裝 Visual Studio 2017 的詳細必要條件，請參閱 [Visual Studio 2017 產品系列系統需求](/visualstudio/productinfo/vs2017-system-requirements-vs)。

在執行 Windows 10 且已安裝所有更新的實體 Windows 電腦 (非虛擬機器) 上安裝 Visual 2017。

### <a name="for-targeting-ios"></a>以 iOS 為目標

在 Windows 電腦上，若要以 iOS 模擬器和裝置為目標，則也需要連上網路且執行 macOS 10.12 或更新版本的 Mac 或 Mac mini，以及 Xcode 8.3。 如需詳細必要條件，請參閱[設定與安裝 Visual Studio for Mac](/visualstudio/mac/installation)。

<a name="windows" />

##  <a name="windows-setup-visual-studio-and-xamarin"></a>Windows 設定 (Visual Studio 和 Xamarin)

如果您尚未安裝 Visual Studio 2017，請執行以下步驟：

1.  [下載並啟動任何 Visual Studio 2017 版本的安裝程式](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) (Community、Professional 或 Enterprise)。 Visual Studio 2017 Community 是免費的版本。 Professional 和 Enterprise 版本提供 30 天的試用期，過了之後就需要授權。

2.  當 [正在安裝] 對話方塊出現時，請選取以下方塊：

    - [行動裝置與遊戲] > [使用 .NET 進行行動開發]。 此選項也會自動選取各種 Android 工具和軟體開發套件。

        ![選取 [遊戲與行動開發] 下的 [行動開發] 選項](../cross-platform/media/cross-plat-xamarin-setup-2a.png "跨平台 Xamarin 設定 2")

    - (選擇性) [Windows] > [通用 Windows 平台開發]。

如果您已安裝 Visual Studio 2017，但尚未安裝 Xamarin 平台，請執行以下步驟：

1. 從 [開始] 功能表執行 [Visual Studio 安裝程式]。

2.  在安裝程式中，按一下 [更多] 按鈕，然後選擇 [修改]：

    ![在 Visual Studio 安裝中選擇 [修改] 選項](../cross-platform/media/cross-plat-xamarin-setup-1a.png "跨平台 Xamarin 設定 1")

3.  當 [正在安裝] 對話方塊出現時，請選取 [行動裝置與遊戲] > [使用 .NET 進行行動開發]，以及 (選擇性) [Windows] > [通用 Windows 平台開發]。 [使用 .NET 進行行動開發] 選項也會更新任何現有的 Xamarin 安裝。

當安裝正在執行時，您可以繼續閱讀 Mac 設定指示，並詳閱[了解 Xamarin 的行動應用程式開發](../cross-platform/learn-about-mobile-development-with-xamarin.md)。

5.  一旦安裝完成後，請啟動 Visual Studio 並登入您的 Microsoft 帳戶 (如果出現提示)。 此帳戶和您用於 Windows 的帳戶相同。

6.  如需測試 Android 應用程式但沒有實體 Android 裝置，請使用 [Android SDK 模擬器](/xamarin/android/get-started/installation/android-emulator/)。

<a name="mac" />

##  <a name="mac-setup-apple-id-xcode-and-xamarin"></a>Mac 設定 (Apple ID、Xcode 和 Xamarin)

1.  如果您還沒有 Apple 識別碼，請在 [https://appleid.apple.com](https://appleid.apple.com/) 建立免費的 Apple 識別碼。 必須使用此 Apple ID 來安裝和登入 Xcode。

2.  從 [https://developer.apple.com/xcode/](https://developer.apple.com/xcode/) \(英文\) 下載並安裝 Xcode，然後遵循[將您的帳戶新增至 Xcode](https://developer.apple.com/library/content/documentation/IDEs/Conceptual/AppStoreDistributionTutorial/AddingYourAccounttoXcode/AddingYourAccounttoXcode.html#//apple_ref/doc/uid/TP40013839-CH40-SW1) \(apple.com\) \(英文\) 中所述以新增您的 Apple ID。

3.  按照[設定與安裝 Visual Studio for Mac](/visualstudio/mac/installation) 中的指示下載並安裝 Visual Studio for Mac。

4.  當您在 Windows 和 Mac 電腦上完成安裝 Xamarin 之後，請遵循[連線到 Mac](/xamarin/ios/get-started/installation/windows/connecting-to-mac/) 上的指示執行，如此就能在 Windows 電腦上透過 Visual Studio 來使用 iOS 和 Mac。

兩部電腦必須位在相同的區域網路上。
