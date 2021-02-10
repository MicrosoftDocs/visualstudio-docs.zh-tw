---
title: 解除封鎖遠端工具下載
description: 解除封鎖 Windows Server 上的遠端工具下載，這可能會因為預設的 IE 安全性設定而相當耗時。
ms.custom: SEO-VS-2020
ms.date: 07/19/2018
ms.topic: troubleshooting
helpviewer_keywords:
- remote debugging, unblock download
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ffefa70c59658382073a10db8ae1832b0d9b03c7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99934555"
---
# <a name="how-to-unblock-the-download-of-the-remote-tools-on-windows-server"></a>如何：解除封鎖 Windows Server 上的遠端工具下載

Internet Explorer 在 Windows Server 上的預設安全性設定，可能會花很多時間來下載像是遠端工具的元件。

* Internet Explorer 上會啟用增強式安全性設定，以防止您開啟網站及存取 web 資源，除非明確允許包含該資源的網域 (也就是信任的) 。 雖然您可以停用此設定，但我們不建議您這麼做，因為它可能會帶來安全性風險。

* 在 Windows Server 2016 上， **internet Options**  >  **Security**  >  **網際網路**  >  **自訂層級**  >  **下載** 的預設設定也會停用檔案下載。 如果您選擇直接在 Windows Server 上下載遠端工具，您必須啟用檔案下載。

若要下載 Windows Server 上的工具，建議您執行下列其中一項動作：

* 在另一部電腦上下載遠端工具，例如執行 Visual Studio 的電腦，然後將 *.exe* 檔複製到 Windows Server。

* 從 Visual Studio 電腦上 [的檔案共用](../debugger/remote-debugging.md#fileshare_msvsmon) 執行遠端偵錯程式。

* 直接在 Windows Server 上下載遠端工具，並接受提示以新增信任的網站。 新式網站通常包含許多協力廠商資源，可能會導致許多提示。 此外，您可能需要手動新增任何重新導向的連結。 在開始下載之前，您可以選擇新增一些受信任的網站。 移至 [ **網際網路選項] > 安全性 > 信任的網站 > 網站** ]，並新增下列網站。

  * visualstudio.microsoft.com
  * download.visualstudio.microsoft.com
  * 關於：空白

  針對 my.visualstudio.com 上較舊版本的偵錯工具，請新增這些其他網站，以確定登入成功：

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

    如果您選擇在下載遠端工具時新增這些網域，請在出現提示時選擇 [ **新增** ]。

    ![封鎖的內容對話方塊](../debugger/media/remotedbg-blocked-content.png)

    當您下載此軟體時，您會取得更多要求，以授與載入各種網站腳本和資源的許可權。 在 my.visualstudio.com 上，建議您新增額外的網域，以確保登入成功。