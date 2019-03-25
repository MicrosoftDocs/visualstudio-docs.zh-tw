---
title: 安裝跨平台行動裝置開發適用的 Visual C++ | Microsoft Docs
ms.custom: ''
ms.date: 05/21/2018
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
ms.openlocfilehash: f24e3460cb1298a36d0365781aa82cf55d8478d3
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2019
ms.locfileid: "57983321"
---
# <a name="install-cross-platform-mobile-development-with-c"></a>使用 C++ 來安裝跨平台行動裝置應用程式開發

您可以使用 Visual Studio 中的 C++ 來建置 Windows 傳統型應用程式、通用 Windows 平台 (UWP) 應用程式、Linux 應用程式，現在還可以建立適用於 Android 和 iOS 的應用程式。 「使用 C++ 進行行動開發」工作負載是 Visual Studio 中一組可安裝的元件，其中包括了跨平台 iOS、Android 及 UWP Visual Studio 範本。 它會安裝快速入門所需的跨平台工具和 SDK，讓您無須自行尋找、下載及設定它們。 您可以使用 Visual Studio 中的這些工具來輕鬆建立、編輯、偵錯及測試跨平台專案。 本主題描述如何安裝使用 Visual Studio 以 C++ 開發跨平台應用程式時，所需的工具和協力廠商軟體。 如需相關概觀，請參閱 [Visual C++ 跨平台行動開發](https://visualstudio.microsoft.com/vs/features/cplusplus-mdd/)

## <a name="requirements"></a>需求

- 如需了解安裝需求，請參閱 [Visual Studio 產品系列系統需求](/visualstudio/productinfo/vs2017-system-requirements-vs)。

   > [!IMPORTANT]
   > 如果您使用 Windows 7 或 Windows Server 2008 R2，則開發程式碼的對象可包括 Windows 傳統型應用程式、Android Native Activity 應用程式和程式庫，以及適用於 iOS 的應用程式和程式碼程式庫，但不包括 Windows Phone 或 UWP 應用程式。

若要建置特定裝置平台的應用程式，有幾個額外的需求：

- Windows Phone 模擬器與 Microsoft Visual Studio Emulator for Android 需要可執行 Hyper-V 的電腦。 您必須先啟用 Windows 中的 HYPER-V 功能，才能安裝和執行模擬器。 如需詳細資訊，請參閱模擬器的[系統需求](system-requirements-for-the-visual-studio-emulator-for-android.md)。

- 搭配 Android SDK 的 x86 Android 模擬器在可執行 Intel HAXM 驅動程式的電腦上效能最佳。 此驅動程式需要 Intel x64 處理器並支援 VT-x 和執行停用位元。 如需詳細資訊，請參閱 [Intel® Hardware Accelerated Execution Manager (Intel® HAXM)](https://go.microsoft.com/fwlink/p/?LinkId=536385) \(英文\)。

- 為 iOS 建置程式碼需要 Apple ID、iOS Developer Program (iOS 開發者計劃) 帳戶，以及可在 OS X Mavericks (10.9 版) 或更新版本上執行 [Xcode](https://go.microsoft.com/fwlink/p/?LinkId=536387) 6 版或更新版本的 Mac 電腦。 如需安裝步驟連結，請參閱[安裝適用於 iOS 的工具](#install-tools-for-ios)。

## <a name="get-the-tools"></a>取得工具

Visual Studio Community、Professional 及 Enterprise 版本中都有提供「使用 C++ 進行行動開發」。 若要取得 Visual Studio，請前往 [Visual Studio 下載](https://visualstudio.microsoft.com/downloads/)頁面。 從 Visual Studio 2015 開始，即提供跨平台行動裝置應用程式開發工具。

## <a name="install-the-tools"></a>安裝工具

適用於 Visual Studio 2017 的 Visual Studio 安裝程式包含「使用 C++ 進行行動開發」工作負載，會在 Visual Studio 中安裝 C++ 語言工具、範本，以及 Android 和 iOS 開發所需的元件。 它會安裝 Android 組建和偵錯所需的 GCC 和 Clang 工具組，以及開發 iOS 所用的 Mac 通訊元件。 它也會安裝支援 iOS 和 Android 應用程式開發所需的所有協力廠商工具和軟體開發套件。 大多數協力廠商工具是 Android 平台支援所需的開放原始碼軟體。

- 建置以 Android 平台為目標的 C++ 程式碼需要 Android 原生開發套件 (NDK)。

- Android 建置流程需要 Android SDK、Apache Ant 及 Java SE Development Kit。

- Google Android Emulator 和 Intel Hardware Accelerated Execution Manager 是選用但建議使用的元件。 您可以在 Android 裝置上直接進行開發和偵錯，但在桌面上使用模擬器來進行偵錯通常較簡單。 Microsoft 也提供可個別安裝的 Visual Studio Android 模擬器。

### <a name="install-the-mobile-development-with-c-workload"></a>安裝「使用 C++ 進行行動開發」工作負載

1. 從 [開始] 功能表執行 [Visual Studio 安裝程式]。

1. 如果您已經安裝 Visual Studio，請選擇所要修改 Visual Studio 安裝版本的 [修改] 按鈕。 否則，請選擇 [安裝] 來安裝 Visual Studio。

1. 在 Visual Studio 安裝程式中，選取 [工作負載] 索引標籤，然後向下捲動並選取 [使用 C++ 進行行動開發] 工作負載。 選取此工作負載時，會一併選取 C++ 開發所需的其他必要元件。 您也可以選擇其他要同時安裝的工作負載和個別元件。 若要建置也將 UWP 作為目標的跨平台程式碼，請選取 [通用 Windows 平台開發] 工作負載。

1. 在 [安裝詳細資料] 窗格中，展開 [使用 C++ 進行行動開發]。 在 [選擇性] 區段中，您可以選擇額外的 NDK 版本、Google Android Emulator、Intel Hardware Accelerated Execution Manager，以及 IncrediBuild 組建加速工具。

1. 此工作負載預設會包含一或多個 Android SDK 安裝程式元件。 有額外的 Android SDK 版本可供使用。 若要為您的安裝新增一個元件，請選擇 [個別元件] 索引標籤，然後向下捲動至 [SDK、程式庫和架構] 區段來進行選取。

1. 選擇 [修改] 或 [安裝] 按鈕來安裝 [使用 C++ 進行行動開發] 工作負載，以及所選取的其他工作負載和選用元件。

   安裝完成時，關閉安裝程式，然後重新啟動電腦。 適用於協力廠商元件的部分安裝動作要在重新啟動電腦之後才會生效。

   > [!IMPORTANT]
   > 您必須重新啟動，確定一切都已正確安裝。

1. 開啟 Visual Studio。

> [!NOTE]
> 如果您使用 Visual Studio 2015，請參閱[安裝適用於跨平台行動裝置應用程式開發的 Visual C++ (Visual Studio 2015)](/cross-platform/install-visual-cpp-for-cross-platform-mobile-development?view=vs-2015)

## <a name="install-tools-for-ios"></a>Install tools for iOS

您可以使用「適用於跨平台行動裝置應用程式開發的 Visual C++」來針對 iOS 程式碼進行編輯、偵錯並將其部署至 iOS 模擬器或 iOS 裝置，但由於授權限制的緣故，必須從遠端在 Mac 上建置程式碼。 若要使用 Visual Studio 建置並執行 iOS 應用程式，您必須在 Mac 上安裝及設定遠端代理程式。 如需詳細的安裝指示、必要條件及設定選項，請參閱[安裝和設定工具以使用 iOS 進行建置](../cross-platform/install-and-configure-tools-to-build-using-ios.md)。 如果您不是針對  iOS 進行建置，可以略過此步驟。

## <a name="install-or-update-dependencies-manually"></a>手動安裝或更新相依項目

如果您在安裝 [使用 C++ 進行行動開發] 工作負載 (或在 Visual Studio 2015 中則為 [Visual C++ 行動開發] 選項) 時，決定不要使用 Visual Studio 安裝程式來安裝一或多個協力廠商相依項目，則可以使用[安裝工具](#install-the-tools)中的步驟稍後安裝這些項目。 Visual Studio 安裝程式會定期更新以安裝最新的協力廠商元件。 您可以使用它來安裝已更新的 SDK 和 NDK。 您也可以獨立於 Visual Studio 安裝或更新這些項目。

> [!CAUTION]
> 您可以依任何順序安裝相依項目，除了 Java 之外。 您必須先安裝及設定 JDK，再安裝 Android SDK。

請閱讀下列資訊並使用這些連結，以手動安裝相依項目。

- [Java SE 開發套件](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)

   根據預設，安裝程式會將 Java 工具放在 *C:\Program Files (x86)\Java*。

- [Android SDK](https://developer.android.com/sdk/index.html#command-tools)

   在安裝期間，請依照建議更新 API。 確定至少已安裝 Android 5.0 Lollipop (API 層級 21) 的 SDK。 根據預設，安裝程式會將 Android SDK 放在 *C:\Program Files (x86)\Android\android-sdk*。

   您可以在 Android SDK 目錄重新執行 SDK Manager 應用程式來更新 SDK，並安裝選擇性工具和其他 API 層級。 除非您使用 [以系統管理員身分執行]  執行 SDK Manager 應用程式，否則可能無法安裝更新。 如果您有建置 Android 應用程式的問題，請檢查 SDK Manager 以確認已安裝的 SDK 是否有更新。

   若要使用 Android SDK 隨附的一些 Android 模擬器，您必須安裝選擇性的 Intel HAXM 驅動程式。 您可能必須從 Windows 移除 Hyper-V 功能，以便順利安裝 Intel HAXM 驅動程式。 您必須還原 Hyper-V 功能，以使用 Windows Phone 模擬器和 Microsoft Visual Studio Emulator for Android。 如需詳細資訊，請參閱 [Android Emulator 硬體加速](https://docs.microsoft.com/xamarin/android/get-started/installation/android-emulator/hardware-acceleration?tabs=vswin)。

- [Android NDK](https://developer.android.com/tools/sdk/ndk/index.html)

   根據預設，安裝程式會將 Android NDK 放在 *C:\ProgramData\Microsoft\AndroidNDK*。 您可以重新下載並安裝 Android NDK，以更新 NDK 安裝。

- [Apache Ant](https://ant.apache.org/bindownload.cgi)

   根據預設，安裝程式會將 Apache Ant 放在 *C:\Program Files (x86)\Microsoft Visual Studio 14.0\Apps*。

- [Microsoft Visual Studio Emulator for Android](https://aka.ms/vscomemudownload)

   「Microsoft Visual Studio 的 Android 模擬器」是一款選用的模擬器，適合用來進行程式碼測試與偵錯。 在「Visual Studio 的 Android 模擬器」發行之後，Google 將其 Android 模擬器更新成透過 Intel 的 HAXM 使用硬體加速。 建議您儘可能使用 Google 的加速模擬器，因為它可讓您存取最新的 Android OS 映像和 Google Play 服務。

在大多數情況中，Visual Studio 皆可偵測您已安裝之協力廠商軟體的組態，並保留內部環境變數中的安裝路徑。 您可以在 Visual Studio IDE 中覆寫這些跨平台開發工具的預設路徑。

#### <a name="to-set-the-paths-for-third-party-tools"></a>若要設定協力廠商工具的路徑

1. 在 Visual Studio 功能表列上，選取 [工具] > [選項]。

1. 在 [選項] 對話方塊中，選取 [跨平台] > [C++] > [Android]。

   ![Android 工具路徑選項](../cross-platform/media/cppmdd_options_android.PNG "CPPMDD_Options_Android")

1. 若要變更工具所使用的路徑，請核取路徑旁的核取方塊，並在文字方塊中編輯資料夾路徑。 您也可以使用瀏覽按鈕 (**...**)，開啟 [選取位置]  對話方塊並選擇資料夾。

1. 選擇 [確定]  ，儲存自訂工具資料夾的位置。

## <a name="see-also"></a>另請參閱

- [安裝和設定工具以使用 iOS 進行建置](install-and-configure-tools-to-build-using-ios.md)
- [Visual C++ 跨平台行動開發](https://go.microsoft.com/fwlink/p/?LinkId=536383)
