---
title: "對 Visual Studio 中的 Python 進行 Azure 遠端偵錯疑難排解 | Microsoft Docs"
ms.custom: 
ms.date: 07/12/2017
ms.reviewer: 
ms.suite: 
ms.technology: devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b723b343-dffb-457e-9af7-ee48c1451e30
caps.latest.revision: "1"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.openlocfilehash: 5f8c27eb0c1360e2bd0fcf0593a8438383b6fd69
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="remote-debugging-troubleshooter-for-python-and-azure"></a>Python 和 Azure 適用的遠端偵錯疑難排解工具

下列的任何一個原因將會導致 Visual Studio 無法附加到[適用於遠端偵錯的 Azure App Service](debugging-azure-remote.md)︰

| 原因 | 解決方法 |
| --- | --- |
| 您並未安裝 Visual Studio 2013 Update 4 或更新版本。 | 從 [visualstudio.com](https://www.visualstudio.com/downloads/) 安裝適合的版本。 | 
| 部署至 App Service 的專案與在 Visual Studio 中開啟的專案不符。 | 將正確的專案載入 Visual Studio。 |
| 專案未使用偵錯組態部署。 | 以滑鼠右鍵按一下 [方案總管] 中的專案，然後選取 [發行] 以重新部署應用程式。 在 [設定] 索引標籤中，確定 [偵錯] 是選取的組態。 |
| App Service 未執行。 | 從 Visual Studio 的 [伺服器總管] 或從 Azure 入口網站啟動它。 |
| App Service 未設定網路通訊端。 | 移至 [Azure 入口網站](https://portal.azure.com)，瀏覽至您的 App Service，開啟 [設定] > [應用程式設定] 刀鋒視窗，將 [一般設定] > [Web 通訊端]設為 [開啟]，然後選取 [儲存]。 (請注意，此刀鋒視窗上顯示的 [偵錯] 選項*不*適用於 Python 偵錯。) |
| `web.debug.config` 已修改為停用偵錯 Proxy。 | 刪除該檔案，重新發行專案至 App Service，在此期間 Visual Studio 會重新建立該檔案。 |

另請參閱：

- [適用於 Python 的 Azure 遠端偵錯](debugging-azure-remote.md)
