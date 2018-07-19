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
ms.openlocfilehash: c22ba73b464f91bf3036541304cdf94e8660970d
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2018
ms.locfileid: "38811911"
---
1. 如果您想要使用 Visual Studio 中的 Web Deploy 部署您的應用程式，請在伺服器上安裝最新版的 Web Deploy。

    若要安裝 Web Deploy，請使用[Web Platform Installer (WebPI)](https://www.microsoft.com/web/downloads/platform.aspx)。 (若要從 IIS 中尋找 Web Platform Installer 連結，請選取**IIS**伺服器管理員 的左窗格中。 以滑鼠右鍵按一下伺服器，然後選取**Internet Information Services (IIS) 管理員**。)

    在 Web Platform Installer 中，您發現 Web Deploy 應用程式 索引標籤中。您也可以取得直接從安裝程式[Microsoft 下載中心](https://www.microsoft.com/search/result.aspx?q=webdeploy&form=dlc)。 

2. 確認 Web Deploy 正在執行正確 %installationdirectory**控制台 > 系統及安全性 > 系統管理工具 > 服務**並確定**Web Deployment Agent Service**執行 (服務名稱是在較舊版本不同）。

    如果未執行的代理程式服務，請加以啟動。 如果它根本不是存在，請移至**控制台 > 程式 > 解除安裝程式**，尋找**Microsoft Web Deploy <version>** 。 選擇**變更**安裝，並確定您選擇**將會安裝成在本機硬碟機**Web Deploy 的元件。 完成變更安裝的步驟。