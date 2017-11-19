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
ms.openlocfilehash: 2d82fc0eb60b2680be9ed2bdb7de13313593da0d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
1. 如果您想要使用 Visual Studio 中的 Web Deploy 部署應用程式，請在伺服器上安裝最新版的 Web Deploy。

    若要安裝 Web Deploy，請使用[Web Platform Installer (WebPI)](https://www.microsoft.com/web/downloads/platform.aspx)或取得直接從安裝程式[Microsoft Download Center](https://www.microsoft.com/search/result.aspx?q=webdeploy&form=dlc)。 在 [應用程式] 索引標籤中尋找 Web Deploy。 

2. 確認 Web Deploy 正在執行正確開啟**控制台 > 系統及安全性 > 系統管理工具 > 服務**並確定**Web Deployment Agent Service**執行 (服務名稱是在較舊的版本不同）。

    如果未執行的代理程式服務，請啟動它。 如果沒有完全，請移至**控制台 > 程式 > 解除安裝程式**，尋找**Microsoft Web Deploy <version>** 。 選擇**變更**安裝，並確定您選擇**將安裝至本機硬碟**Web Deploy 的元件。 完成變更安裝步驟。