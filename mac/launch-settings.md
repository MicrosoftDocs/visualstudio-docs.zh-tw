---
title: Launchsettings.json. json 支援
description: 本檔涵蓋 Visual Studio for Mac 中的 Launchsettings.json 支援
author: sayedihashimi
ms.author: sayedha
ms.date: 09/18/2019
ms.assetid: a556f9d7-86a8-408e-aa54-392584845889
ms.openlocfilehash: e7de368dd26bf2724a7bc060dade46422817da1e
ms.sourcegitcommit: ea182703e922c74725045afc251bcebac305068a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2019
ms.locfileid: "71213756"
---
# <a name="launchsettingsjson"></a>Launchsettings.json json

在開發 ASP.NET Core 專案時，您可以藉由自訂檔案的內容`launchSettings.json` ，來設定您的專案在開發案例中的啟動方式。 在 Visual Studio for Mac 中，您可以使用 [專案選項] UI 或直接編輯`launchSettings.json`檔案來更新這個檔案。 這個檔案與在 Windows 上執行 Visual Studio 或使用`dotnet`從命令列執行時，可以使用相同的設定檔。 這個檔案會儲存在您的專案中`Properties`的資料夾底下。

如需更詳細的資訊，您可以移至[在 ASP.NET Core 中使用多個環境](https://docs.microsoft.com/aspnet/core/fundamentals/environments)。 在本檔中，我們將討論如何在 Visual Studio for Mac 中更新此檔案。

## <a name="updating-start-configuration-using-visual-studio-for-mac"></a>使用 Visual Studio for Mac 更新啟動設定

您可以直接在 Visual Studio for Mac `launchSettings.json`中編輯，或者您可以使用專案選項來編輯它。 若要取得專案選項，請以滑鼠右鍵按一下您的專案，然後選取 [選項]。 請參閱下圖。

![已選取專案內容功能表選項](media/vsmac-ctx-proj-options.png)

當您進入此對話方塊時，請移至 [執行 > 設定] > 預設值。

![執行設定的預設值](media/vsmac-run-config-default.png)

您主要會在這裡設定兩個專案。

 - 啟動時設定的環境變數
 - 專案的起始 URL

## <a name="configure-environment-variables"></a>設定環境變數

您可以使用方格來指定環境變數的值。 當您在 Visual Studio for Mac 內啟動應用程式時，將會設定這些環境變數。 在開發 ASP.NET Core 應用程式時，您應該注意特殊`ASPNETCORE_ENVIRONMENT`的環境變數。 若要深入瞭解，請參閱[在 ASP.NET Core 中使用多個環境](https://docs.microsoft.com/aspnet/core/fundamentals/environments)。


## <a name="configure-start-url"></a>設定起始 URL

若要設定將啟動應用程式的 URL，請移至 [ASP.NET Core] 索引標籤。

![proj 選項起始 url](media/vsmac-run-config-default-aspnetcore.png)

在這裡，您可以指定應用程式啟動時所要接聽的 URL。