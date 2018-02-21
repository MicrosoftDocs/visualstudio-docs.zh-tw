---
title: "將私人網路中的 URL 置於白名單中 | Microsoft Docs"
ms.custom: 
ms.date: 09/19/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 4a4093c7ebba74493a64833bfbf83ee6d28ef1ef
ms.sourcegitcommit: 06cdc1651aa7f45e03d260080da5a623d6258661
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/15/2018
---
# <a name="whitelisting-urls-in-a-private-network"></a>將私人網路中的 URL 置於白名單中

如果您在使用安全性設備 (例如防火牆) 的私人網路中使用 Visual Studio，Visual Studio 可能無法連線到某些網路資源。 這些資源包括用於登入和授權的 Visual Studio Team Services (VSTS)、NuGet 和 Azure 服務。 如果 Visual Studio 無法連線到這些資源的其中一項，您會看到以下錯誤訊息：

  **基礎連線已關閉：傳送時發生未預期的錯誤**

Visual Studio 使用傳輸層安全性 (TLS) 1.2 通訊協定連線到網路資源。 有些私人網路的安全性設備在 Visual Studio 使用 TLS 1.2 時，會封鎖某些伺服器連線。 若要修正錯誤，請啟用下列 URL 連線：

- https://management.core.windows.net

- https://app.vssps.visualstudio.com

- https://login.microsoftonline.com

- https://login.live.com

- https://go.microsoft.com

- https://graph.windows.net

- https://app.vsspsext.visualstudio.com

- *.azurewebsites.net (適用於 Azure 連線)

- *.nuget.org (適用於 NuGet 連線)

- *.visualstudio.com

- cdn.vsassets.io (主機內容傳遞網路 (又稱 CDN) 內容)

- *.gallerycdn.vsassets.io (主機 VSTS 延伸模組)

- static2.sharepointonline.com (Visual Studio 在 Office 網狀架構 UI 套件中使用的主機資源，例如字型)

> [!NOTE]
> 上列清單可能不含私人擁有的 NuGet 伺服器 URL。 您可以藉由開啟 %APPData%\Nuget\NuGet.Config 來檢查您所使用的 NuGet 伺服器。

## <a name="see-also"></a>另請參閱

[需要 Proxy 授權錯誤](../ide/reference/proxy-authorization-required.md)  
[將 Visual Studio 安裝在防火牆或 Proxy 伺服器後方](../install/install-visual-studio-behind-a-firewall-or-proxy-server.md)
