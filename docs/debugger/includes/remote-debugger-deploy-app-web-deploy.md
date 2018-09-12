---
title: 使用 Web Deploy 的部署
description: 部署使用 Visual Studio 中的 Web Deploy 應用程式
services: ''
author: mikejo5000
ms.service: ''
ms.topic: include
ms.date: 05/23/2018
ms.author: mikejo
ms.custom: include file
ms.openlocfilehash: 8c843ffa6abcb7517ebfe7cdfb0e742a5f244e07
ms.sourcegitcommit: aea5cdb76fbc7eb31d1e5cc3c8d6adb0c743220f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2018
ms.locfileid: "34478310"
---
如果您安裝 Web Deploy 使用 Web Platform Installer，您可以部署應用程式直接從 Visual Studio。

1. 啟動 Visual Studio 系統管理員權限，並重新開啟專案。

    系統管理員權限，才能部署您的應用程式使用 Web Deploy。

1. 在 [方案總管] ，以滑鼠右鍵按一下專案節點，然後選取 [發行] 。

    如果您先前已設定任何發行的設定檔**發佈**窗格隨即出現。 按一下 **新的設定檔**。

1. 針對**選取發行目標**，選取**IIS、 FTP 等**，按一下 **發行**。

    ![RemoteDBG_Publish_IISl](../media/remotedbg_iis_profile.png "RemoteDBG_Publish_IIS")

1. 針對您的 IIS 設定中輸入更正組態參數。

    ![RemoteDBG_Publish_WebDeployl](../media/remotedbg_iis_webdeploy_config.png "RemoteDBG_Publish_WebDeploy")

    如果未解析的主機名稱，當您嘗試驗證中的下一個步驟**Server**文字，請嘗試 IP 位址。 包含`http://`中的前置詞為**Server**欄位。  請確定您在使用中的連接埠 80 **Server**文字，然後確定連接埠 80 在防火牆中開啟。

1. 按一下 **下一步**，選擇**偵錯**組態，然後選擇 **移除目的地上的其他檔案**下**檔案發行**選項。

    > [!NOTE]
    > 如果您選擇發行組態時，您停用在發行時，偵錯 web.config 檔案中。

1. 按一下  **Prev**，然後選擇**Validate**。 如果在連線設定驗證，您可以嘗試發行。

1. 按一下 **發佈**發行應用程式。

    [輸出] 索引標籤會顯示您是否已成功，發佈，並且您的瀏覽器，然後開啟應用程式。

    如果您收到錯誤一提的是 Web Deploy，重新檢查的 Web Deploy 的安裝步驟，並確定已開啟正確的連接埠 （Web Deploy 也需要連接埠 8172 開啟伺服器上）。

    如果應用程式部署成功，但無法正確地執行，可能是您的 IIS 組態、 ASP.NET 安裝或您的網站設定發生問題。 在 Windows 伺服器上，開啟網站從 IIS 更特定的錯誤訊息，並再重新檢查先前的步驟。
