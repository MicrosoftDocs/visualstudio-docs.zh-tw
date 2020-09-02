---
title: 了解組建組態
description: 本文描述 Visual Studio for Mac 中的各種組建組態
author: heiligerdankgesang
ms.author: dominicn
ms.date: 09/18/2019
ms.assetid: 78107CFA-9308-4293-A92A-9B552A259E15
ms.openlocfilehash: d1511434a34017a7f0f7da65fe1ea6956d45d497
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "71128404"
---
# <a name="understanding-build-configurations"></a>了解組建組態

您可以在開發過程中，儲存不同的解決方案和專案屬性設定，以用於不同類型的組建。 使用範本 Visual Studio for Mac 所建立的專案通常會包含可分別支援應用程式和部署應用程式之偵錯工具的偵錯工具和發行設定。 

如果您想要建立自訂設定，請參閱建立 [和編輯組建](/visualstudio/mac/create-and-edit-configurations)設定。

>[!NOTE]
>本主題適用於 Visual Studio for Mac。 針對 Windows 上的 Visual Studio，請參閱 [瞭解組建](/visualstudio/ide/understanding-build-configurations)設定。

## <a name="solution-configurations"></a>方案組態

方案設定是用來指定方案中所有專案的設定。 您可以使用**組建 >** 設定專案下的 [設定對應] 索引標籤，為開啟的解決方案**中的每**個專案指派目標設定。 如下圖所示：

![組態對應選項](media/projects-and-solutions-image3.png)

如需有關設定的詳細資訊，請參閱由 James Montemagno 所建立的[設定管理員](https://www.youtube.com/watch?v=tjSdkqYh5Vg) \(英文\) 影片。

## <a name="project-build-configurations"></a>專案組建組態

專案通常會有多個設定。 專案目標的設定和平臺會一起使用，以指定建立時要使用的屬性。 在設定之間切換，可在組建階段進行不同的輸出。 例如，偵錯設定會輸出偵錯符號，可讓偵錯工具從已損毀應用程式的堆疊追蹤中解析函式名稱、參數或變數。 雖然在開發期間，這項額外資訊很有用，但它會導致檔案大小擴大，因而不適合用於發佈。

每個平台都有其組建的特定組態。 您可以藉由流覽至 [**專案選項**] 對話方塊中的 [**組建**] 區段，來存取專案的組建設定頁面。 以滑鼠右鍵按一下專案並選取 [ **選項** ]，或按兩下 [方案瀏覽器] 中的專案，以開啟此對話方塊。

## <a name="run-configuration"></a>回合組態

Visual Studio for Mac 可讓您設定 _執行_設定。 回合組態顯示在組建組態選取器旁邊的工具列下拉式清單中，如下所示：

![回合組態下拉式清單](media/projects-and-solutions-image8.png)

回合組態是一組執行選項，具有一個名稱和數個基於不同目的定義在專案中的組態。 回合設定是在專案層級定義的，而且會自動為每個可執行檔專案建立預設值，但您可以視需要新增許多專案。 特定專案類型會自動產生其他的回合組態。 例如，watchOS 專案可能會產生  _概覽和通知設定。_

設定可以與其他開發人員共用 (在這種情況下，設定會儲存在 .csproj 檔案中) 或保存在本機 (，在這種情況下，這些設定會儲存在) 的使用者檔案中。

### <a name="android-run-configurations"></a>Android 回合組態

Android 專案的執行設定可讓特定活動、服務或廣播接收器的指定在執行或偵測專案時啟動。 您可以傳遞意圖額外的資料，並設定意圖旗標，以在不同的啟動條件下測試您的元件。

`MainLauncher` 以外的活動需要將 `Exported=true` 新增至活動屬性，才能對實體裝置進行偵錯，否則必須定義意圖篩選器。

## <a name="examples-of-data-that-might-be-included-in-run-configurations"></a>回合組態中可能包含的資料範例

下列清單提供一些可以包含在回合設定中的資料範例：

* 一般 .NET 專案
  * 替代啟動應用程式
  * 啟動引數
  * 工作目錄
  * 環境變數
  * Mono 執行階段選項 (只有在 Mono 上執行時才能使用)
* Android 專案
  * 進入點 (活動、服務、接收器)
  * 意圖引數和資料
* iOS 專案
  * 模式 (一般、背景擷取)
* iOS 延伸模組專案
  * 啟動應用程式：預設或自訂
* WatchKit 專案
  * 模式 (概覽、通知)
  * 通知承載

## <a name="see-also"></a>另請參閱

- [了解組建組態 (Windows 上的 Visual Studio)](/visualstudio/ide/understanding-build-configurations)
