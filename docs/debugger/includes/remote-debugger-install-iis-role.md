---
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.openlocfilehash: 13ca035b01ec8af1277d70b3c792293a1af4687a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "89323437"
---
這些步驟只會顯示 IIS 的基本設定。 如需更深入的資訊或安裝到 Windows 桌上型電腦，請參閱[使用 ASP.NET 3.5 和 ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45)[發行至 iis](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration)或 iis 8.0。

若是 Windows Server 作業系統，請透過**伺服器管理員**中的 [**管理**] 連結或 [**儀表板**] 連結，使用 [**新增角色及功能**]。 在**伺服器角色**步驟中，核取 [網頁伺服器 (IIS)]**** 方塊。

![在選取伺服器角色步驟中選取網頁伺服器 IIS 角色。](../media/remotedbg-server-roles-ws2012.png)

在**角色服務**步驟中，選取您想要的 IIS 角色服務或接受提供的預設角色服務。 如果您想要使用發行設定和 Web Deploy 來啟用部署，請確定已選取 [ **IIS 管理腳本及工具** ]。

繼續進行確認步驟，以安裝 web 伺服器角色和服務。 安裝網頁伺服器 (IIS) 角色之後，不需要重新啟動伺服器/IIS。