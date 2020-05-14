---
title: 啟動設置.json 支援
description: 本文檔介紹了 Mac 視覺化工作室對啟動設置.json 的支援
author: sayedihashimi
ms.author: sayedha
ms.date: 09/18/2019
ms.assetid: a556f9d7-86a8-408e-aa54-392584845889
ms.openlocfilehash: d35bfed901dca960ae21b4e2cf2fa75067c1b3ee
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/20/2020
ms.locfileid: "73715929"
---
# <a name="launchsettingsjson"></a>launchSettings.json

開發ASP.NET核心專案時，可以通過自訂啟動設置.json 檔的內容來配置在開發方案中應如何啟動專案。 在 Mac 的 Visual Studio 中，您可以使用專案選項 UI 或直接編輯更新此檔。 此檔與在 Windows 上運行 Visual Studio 或從 命令列通過`dotnet`時可以使用的設定檔相同。 此檔存儲在"屬性"資料夾下的專案中。

有關詳細資訊，請參閱[在 ASP.NET 酷中使用多個環境](/aspnet/core/fundamentals/environments)。 在本文中，我們將介紹如何在 Mac 的 Visual Studio 中更新此檔。

## <a name="update-the-start-configuration-by-using-visual-studio-for-mac"></a>使用 Mac 的視覺化工作室更新開始配置

您可以直接編輯 Mac 視覺化工作室中的啟動設置.json 檔，也可以使用專案選項對其進行編輯。 要獲取專案選項，請按右鍵專案並選擇 **"選項**"。

![選擇"選項"的專案快捷方式功能表](media/vsmac-ctx-proj-options.png)

選擇 **"運行** > **配置** > **預設值**"。

![專案選項中的"運行"、"配置"和"預設"](media/vsmac-run-config-default.png)

首先，您將在此處配置兩件事：

 - 環境變數
 - 專案的應用 URL

## <a name="configure-environment-variables"></a>設定環境變數

可以使用網格指定環境變數的值。 當您在 Mac 的 Visual Studio 中啟動應用程式時，將設置這些環境變數。 開發ASP.NET核心應用程式時，您應該瞭解特殊的`ASPNETCORE_ENVIRONMENT`環境變數。 要瞭解更多資訊，請參閱[在 ASP.NET 酷中使用多個環境](/aspnet/core/fundamentals/environments)。


## <a name="configure-the-start-url"></a>配置啟動 URL

要配置應用程式將開始的 URL，請轉到**ASP.NET核心**選項卡。

![專案選項中的應用程式 URL](media/vsmac-run-config-default-aspnetcore.png)

在這裡，您可以指定應用程式在啟動時將偵聽的 URL。