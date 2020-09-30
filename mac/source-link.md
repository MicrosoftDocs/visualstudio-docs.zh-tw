---
title: 使用來源連結進行 NuGet 套件的調試
description: 本文說明 Visual Studio for Mac 中的「來源連結」功能。
author: heiligerdankgesang
ms.author: dominicn
ms.date: 12/16/2019
ms.assetid: 4bcb8acf-db50-4bd8-a48e-86248f00c90b
ms.openlocfilehash: 307196dc7e33d268c45a9bb126c002ad426c5558
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/30/2020
ms.locfileid: "91583914"
---
# <a name="debugging-into-nuget-packages-with-source-link"></a>使用來源連結進行 NuGet 套件的調試

來源連結技術可讓您從提供的 NuGet 中，針對 .NET 元件進行原始程式碼的偵錯工具。具有原始檔連結的 Pdb。 當開發人員建立其 NuGet 套件，並將原始檔控制中繼資料內嵌在元件和套件內時，會執行來源連結。 當 Visual Studio for Mac 中啟用來源連結時，IDE 會偵測是否有已安裝套件的原始程式檔。 Visual Studio for Mac 接著會提供下載，可讓您逐步執行套件程式碼。 來源連結也適用于 Xamarin 專案的 Mono 基底類別庫程式碼，讓您也可以逐步執行 .NET Framework 程式碼。 來源連結提供原始程式碼控制中繼資料來建立絕佳的偵錯體驗。

> [!NOTE]
> Visual Studio for Mac 目前不支援符號伺服器。 因此，不支援在符號伺服器上託管中繼資料的來源連結。

## <a name="enable-source-link"></a>啟用來源連結

若要在 Visual Studio for Mac 中啟用來源連結，請流覽至 **Visual Studio > 喜好設定 ... > 專案 > 偵錯工具** ，並確定已核取 [ **逐步執行外部程式碼** ] 核取方塊。

![顯示 [逐步執行外部程式碼] 核取方塊的喜好設定對話方塊螢幕擷取畫面](media/source-link1.png)

您可以變更 [ **下載外部程式碼** ] 中的設定，以符合您的喜好設定：
* 問： Visual Studio for Mac 會提示您下載外部程式碼
* Always： Visual Studio for Mac 會自動下載外部程式碼
* 永不： Visual Studio for Mac 不會下載相關的外部程式碼

預設會選取 [ **詢問** ]。 當您找到 NuGet 套件的外部程式碼時，將會收到下列提示：

![找到 NuGet 套件的外部程式碼時出現的提示螢幕擷取畫面](media/source-link2.png)


## <a name="see-also"></a>另請參閱

- [來源連結 GitHub 存放庫](https://github.com/dotnet/sourcelink/blob/master/README.md)
- 關於來源連結的[.net 檔](/dotnet/standard/library-guidance/sourcelink)，以及如何將來源連結支援新增至套件的詳細資訊