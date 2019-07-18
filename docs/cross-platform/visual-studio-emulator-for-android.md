---
title: Visual Studio 的 Android 模擬器 | Microsoft Docs
ms.custom: ''
ms.date: 07/03/2018
ms.technology: vs-ide-mobile
ms.topic: conceptual
ms.assetid: 80f0104f-a4db-44dd-bd55-37bb67776c62
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3bf5a994d173a11a8515e166c3b0bc3044bdc587
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63402901"
---
# <a name="visual-studio-emulator-for-android"></a>Visual Studio Emulator for Android

Visual Studio Emulator for Android 是模擬 Android 裝置的桌面應用程式。 它提供虛擬化環境，讓您不需要實體裝置，便可以在其中偵錯及測試 Android 應用程式。 它也為您的應用程式原型提供一個隔離環境。

> [!IMPORTANT]
> 在大部分情況下，建議使用 Google Android 模擬器，而不是 Visual Studio 的 Android 模擬器：
> - Visual Studio Emulator for Android 在 Visual Studio 2015 之後不受支援。
> - Android 6.0 版以上的模擬器映像不適用於 Visual Studio Emulator for Android。
> - Google Android 模擬器現在支援 [Hyper-V](https://docs.microsoft.com/xamarin/android/get-started/installation/android-emulator/hardware-acceleration#accelerating-with-hyper-v)。
> - Visual Studio Tools for Apache Cordova 可與 Google Android 模擬器搭配使用。 如需詳細資訊，請參閱[在 Android 上執行 Apache Cordova 應用程式](/visualstudio/cross-platform/tools-for-cordova/run-your-app/run-app-android#google-android-emulator) (請注意，您不再需要停用 Hyper-V，如本文中所述)。
>
> 如需設定和使用 Google Android 模擬器的詳細資訊，請參閱 [Android Emulator 安裝](https://docs.microsoft.com/xamarin/android/get-started/installation/android-emulator/)。

 Visual Studio Emulator for Android 的設計目的，是為了提供與實際裝置相當的效能。 不過，建議您先在實體裝置上測試應用程式，再發行應用程式。

 您可以透過唯一的裝置設定檔，針對每個 Android 平台、螢幕解析度，以及 Visual Studio Emulator for Android 支援的其他硬體內容來測試應用程式。

## <a name="Installing"></a> 安裝及解除安裝
 安裝

 Visual Studio Emulator for Android 是 Visual Studio 中可用的跨平台工具元件，當您在自訂 Visual Studio 安裝期間，依序選取 [跨平台行動開發]、[一般工具和軟體開發套件] 和 [Visual Studio Emulator for Android] 時，即會自動安裝這個元件。

 解除安裝

 您可以使用 [控制台] 的 [新增/移除程式]，解除安裝 Visual Studio Emulator for Android。

> [!NOTE]
> 解除安裝 Visual Studio 不會解除安裝此模擬器。 您必須個別解除安裝模擬器。

 當您解除安裝 Visual Studio Emulator for Android 時，不會自動移除為了提供給模擬器使用所建立的 Hyper-V 虛擬乙太網路介面卡。 您可以手動移除這些虛擬介面卡 (若未使用)，方法是開啟 Hyper-V 管理員，從中選取一個模擬器 VHD 影像，再選擇 [網路] 索引標籤，然後為此索引標籤中所顯示的每個參數選擇 [移除]。

## <a name="Requirements"></a> 系統需求和回溯相容性
 如需 Visual Studio Emulator for Android 之硬體、軟體與組態需求的重要資訊，請參閱下列主題。

- [Visual Studio 的 Android 模擬器系統需求](../cross-platform/system-requirements-for-the-visual-studio-emulator-for-android.md)

  Visual Studio Emulator for Android 需要 Visual Studio 2015；它與舊版 Visual Studio 不相容。

  新版模擬器是安裝在舊版之上 (在某些情況下可能會取代舊映像，並捨棄這些映像上的設定，以及安裝在這些映像上的應用程式和檔案)。

## <a name="Networking"></a> Visual Studio 的 Android 模擬器網路功能
 Visual Studio Emulator for Android 的網路連線運作方式類似桌上型電腦的連線，並具有下列特性：

- 模擬器以具有自己 IP 位址的個別裝置形式出現在網路上。

- 它不需要模擬器尚未隨附安裝的任何其他網路軟體。

- 它未加入 Windows 網域。

  若要了解模擬器的網路連線功能，請將它視為類似從您的 Android 手機連接到相同網路的 Wi-Fi 連線。 如果您的手機上執行的應用程式可以透過其 Wi-Fi 連線存取網路資源，則模擬器上執行的應用程式也可以存取相同的網路資源。

  如需網路需求的詳細資訊，請參閱 [Visual Studio 的 Android 模擬器系統需求](../cross-platform/system-requirements-for-the-visual-studio-emulator-for-android.md)

  如需針對網路問題進行疑難排解的詳細資訊，請參閱[針對 Visual Studio 的 Android 模擬器進行疑難排解](../cross-platform/troubleshooting-the-visual-studio-emulator-for-android.md)。

## <a name="Configuring"></a> 設定 Visual Studio 的 Android 模擬器
 在各種大量的 Android 硬體之間測試 Android 應用程式的相容性可能是項挑戰。 市面上的 Android 手機和平板電腦橫跨各種版本和螢幕大小，並有許多不同的硬體組態 (RAM、CPU、架構等)。 Visual Studio Emulator for Android 簡化了使用裝置設定檔的這項工作。 我們提供了一組裝置設定檔，代表市面上最受歡迎的硬體，包括 Samsung、Motorola、Sony、LG 等裝置。

 在 Visual Studio 2015 中，您可以使用模擬器管理員，來安裝、解除安裝及啟動裝置設定檔。 若要存取 [模擬器管理員]，請依序選擇 [工具] 和 [Visual Studio 的 Android 模擬器]。

 ![Visual Studio 的 Android 模擬器管理員](../cross-platform/media/android_emu_manager.png "Android_Emu_Manager")

 預設有四個預先安裝的裝置設定檔 (5 英吋的 KitKat 和 Lollipop 手機和和 7 英吋的平板電腦組態)，如白色文字和圖示所示。 直到您選擇 [安裝設定檔] 按鈕並完成安裝為止，清單中的其他設定檔都會呈現灰色。 您可以依應用程式開發介面層級篩選清單，然後按一下設定檔右下方的詳細資料箭號，以檢視其完整組態詳細資料。

 一旦您安裝好目標設定檔集合，即可按綠色的 [播放] 按鈕，直接從管理員啟動這些新的設定檔。 這些設定檔也會出現在任何 Visual Studio 跨平台行動專案類型中的 [偵錯目標] 下拉式功能表中。

## <a name="FeaturesTest"></a> 您可以在模擬器中測試的功能
 如需可在模擬器中測試之功能的詳細資訊，請參閱此[部落格文章](https://devblogs.microsoft.com/devops/introducing-visual-studios-emulator-for-android/) \(英文\)。

## <a name="FeaturesNonTest"></a> 您無法在模擬器中測試的功能
 下列清單描述您**無法**在模擬器中測試的 Android 平台功能。 您必須在實體裝置上測試這些功能。

- 羅盤

- 迴轉儀

- 震動控制器

- 亮度。 變更模擬器的亮度不會影響裝置在螢幕上的視覺顯示方式。

## <a name="Support"></a> 支援資源
 若您的主機電腦符合系統需求，但發生了此疑難排解指南未涵蓋的問題：

- 使用 [android-emulator](http://stackoverflow.com/questions/tagged/android-emulator) 與 visual-studio 標記在 StackOverflow 上發問。

- 使用 Visual Studio 或模擬器管理員中的 [傳送笑臉] 工具回報問題。

## <a name="see-also"></a>另請參閱
 [Android 版 Visual Studio 模擬器的系統需求](../cross-platform/system-requirements-for-the-visual-studio-emulator-for-android.md) [針對 Android 版 Visual Studio 模擬器進行疑難排解](../cross-platform/troubleshooting-the-visual-studio-emulator-for-android.md)
