---
title: 需要 Proxy 授權 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: troubleshooting
ms.assetid: c2d24ae1-9902-460e-b72a-0299eed9ee82
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: f2de40c520bca0ea04f50ec782fec2dda531172e
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2019
ms.locfileid: "67822074"
---
# <a name="proxy-authorization-required"></a>所需的 Proxy 授權
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

**需要 Proxy 授權**使用者連接到 Visual Studio online 資源，透過 proxy 伺服器，並使用 proxy 伺服器封鎖呼叫時，通常會發生錯誤。

若要更正這個錯誤，請嘗試下列一或多個下列步驟：

- 重新啟動 Visual Studio。 應該會出現 [Proxy 驗證] 對話方塊。 在對話方塊中輸入您的認證。

- 如果上述步驟無法解決問題，這可能是因為您的 Proxy 伺服器沒有提示輸入 http://go.microsoft.com 位址的認證，而是提示輸入 *.visualStudio.com 位址的認證。 對於這些伺服器，您需要將下列 Url 新增至允許清單，以解除封鎖 Visual Studio 中的所有登入情節：

  - \* windows.net

  - *.microsoftonline.com

  - *.visualstudio.com

  - *.microsoft.com

  - *.live.com

- 您可以移除 http://go.microsoft.com 位址從允許清單，這樣 proxy 驗證對話方塊會顯示兩個 http://go.microsoft.com 位址及伺服器端點時重新啟動 Visual Studio。

- 如果您想要將您的預設認證用於 proxy，執行下列作業：

   1. 在 **%ProgramFiles%\Microsoft Visual Studio 14.0\Common7\IDE** (或 **%ProgramFiles(x86)%\Microsoft Visual Studio 14.0\Common7\IDE**) 尋找 devenv.exe.config (devenv.exe 組態檔)。

   2. 在組態檔中，找出 `<system.net>` 區塊，並加入下列程式碼：

      ```xml
      <defaultProxy enabled="true" useDefaultCredentials="true">
          <proxy bypassonlocal="True" proxyaddress=" HYPERLINK "http://<yourproxy:port#" http://<yourproxy:port#>"/>
      </defaultProxy>
      ```

      插入您的網路中的正確的 proxy 位址`proxyaddress="<http://<yourproxy:port#>`。

- 請依照下列中的指示[此部落格文章](http://blogs.msdn.com/b/rido/archive/2010/05/06/how-to-connect-to-tfs-through-authenticated-web-proxy.aspx)加入可讓您使用 proxy 的程式碼。
