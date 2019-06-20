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
ms.sourcegitcommit: b468d71052a1b8a697f477ab23a3644de139f1e9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2019
ms.locfileid: "67256207"
---
這些步驟會顯示 IIS 的基本組態。 如需詳細的深入資訊，或安裝至 Windows 桌面的電腦，請參閱[Publishing to IIS](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration)或是[IIS 8.0 使用 ASP.NET 3.5 和 ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45)。

對於 Windows Server 作業系統中，使用**新增角色及功能**透過精靈**管理**連結或**儀表板**連結**伺服器管理員**. 在**伺服器角色**步驟中，核取 [網頁伺服器 (IIS)]  方塊。

![在選取伺服器角色步驟中選取網頁伺服器 IIS 角色。](../media/remotedbg-server-roles-ws2012.png)

在**角色服務**步驟中，選取您想要的 IIS 角色服務或接受提供的預設角色服務。 如果您想要啟用部署使用發佈設定和 Web Deploy，請確定**IIS 管理指令碼及工具**已選取。

繼續執行安裝的 web 伺服器角色和服務的確認步驟。 安裝網頁伺服器 (IIS) 角色之後，不需要重新啟動伺服器/IIS。