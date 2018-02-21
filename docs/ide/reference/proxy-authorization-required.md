---
title: "更正所需的 Proxy 授權錯誤 | Microsoft Docs"
ms.custom: 
ms.date: 09/22/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c2d24ae1-9902-460e-b72a-0299eed9ee82
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: e33e0e2896ccb3a5f7fe6d6da57f509af30d77fe
ms.sourcegitcommit: 06cdc1651aa7f45e03d260080da5a623d6258661
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/15/2018
---
# <a name="proxy-authorization-required"></a>所需的 Proxy 授權

通常當使用者透過 Proxy 伺服器連線到網際網路，而 Proxy 伺服器封鎖 Visual Studio 對某些網路資源所做的呼叫時，就會發生這個錯誤。

## <a name="to-correct-this-error"></a>更正這個錯誤

- 重新啟動 Visual Studio。 應該會出現 [Proxy 驗證] 對話方塊。 在對話方塊中輸入您的認證。

- 如果上述步驟無法解決問題，這可能是因為您的 Proxy 伺服器並未提示輸入 http://go.microsoft.com 位址的認證，而是提示輸入 *.visualStudio.com 位址的認證。 對於這些伺服器，您必須將下列 URL 清單列為允許清單，以解除封鎖 Visual Studio 中的所有登入情節：

    - * windows.net

    - *.microsoftonline.com

    - *.visualstudio.com

    - *.microsoft.com

    - *.live.com

- 否則您可以從允許清單中移除 http://go.microsoft.com，這樣 Proxy 驗證對話方塊在 Visual Studio 重新啟動時，就會同時為 http://go.microsoft.com 位址及伺服器端點而顯示。

    或

- 如果您想要將您的預設認證用於 Proxy，您可以執行下列作業：

    1. 在 **%ProgramFiles%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE** 或 **%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE** 中尋找 **devenv.exe.config** (devenv.exe 設定檔)。

    1. 在組態檔中，找出 `<system.net>` 區塊，並加入下列程式碼：

        ```xml
        <defaultProxy enabled="true" useDefaultCredentials="true">
            <proxy bypassonlocal="True" proxyaddress=" HYPERLINK "http://<yourproxy:port#" http://<yourproxy:port#>"/>
        </defaultProxy>
        ```

        您必須在 `proxyaddress="<http://<yourproxy:port#>`中插入您的網路的正確 Proxy 位址。

    OR

- 您也可以遵循 [這篇文章](http://blogs.msdn.com/b/rido/archive/2010/05/06/how-to-connect-to-tfs-through-authenticated-web-proxy.aspx) 中的指令，加入允許您使用 Proxy 的程式碼。
