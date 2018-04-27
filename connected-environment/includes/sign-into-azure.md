---
ms.topic: include
ms.openlocfilehash: 502bd8d206b43fc219c850ab870db35e6c3af1c0
ms.sourcegitcommit: 928885ace538bef5b25961358d4f166d648f196a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2018
---
## <a name="sign-in-to-azure"></a>登入 Azure
我們需要登入 Azure 以建立我們的開發環境。 在終端機視窗中鍵入下列命令：
```cmd
az login
```

> [!Note]
> 如果您沒有 Azure 訂用帳戶，您可以建立[免費帳戶](https://azure.microsoft.com/free)。

### <a name="if-you-have-multiple-azure-subscriptions"></a>如果您有多個 Azure 訂用帳戶...
您可以執行下列作業，檢視您的訂用帳戶： 
```cmd
az account list
```
尋找在 JSON 輸出中有 `isDefault: true` 的訂用帳戶。
如果這不是您想要使用的訂用帳戶，您可以變更預設訂用帳戶：
```cmd
az account set --subscription <subscription ID>
```
