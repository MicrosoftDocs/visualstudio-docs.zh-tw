---
ms.openlocfilehash: a292b37a50bbf667fa5b23f18879cd79c3f76805
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85292176"
---
Web Deploy 3.6 for Hosting Servers 提供其他組態功能，可讓您從 UI 建立發行設定檔。

1. 如果您已在 Windows Server 上安裝 Web Deploy，請使用**主控台**  >  **程式**  >  **卸載程式**來將它卸載。

2. 接下來，在 Windows Server 上安裝 Web Deploy 3.6 for Hosting Servers。

    若要安裝 Web Deploy for Hosting Servers，請使用 Web Platform Installer (WebPI)。 (若要從 IIS 尋找 Web Platform Installer 連結，請選取 Server Manager 左窗格中的 [IIS]****。 在 [伺服器] 窗格中，以滑鼠右鍵按一下伺服器，然後選取 [ **Internet Information Services (IIS) 管理員**。 然後，在 [**動作**] 視窗中使用 [**取得新的 Web 平臺元件**] 連結。 ) 您也可以從[下載](https://www.microsoft.com/web/downloads/platform.aspx)中取得 Web Platform Installer (WebPI) 。

    在 Web Platform Installer 中，您會在 [應用程式] 索引標籤中找到 **主控伺服器的 Web Deploy 3.6** 。

3. 如果您尚未安裝 **IIS 管理指令碼及工具**，請立即安裝。

    移至 [**選取伺服器角色**  >  **Web 服務器 (IIS) **  >  **管理工具**]，然後選取 [ **iis 管理腳本及工具**] 角色，按 **[下一步]**，然後安裝角色。

    ![安裝 IIS 管理指令碼及工具](../../deployment/media/tutorial-iis-management-scripts-and-tools.png)

    您需要這些指令碼及工具，才能產生發行設定檔。

4.  (選擇性) 透過開啟  **主控台 > [系統和安全性] > [系統管理工具**] > Services，確認 Web Deploy 正常執行，然後確定：

    * **Web Deployment Agent 服務** 正在執行 (舊版) 中的服務名稱不同。

    * **Web 管理服務** 正在執行。

    如果其中一個代理程式服務未執行，請重新開機 **Web Deployment Agent 服務**。

    如果 Web Deployment Agent 服務完全不存在，請移至**主控台 > 程式 > 卸載程式**，尋找**Microsoft Web Deploy \<version> **。 選擇 [變更]**** 安裝，並確定您針對 Web Deploy 元件選擇 [將會安裝至本機硬碟]****。 完成變更安裝步驟。