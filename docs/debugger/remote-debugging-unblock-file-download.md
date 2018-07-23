---
title: 解除封鎖遠端工具下載
ms.custom: ''
ms.date: 07/19/2018
ms.technology: vs-ide-debug
ms.topic: troubleshooting
helpviewer_keywords:
- remote debugging, unblock download
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e0586b8f0699ec2eca5843d59df1b6ddd7cecbd3
ms.sourcegitcommit: 5b767247b3d819a99deb0dbce729a0562b9654ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/20/2018
ms.locfileid: "39180657"
---
# <a name="how-to-unblock-the-download-of-the-remote-tools-on-windows-server"></a>如何： 解除封鎖 Windows Server 上的遠端工具下載

在 Windows Server 上的 Internet Explorer 中的預設安全性設定可以讓它更耗時下載元件，例如遠端工具。

* Internet Explorer 中，它會防止您從開啟網站，並存取 web 資源，除非明確允許包含資源的網域上啟用增強式的安全性設定 （也就是受信任）。 雖然您可以停用此設定，但我們不建議您這麼做因為它可以有安全性風險。

* 在 Windows Server 2016 中設定的預設值**網際網路選項** > **安全性** > **網際網路** >  **自訂層級** > **下載**也會停用檔案的下載。 如果您選擇下載直接在 Windows Server 上的遠端工具，您必須啟用檔案下載。

若要下載 Windows Server 上的工具，我們建議下列其中一項：

* 下載像是一個執行的 Visual Studio，在不同電腦上的遠端工具，然後複製 *.exe*到 Windows Server 的檔案。

* 執行遠端偵錯工具[從檔案共用](../debugger/remote-debugging.md#fileshare_msvsmon)Visual Studio 電腦上。

* 下載直接在 Windows Server 上的遠端工具，並接受提示來加入信任的網站。 現代化網站通常會包含許多協力廠商資源，因此這可能會導致很多提示。 此外，任何重新導向的連結可能需要手動加入。 您可以選擇將部分信任的網站開始下載之前。 移至**網際網路選項 > 安全性 > 受信任的站台 > 網站**然後新增下列站台。

  * visualstudio.microsoft.com
  * download.visualstudio.microsoft.com
  * 關於： 空白

  針對舊版 my.visualstudio.com 的偵錯工具中，加入這些額外的站台，以確定該登入成功：

  * microsoft.com
  * go.microsoft.com
  * download.microsoft.com
  * my.visualstudio.com
  * login.microsoftonline.com
  * login.live.com
  * secure.aadcdn.microsoftonline-p.com
  * msft.sts.microsoft.com
  * auth.gfx.ms
  * app.vssps.visualstudio.com
  * vlscppe.microsoft.com
  * query.prod.cms.rt.microsoft.com

    如果您選擇將這些網域加入下載遠端工具時，請選擇**新增**出現提示時。

    ![已封鎖的內容對話方塊](../debugger/media/remotedbg-blocked-content.png)

    當您下載軟體時，您會取得載入各種 web 站台指令碼和資源的權限授與某些其他要求。 My.visualstudio.com，建議您新增其他網域，以確定該登入成功。