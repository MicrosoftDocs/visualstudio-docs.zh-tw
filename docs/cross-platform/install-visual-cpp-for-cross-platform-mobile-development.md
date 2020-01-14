---
title: 使用C++ | 安裝跨平臺行動開發Microsoft Docs
ms.custom: ''
ms.date: 10/17/2019
ms.technology: vs-ide-mobile
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: aaea6b8d-55eb-4427-8185-c050f855c257
author: corob-msft
ms.author: corob
manager: jillfra
ms.workload:
- xplat-cplusplus
ms.openlocfilehash: c3ea8c91c54586cf54b82566a4803b464e01750c
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/13/2020
ms.locfileid: "75916487"
---
# <a name="install-cross-platform-mobile-development-with-c"></a>安裝 C++ 的跨平台行動裝置應用程式開發

您可以使用 Visual Studio 中的 C++ 來建置 Windows 傳統型應用程式、通用 Windows 平台 (UWP) 應用程式、Linux 應用程式，現在還可以建立適用於 Android 和 iOS 的應用程式。 「使用 C++ 進行行動開發」工作負載是 Visual Studio 中一組可安裝的元件，其中包括了跨平台 iOS、Android 及 UWP Visual Studio 範本。 它會安裝快速入門所需的跨平台工具和 SDK，讓您無須自行尋找、下載及設定它們。 您可以使用 Visual Studio 中的這些工具來輕鬆建立、編輯、偵錯及測試跨平台專案。 本文說明如何使用 Visual Studio，在中C++安裝開發跨平臺應用程式所需的工具和協力廠商軟體。 如需相關概觀，請參閱 [Visual C++ 跨平台行動開發](https://visualstudio.microsoft.com/vs/features/cplusplus-mdd/)

## <a name="requirements"></a>需求

::: moniker range="vs-2017"

- 如需了解安裝需求，請參閱 [Visual Studio 產品系列系統需求](/visualstudio/productinfo/vs2017-system-requirements-vs)。

   > [!IMPORTANT]
   > 如果您使用的是 Windows 7 或 Windows Server 2008 R2，您可以開發適用于 Windows 桌面應用程式、Android Native Activity 應用程式和程式庫，以及適用于 iOS 的應用程式和程式碼程式庫，而不是 Windows Store 或 UWP 應用程式的程式碼。

::: moniker-end
::: moniker range=">=vs-2019"

- 如需了解安裝需求，請參閱 [Visual Studio 產品系列系統需求](/visualstudio/releases/2019/system-requirements)。

   > [!IMPORTANT]
   > 如果您使用 Windows 7 或 Windows Server 2008 R2，則開發程式碼的對象可包括 Windows 傳統型應用程式、Android Native Activity 應用程式和程式庫，以及適用於 iOS 的應用程式和程式碼程式庫，但不包括 Windows Phone 或 UWP 應用程式。

::: moniker-end

若要建置特定裝置平台的應用程式，有幾個額外的需求：

- 隨附于 Android SDK 的 x86 Android 模擬器最適用于可使用硬體加速的電腦，例如 Intel Hardware Accelerated Execution Manager （HAXM）。 如需詳細資訊，請參閱[適用于模擬器效能的硬體加速（hyper-v & HAXM）](/xamarin/android/get-started/installation/android-emulator/hardware-acceleration?tabs=vswin&pivots=windows)。

- 建立適用于 iOS 的程式碼需要 Apple ID、iOS 開發人員計畫帳戶，以及可在 OS X Mavericks （10.9 版）或更新版本上執行[Xcode](https://developer.apple.com/xcode/) 10.2 版或更新版本的 Mac 電腦。 如需安裝步驟連結，請參閱[安裝適用於 iOS 的工具](#install-tools-for-ios)。

- Windows Phone 模擬器需要可執行 Hyper-V 的電腦。 您必須先啟用 Windows 中的 HYPER-V 功能，才能安裝和執行模擬器。 如需詳細資訊，請參閱模擬器的[系統需求](system-requirements-for-the-visual-studio-emulator-for-android.md)。

## <a name="get-the-tools"></a>取得工具

Visual Studio Community、Professional 及 Enterprise 版本中都有提供「使用 C++ 進行行動開發」。 若要取得 Visual Studio，請前往 [Visual Studio 下載](https://visualstudio.microsoft.com/downloads/)頁面。 從 Visual Studio 2015 開始，即提供跨平台行動裝置應用程式開發工具。

## <a name="install-the-tools"></a>安裝工具

Visual Studio 安裝程式包括**具有C++** 工作負載的行動裝置開發。 此工作負載會C++在 Visual Studio 中安裝 Android 和 iOS 開發所需的語言工具、範本和元件。 其中包含 Android 組建和偵錯工具所需的 GCC 和 Clang 工具組、Android SDK 和元件，以便與適用于 iOS 開發的 Mac 進行通訊。 它也會安裝支援 iOS 和 Android 應用程式開發所需的所有其他協力廠商工具和軟體發展工具組。 大多數協力廠商工具是 Android 平台支援所需的開放原始碼軟體。

- 建立C++以 android 平臺為目標的程式碼需要 Android 原C++生開發工具組（NDK）、Apache Ant 和 android 開發工具。

- Google Android Emulator 和 Intel Hardware Accelerated Execution Manager （HAXM）是選擇性的，但建議使用的元件。 （Intel HAXM 驅動程式只適用于 Intel 處理器，而且與一些 Vm （包括 Hyper-v）不相容。您可以直接在 Android 裝置上進行開發和調試，但使用您桌面上的模擬器來進行調試通常會比較容易。

- C++若要建立C++以 ios 平臺為目標的程式碼，必須要有 iOS 開發工具。

> [!NOTE]
> 如果您使用 Visual Studio 2015，請參閱[安裝適用於跨平台行動裝置應用程式開發的 Visual C++ (Visual Studio 2015)](install-visual-cpp-for-cross-platform-mobile-development.md?view=vs-2015)

### <a name="install-the-mobile-development-with-c-workload"></a>安裝「使用 C++ 進行行動開發」工作負載

1. 從 [開始] 功能表執行 [Visual Studio 安裝程式]。

1. 如果您已經安裝 Visual Studio，請選擇所要修改 Visual Studio 安裝版本的 [修改] 按鈕。 否則，請選擇 [安裝] 來安裝 Visual Studio。

1. 在 Visual Studio 安裝程式中，選取 [工作負載] 索引標籤，然後向下捲動並選取 [使用 C++ 進行行動開發] 工作負載。 選取此工作負載時，會一併選取 C++ 開發所需的其他必要元件。 您也可以選擇其他要同時安裝的工作負載和個別元件。 若要建置也將 UWP 作為目標的跨平台程式碼，請選取 [通用 Windows 平台開發] 工作負載。

1. 在 [安裝詳細資料] 窗格中，展開 [使用 C++ 進行行動開發]。 在 [選擇性] 區段中，您可以選擇額外的 NDK 版本、Google Android Emulator、Intel Hardware Accelerated Execution Manager，以及 IncrediBuild 組建加速工具。

1. 此工作負載預設會包含一或多個 Android SDK 安裝程式元件。 有額外的 Android SDK 版本可供使用。 若要為您的安裝新增一個元件，請選擇 [個別元件] 索引標籤，然後向下捲動至 [SDK、程式庫和架構] 區段來進行選取。

1. 選擇 [修改] 或 [安裝] 按鈕來安裝 [使用 C++ 進行行動開發] 工作負載，以及所選取的其他工作負載和選用元件。

   安裝完成時，關閉安裝程式，然後重新啟動電腦。 在重新開機電腦之前，協力廠商元件的某些設定動作不會生效。

   > [!IMPORTANT]
   > 您必須重新啟動，確定一切都已正確安裝。

1. 開啟 Visual Studio。

## <a name="install-tools-for-ios"></a>Install tools for iOS

您可以使用 Visual Studio 來編輯、進行偵錯工具，以及將 iOS 程式碼部署至 iOS 模擬器或 iOS 裝置。 不過，由於授許可權制，程式碼必須在 Mac 上以遠端方式建立。 若要使用 Visual Studio 建置並執行 iOS 應用程式，您必須在 Mac 上安裝及設定遠端代理程式。 如需詳細的安裝指示、必要條件及設定選項，請參閱[安裝和設定工具以使用 iOS 進行建置](../cross-platform/install-and-configure-tools-to-build-using-ios.md)。 如果您不是針對  iOS 進行建置，可以略過此步驟。

## <a name="install-or-update-dependencies-manually"></a>手動安裝或更新相依項目

如果您在安裝 [使用 C++ 進行行動開發] 工作負載 (或在 Visual Studio 2015 中則為 [Visual C++ 行動開發] 選項) 時，決定不要使用 Visual Studio 安裝程式來安裝一或多個協力廠商相依項目，則可以使用[安裝工具](#install-the-tools)中的步驟稍後安裝這些項目。 Visual Studio 安裝程式會定期更新以安裝最新的協力廠商元件。 您可以使用它來安裝已更新的 SDK 和 NDK。 您也可以獨立於 Visual Studio 安裝或更新這些項目。

您可以在 Android SDK 目錄重新執行 SDK Manager 應用程式來更新 SDK，並安裝選擇性工具和其他 API 層級。 除非您使用 [以系統管理員身分執行] 執行 SDK Manager 應用程式，否則可能無法安裝更新。 如果您有建置 Android 應用程式的問題，請檢查 SDK Manager 以確認已安裝的 SDK 是否有更新。

若要使用 Android SDK 隨附的一些 Android 模擬器，您可能需要設定硬體加速。 如需詳細資訊，請參閱[適用于模擬器效能的硬體加速（hyper-v & HAXM）](/xamarin/android/get-started/installation/android-emulator/hardware-acceleration?tabs=vswin)。

在大多數情況中，Visual Studio 皆可偵測您已安裝之協力廠商軟體的組態，並保留內部環境變數中的安裝路徑。 您可以在 Visual Studio IDE 中覆寫這些跨平台開發工具的預設路徑。

#### <a name="to-set-the-paths-for-third-party-tools"></a>若要設定協力廠商工具的路徑

1. 在 Visual Studio 功能表列上，選取 [工具] > [選項]。

1. 在 [選項] 對話方塊中，選取 [跨平台] > [C++] > [Android]。

   ![Android 工具路徑選項](../cross-platform/media/cppmdd_options_android.PNG "CPPMDD_Options_Android")

1. 若要變更工具所使用的路徑，請核取路徑旁的核取方塊，並在文字方塊中編輯資料夾路徑。 您也可以使用瀏覽按鈕 ( **...** )，開啟 [選取位置] 對話方塊並選擇資料夾。

1. 選擇 [確定] ，儲存自訂工具資料夾的位置。

## <a name="see-also"></a>請參閱

- [安裝和設定工具以使用 iOS 進行建置](install-and-configure-tools-to-build-using-ios.md)
- [Visual C++ 跨平台行動開發](https://visualstudio.microsoft.com/vs/features/cplusplus-mdd/)
