---
title: 使用來源連結進行 NuGet 套件的調試
description: 本文說明 Visual Studio for Mac 中的來源連結功能。
author: heiligerdankgesang
ms.author: dominicn
ms.date: 12/16/2019
ms.assetid: 4bcb8acf-db50-4bd8-a48e-86248f00c90b
ms.openlocfilehash: 530ad09bbf72d9696621f328c2df40b37f362c13
ms.sourcegitcommit: 8e123bcb21279f2770b28696995450270b4ec0e9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/25/2019
ms.locfileid: "75451486"
---
# <a name="debugging-into-nuget-packages-with-source-link"></a>使用來源連結進行 NuGet 套件的調試

來源連結技術可讓您從隨附的 NuGet，對 .NET 元件進行原始程式碼的偵錯工具。具有來源檔案連結的 Pdb。 來源連結會在開發人員建立其 NuGet 套件，並將原始檔控制中繼資料內嵌在元件和封裝內時執行。 在 Visual Studio for Mac 中啟用 [來源連結] 時，IDE 會偵測是否有原始程式檔可供已安裝的封裝使用。 Visual Studio for Mac 接著會提供下載，讓您逐步執行封裝程式碼。 來源連結也適用于 Xamarin 專案的 Mono 基類庫程式碼，讓您也可以逐步執行 .NET Framework 程式碼。 來源連結提供原始程式碼控制中繼資料來建立絕佳的偵錯體驗。

> [!NOTE]
> Visual Studio for Mac 目前不支援符號伺服器。 因此，不支援在符號伺服器上主控中繼資料的來源連結。

## <a name="enable-source-link"></a>啟用來源連結

若要在 Visual Studio for Mac 中啟用來源連結，請流覽至**Visual Studio > 喜好設定 .。。> 專案 > 偵錯工具**，並確定已核取 [**逐步執行外部程式碼**] 核取方塊。

![顯示逐步執行外部程式碼核取方塊的 [喜好設定] 對話方塊螢幕擷取畫面](media/source-link1.png)

您可以變更 [**下載外部程式碼**] 中的設定，以符合您的偏好：
* 詢問： Visual Studio for Mac 會提示您下載外部程式碼
* 一律： Visual Studio for Mac 會自動下載外部程式碼
* 永不： Visual Studio for Mac 不會下載相關的外部程式碼

預設會選取 [**詢問**]。 當您找到 NuGet 套件的外部程式碼時，您會收到下列提示：

![為 NuGet 套件找到外部程式碼時出現的提示螢幕擷取畫面](media/source-link2.png)


## <a name="see-also"></a>請參閱

- [來源連結 GitHub 存放庫](https://github.com/dotnet/sourcelink/blob/master/README.md)
- 關於來源連結的[.net 檔](https://docs.microsoft.com/dotnet/standard/library-guidance/sourcelink)，以及有關如何將來源連結支援新增至封裝的詳細資訊
