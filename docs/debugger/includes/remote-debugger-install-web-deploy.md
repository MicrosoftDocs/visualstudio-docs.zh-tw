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
ms.sourcegitcommit: d1824ab926ebbc4a8057163e0edeaf35cec57433
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/24/2018
---
1. 如果您想要使用 Visual Studio 中的 Web Deploy 部署應用程式，請在伺服器上安裝最新版的 Web Deploy。

    若要安裝 Web Deploy，請使用[Web Platform Installer (WebPI)](https://www.microsoft.com/web/downloads/platform.aspx)。 (若要尋找 Web Platform Installer 連結從 IIS，請選取**IIS**伺服器管理員 的左窗格中。 以滑鼠右鍵按一下伺服器，然後選取**網際網路資訊服務 (IIS) 管理員**。)

    在 Web Platform Installer，Web Deploy 中找到的應用程式 索引標籤。您也可以取得直接從安裝程式[Microsoft Download Center](https://www.microsoft.com/search/result.aspx?q=webdeploy&form=dlc)。 

2. 確認 Web Deploy 正在執行正確開啟**控制台 > 系統及安全性 > 系統管理工具 > 服務**並確定**Web Deployment Agent Service**執行 (服務名稱是在較舊的版本不同）。

    如果未執行的代理程式服務，請啟動它。 如果沒有完全，請移至**控制台 > 程式 > 解除安裝程式**，尋找**Microsoft Web Deploy <version>** 。 選擇**變更**安裝，並確定您選擇**將安裝至本機硬碟**Web Deploy 的元件。 完成變更安裝步驟。