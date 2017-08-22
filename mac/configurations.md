---
title: "了解組建組態"
description: 
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.assetid: 78107CFA-9308-4293-A92A-9B552A259E15
ms.translationtype: HT
ms.sourcegitcommit: e2b7ff9126e1cc38ac2e58d6be339b656a024e7f
ms.openlocfilehash: e435418c0c77f1577e9db8ab35d76d6bd54f8447
ms.contentlocale: zh-tw
ms.lasthandoff: 08/11/2017

---

# <a name="understanding-build-configurations"></a>了解組建組態

## <a name="project-build-configurations"></a>專案組建組態 

專案可以有多個組態，在它們之間切換可在建置時產生不同的輸出。 例如，使用偵錯組態時，輸出會包含偵錯符號，可讓偵錯工具從已損毀應用程式的堆疊追蹤解析函式名稱、參數或變數。 不過，使用偵錯組態會導致檔案大小擴大，因此不適合用於散佈的應用程式。

每個平台都有其組建的特定組態。 Xamarin.Android 開發始終只有發行或偵錯組態。 Xamarin.iOS 則具有其他組態。 較新的 iOS 專案只有偵錯或發行組態，但可以為裝置或任何已安裝的模擬器設定這些組態。

## <a name="solution-configurations"></a>方案組態

類似於專案組態，方案組態是用來建立整個專案的自訂組態。 透過使用 [組建] > [組態] 項目下的 [組態對應] 索引標籤，您可以為每個方案項目指派目標組態，如下所示：


 ![組態對應選項](media/projects-and-solutions-image3.png)

如需詳細資訊，請參閱 James Montemagno 所建立的[組態管理員](https://www.youtube.com/watch?v=tjSdkqYh5Vg)影片。

## <a name="run-configuration"></a>回合組態

在舊版的 Xamarin Studio 中，您可以選取此選項將專案設定為**啟始專案**，這是使用全域執行/偵錯命令時所執行/偵錯的專案。 這在專案板中是以粗體字表示專案名稱。

在 Visual Studio for Mac 中，您可以設定「回合組態」，而不是設定啟始專案。 回合組態顯示在組建組態選取器旁邊的工具列下拉式清單中，如下所示：

 ![回合組態下拉式清單](media/projects-and-solutions-image8.png)

回合組態是一組執行選項，具有一個名稱和數個基於不同目的定義在專案中的組態。 回合組態會在專案層級定義，並且會針對每個可執行專案自動建立一個預設組態，但是您可以新增所需數目的組態。 特定專案類型會自動產生其他的回合組態。 例如，watchOS 專案可能會產生「概覽和通知組態」。 
 
組態可以與其他開發人員共用 (在此情況下，組態會儲存在 .csproj 檔案)，或保留在本機中 (在此情況下，它們會儲存在 .user 檔案)。

### <a name="android-run-configurations"></a>Android 回合組態
 
Android 專案的回合組態可讓您指定執行專案或對專案進行偵錯時，所要啟動的活動、服務或廣播接收器。 您可以傳遞意圖的額外資料，並設定意圖旗標，以便能夠在不同的啟動條件下測試您的元件。

`MainLauncher` 以外的活動需要將 `Exported=true` 新增至活動屬性，才能對實體裝置進行偵錯，否則必須定義意圖篩選器。

## <a name="examples-of-data-that-might-be-included-in-run-configurations"></a>回合組態中可能包含的資料範例

下列清單提供一些可以包含在回合組態中的資料範例：

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

