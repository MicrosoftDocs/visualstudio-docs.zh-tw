---
ms.topic: include
ms.openlocfilehash: 94e82185b05900101f91e4b368bb30d2aaceac03
ms.sourcegitcommit: 928885ace538bef5b25961358d4f166d648f196a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2018
ms.locfileid: "32030815"
---
## <a name="clean-up"></a>清除
若要完全刪除 Azure 中已連線的環境，包括其中所有執行中的服務，請使用 `vsce env rm` 命令。 請記住，這個動作無法復原。

下列範例會列出有效 Azure 訂用帳戶中已連線的環境，然後刪除資源群組中 'myenv-rg' 名為 'myenv' 的環境。

```cmd
vsce env list
vsce env rm --name myenv --resource-group myenv-rg
```

