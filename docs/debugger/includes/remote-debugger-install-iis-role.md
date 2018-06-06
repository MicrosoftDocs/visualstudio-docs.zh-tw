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
ms.openlocfilehash: 103000c2ded944236762ffd55603877ece7b7968
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/05/2018
ms.locfileid: "34768218"
---
這些步驟會顯示 IIS 的基本組態。 如需進一步資訊或安裝到 Windows 桌面的電腦，請參閱[發行至 IIS](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration)或[IIS 8.0 使用 ASP.NET 3.5 和 ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45)。

Windows Server 作業系統中，使用**新增角色及功能**透過精靈**管理**連結或**儀表板**中連結**伺服器管理員**. 在**伺服器角色**步驟中，核取 [網頁伺服器 (IIS)] 方塊。

![在選取伺服器角色步驟中選取網頁伺服器 IIS 角色。](../media/remotedbg-server-roles-ws2012.png)

在**角色服務**步驟中，選取您想要的 IIS 角色服務或接受提供的預設角色服務。 如果您想要部署使用啟用發佈設定及 Web Deploy，請確定**IIS 管理指令碼及工具**已選取。

繼續完成安裝網頁伺服器角色和服務的確認步驟。 安裝網頁伺服器 (IIS) 角色之後，不需要重新啟動伺服器/IIS。