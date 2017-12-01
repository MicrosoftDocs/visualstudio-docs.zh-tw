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
ms.openlocfilehash: 81b58a2162d7240e32e1fb2d45e462ec551155e7
ms.sourcegitcommit: 5f5587a1bcf4aae995c80d54a67b4b461f8695f3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/29/2017
---
1. 如果您想要使用 Visual Studio 中的 Web Deploy 部署應用程式，請在伺服器上安裝最新版的 Web Deploy。

    若要安裝 Web Deploy，請使用[Web Platform Installer (WebPI)](https://www.microsoft.com/web/downloads/platform.aspx)。 在 [應用程式] 索引標籤中尋找 Web Deploy。您也可以取得直接從安裝程式[Microsoft Download Center](https://www.microsoft.com/search/result.aspx?q=webdeploy&form=dlc)。 

2. 確認 Web Deploy 正在執行正確開啟**控制台 > 系統及安全性 > 系統管理工具 > 服務**並確定**Web Deployment Agent Service**執行 (服務名稱是在較舊的版本不同）。

    如果未執行的代理程式服務，請啟動它。 如果沒有完全，請移至**控制台 > 程式 > 解除安裝程式**，尋找**Microsoft Web Deploy <version>** 。 選擇**變更**安裝，並確定您選擇**將安裝至本機硬碟**Web Deploy 的元件。 完成變更安裝步驟。