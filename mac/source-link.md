---
title: 使用源連結調試到 NuGet 包
description: 本文介紹了 Mac 視覺化工作室中的源連結功能。
author: heiligerdankgesang
ms.author: dominicn
ms.date: 12/16/2019
ms.assetid: 4bcb8acf-db50-4bd8-a48e-86248f00c90b
ms.openlocfilehash: 530ad09bbf72d9696621f328c2df40b37f362c13
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/20/2020
ms.locfileid: "75451486"
---
# <a name="debugging-into-nuget-packages-with-source-link"></a>使用源連結調試到 NuGet 包

源連結技術支援從 NuGet 該船舶對 .NET 程式集進行原始程式碼調試。具有原始檔案的 PDFB。 當開發人員創建其 NuGet 包並在程式集和包中嵌入原始程式碼管理中繼資料時，源連結將執行。 在 Mac 的 Visual Studio 中啟用源連結時，IDE 將檢測原始檔案是否可用於已安裝的套裝軟體。 然後，Mac 的 Visual Studio 將提供下載它們，這允許您單一步驟套裝軟體代碼。 源連結還適用于 Xamarin 專案的單一基類庫代碼，允許您也進入 .NET 框架代碼。 來源連結提供原始程式碼控制中繼資料來建立絕佳的偵錯體驗。

> [!NOTE]
> 適用于 Mac 的視覺化工作室當前不支援符號伺服器。 因此，不支援具有符號伺服器上託管中繼資料的源連結。

## <a name="enable-source-link"></a>啟用源連結

要在 Mac 的視覺化工作室中啟用源連結，請流覽到**視覺化 Studio >首選項... >專案>調試器**，並確保選中"**進入外部代碼"** 核取方塊。

![顯示"進入外部代碼"核取方塊的首選項對話方塊的螢幕截圖](media/source-link1.png)

您可以更改 **"下載外部代碼"** 中的設置，以適合您的首選項：
* 詢問：Mac 的視覺化工作室將提示您下載外部代碼
* 始終：Mac 的視覺化工作室將自動下載外部代碼
* 從不：Mac 的視覺化工作室不會下載相關的外部代碼

預設情況下，選擇 **"詢問**"。 當找到 NuGet 包的外部代碼時，您將收到以下提示：

![找到 NuGet 包的外部代碼時出現的提示符螢幕截圖](media/source-link2.png)


## <a name="see-also"></a>另請參閱

- [源連結 GitHub 存儲庫](https://github.com/dotnet/sourcelink/blob/master/README.md)
- [.NET](https://docs.microsoft.com/dotnet/standard/library-guidance/sourcelink)有關源連結的文檔，以及如何向包添加源連結支援的詳細資訊
