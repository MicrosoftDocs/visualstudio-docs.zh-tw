---
ms.topic: include
ms.openlocfilehash: 9da28d29dc431f2f6ec92a01c397244147042f12
ms.sourcegitcommit: 928885ace538bef5b25961358d4f166d648f196a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2018
---
2. 點擊 F5 (或在終端機視窗中鍵入 `vsce up`) 來執行服務。 這樣做會在我們新選取的空間 `scott` 中自動執行它。 
1. 我們可以再次執行 `vsce list` 來確認它。 首先，您會發現 `mywebapi` 的執行個體正在 `scott` 空間中執行 (`mainline` 中執行的版本仍在執行，但卻未列出)。 其次，`webfrontend` 的存取點 URL 前面會加上文字 "scott-"。 此 URL 對 `scott` 空間而言是唯一的，而且表示傳送至 "scott URL" 的要求 會首先嘗試路由 `scott` 空間中的服務，並會切換回 `mainline` 空間中的服務。

```
Name         Space     Chart              Ports   Updated     Access Points
-----------  --------  -----------------  ------  ----------  -------------
mywebapi     scott     mywebapi-0.1.0     80/TCP  15s ago     http://localhost:61466
webfrontend  mainline  webfrontend-0.1.0  80/TCP  5h ago      https://scott-webfrontend-contosodev.vsce.io
```

![](../media/space-routing.png)

已連線的環境這項內建功能可讓您在共用環境中以端對端方式測試程式碼，不需要每位開發人員在其空間內重新建立完整的服務堆疊。 請注意，此路由需要在您的應用程式程式碼中轉送傳播標頭，如本指南上一個步驟中所示。

## <a name="test-code-in-a-space"></a>在空間中測試程式碼
若要測試我們的新版 `mywebapi` 搭配 `webfrontend`，請在您的瀏覽器中開啟 webfrontend 的公用存取點 URL，並移至 [關於] 頁面。 您應該會看到顯示的新訊息。

現在，移除 URL 的 "scott-" 部分，並重新整理瀏覽器。 您應該會看到舊的行為 (由在 `mainline` 中執行的 `mywebapi` 版本展示)。