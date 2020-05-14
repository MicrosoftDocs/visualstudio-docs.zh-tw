---
title: 了解組建組態
description: 本文描述 Visual Studio for Mac 中的各種組建組態
author: heiligerdankgesang
ms.author: dominicn
ms.date: 09/18/2019
ms.assetid: 78107CFA-9308-4293-A92A-9B552A259E15
ms.openlocfilehash: d1511434a34017a7f0f7da65fe1ea6956d45d497
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/20/2020
ms.locfileid: "71128404"
---
# <a name="understanding-build-configurations"></a>了解組建組態

您可以存儲解決方案和專案屬性的不同配置，在開發過程中用於不同類型的生成。 Visual Studio 使用範本為 Mac 創建的專案通常包括分別支援應用調試和部署應用的調試和發佈配置。 

如果要創建自訂配置，請參閱[創建和編輯組建組態](/visualstudio/mac/create-and-edit-configurations)。

>[!NOTE]
>本主題適用於 Visual Studio for Mac。 有關 Windows 上的視覺化工作室，請參閱[瞭解組建組態](/visualstudio/ide/understanding-build-configurations)。

## <a name="solution-configurations"></a>方案組態

解決方案配置用於指定解決方案中所有專案的配置。 通過使用"**生成>配置"** 項下的 **"配置映射**"選項卡，可以為打開的解決方案中的每個項分配目標配置。 下圖演示了這一點：

![組態對應選項](media/projects-and-solutions-image3.png)

如需有關設定的詳細資訊，請參閱由 James Montemagno 所建立的[設定管理員](https://www.youtube.com/watch?v=tjSdkqYh5Vg) \(英文\) 影片。

## <a name="project-build-configurations"></a>專案組建組態

專案往往具有多種配置。 專案目標的配置和平臺一起使用，以指定生成時要使用的屬性。 在配置之間切換允許在生成時使用不同的輸出。 例如，偵錯設定會輸出偵錯符號，可讓偵錯工具從已損毀應用程式的堆疊追蹤中解析函式名稱、參數或變數。 雖然在開發期間，這項額外資訊很有用，但它會導致檔案大小擴大，因而不適合用於發佈。

每個平台都有其組建的特定組態。 可以通過導航到 **"專案選項**"對話方塊中的 **"生成**"部分來訪問專案的組建組態頁。 通過按右鍵專案並選擇 **"選項"** 或按兩下解決方案資源管理器中的專案來打開此對話方塊。

## <a name="run-configuration"></a>回合組態

Mac 的視覺化工作室允許您設置_回合組態_。 回合組態顯示在組建組態選取器旁邊的工具列下拉式清單中，如下所示：

![回合組態下拉式清單](media/projects-and-solutions-image8.png)

回合組態是一組執行選項，具有一個名稱和數個基於不同目的定義在專案中的組態。 回合組態在專案級別定義，並且將自動為每個可執行專案創建預設值，儘管可以根據需要添加盡可能多的。 特定專案類型會自動產生其他的回合組態。 例如，watchOS 專案可能會生成_概覽和通知配置。_

配置可以與其他開發人員共用（在這種情況下，配置將存儲在 .csproj 檔中），也可以保存在本地（在這種情況下，它們將存儲在 .user 檔中）。

### <a name="android-run-configurations"></a>Android 回合組態

為 Android 專案回合組態允許在運行或調試專案時啟動特定活動、服務或廣播接收器的規範。 您可以傳遞意向額外資料並設置意圖示志，以在不同的啟動條件下測試元件。

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
