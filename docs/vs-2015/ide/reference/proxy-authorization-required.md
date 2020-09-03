---
title: 需要 Proxy 授權 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: troubleshooting
ms.assetid: c2d24ae1-9902-460e-b72a-0299eed9ee82
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 848817691d7fae32f2240e3d6cac4451c4ce58c4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "74297818"
---
# <a name="proxy-authorization-required"></a>所需的 Proxy 授權
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

當使用者透過 proxy 伺服器連線到 Visual Studio 線上資源，而 proxy 伺服器封鎖這些呼叫時，通常會發生 **proxy 授權** 錯誤。

若要更正這個錯誤，請嘗試下列一或多個步驟：

- 重新啟動 Visual Studio。 應該會出現 [Proxy 驗證] 對話方塊。 在對話方塊中輸入您的認證。

- 如果上述步驟無法解決問題，這可能是因為您的 Proxy 伺服器沒有提示輸入 https://go.microsoft.com 位址的認證，而是提示輸入 *.visualStudio.com 位址的認證。 針對這些伺服器，您必須將下列 Url 新增至允許清單，以解除封鎖 Visual Studio 中的所有登入案例：

  - *.windows.net

  - *.microsoftonline.com

  - *.visualStudio.com

  - *.microsoft.com

  - *.live.com

- 您可以 https://go.microsoft.com 從允許清單中移除位址，以便在 https://go.microsoft.com 重新開機 Visual Studio 時，同時顯示位址和伺服器端點的 [proxy 驗證] 對話方塊。

- 如果您想要將預設認證用於 proxy，請執行下列動作：

   1. 在 **%ProgramFiles%\Microsoft Visual Studio 14.0\Common7\IDE** (或 **%ProgramFiles(x86)%\Microsoft Visual Studio 14.0\Common7\IDE**) 尋找 devenv.exe.config (devenv.exe 組態檔)。

   2. 在組態檔中，找出 `<system.net>` 區塊，並加入下列程式碼：

      ```xml
      <defaultProxy enabled="true" useDefaultCredentials="true">
          <proxy bypassonlocal="True" proxyaddress=" HYPERLINK "http://<yourproxy:port#" http://<yourproxy:port#>"/>
      </defaultProxy>
      ```

      在中插入您的網路的正確 proxy 位址 `proxyaddress="<http://<yourproxy:port#>` 。

- 遵循 [此 blog 文章](https://blogs.msdn.microsoft.com/rido/2010/05/06/how-to-connect-to-tfs-through-authenticated-web-proxy/) 中的指示，加入可讓您使用 proxy 的程式碼。
