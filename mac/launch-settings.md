---
title: launchSettings.json 支援
description: 本檔涵蓋在中對 launchSettings.js的支援 Visual Studio for Mac
author: sayedihashimi
ms.author: sayedha
ms.date: 09/18/2019
ms.assetid: a556f9d7-86a8-408e-aa54-392584845889
ms.openlocfilehash: df702b5d49e5204e65675c1c57d222e490a33824
ms.sourcegitcommit: 577c905de52057a741e68c2ed168ea527813fda5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2020
ms.locfileid: "88247926"
---
# <a name="launchsettingsjson"></a>launchSettings.json

當您正在開發 ASP.NET Core 專案時，您可以藉由自訂檔案 launchSettings.js的內容，設定專案在開發案例中的啟動方式。 在 Visual Studio for Mac 中，您可以使用 [專案選項] UI 或直接編輯此檔案來更新此檔案。 這個檔案與您在 Windows 上或從命令列執行 Visual Studio 時可以使用的設定檔相同 `dotnet` 。 這個檔案會儲存在您的專案中的 [Properties] 資料夾底下。

如需詳細資訊，請參閱 [在 ASP.NET Core 中使用多個環境](/aspnet/core/fundamentals/environments)。 在本文中，我們將討論如何在 Visual Studio for Mac 中更新此檔案。

## <a name="update-the-start-configuration-by-using-visual-studio-for-mac"></a>使用 Visual Studio for Mac 更新啟動設定

您可以直接在 Visual Studio for Mac 中編輯檔案上的 launchSettings.js，也可以使用專案選項來進行編輯。 若要取得專案選項，請以滑鼠右鍵按一下您的專案，然後選取 [ **選項**]。

![已選取 [選項] 的專案快捷方式功能表](media/vsmac-ctx-proj-options.png)

選取 [**執行**設定] [  >  **Configurations**  >  **預設**]。

![專案選項中的 [執行]、[設定] 和 [預設]](media/vsmac-run-config-default.png)

您主要會在這裡設定兩個專案：

- 環境變數
- 專案的應用程式 URL

## <a name="configure-environment-variables"></a>設定環境變數

您可以使用方格來指定環境變數的值。 當您在 Visual Studio for Mac 中啟動應用程式時，將會設定這些環境變數。 當您正在開發 ASP.NET Core 應用程式時，您應該知道特殊的 `ASPNETCORE_ENVIRONMENT` 環境變數。 若要深入瞭解，請參閱 [在 ASP.NET Core 中使用多個環境](/aspnet/core/fundamentals/environments)。


## <a name="configure-the-start-url"></a>設定起始 URL

若要設定應用程式將用來啟動的 URL，請移至 [ **ASP.NET Core** ] 索引標籤。

![專案選項中的應用程式 URL](media/vsmac-run-config-default-aspnetcore.png)

在這裡，您可以指定應用程式啟動時所要接聽的 URL。
