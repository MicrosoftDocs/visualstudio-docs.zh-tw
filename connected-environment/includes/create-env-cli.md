---
ms.topic: include
ms.openlocfilehash: 97f9885780c9f697cfc6a58b78054761fdcd725d
ms.sourcegitcommit: 928885ace538bef5b25961358d4f166d648f196a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2018
---
## <a name="create-a-kubernetes-development-environment-in-azure"></a>在 Azure 中建立 Kubernetes 開發環境
使用已連線的環境，您可以建立完全受 Azure 管理且針對開發最佳化的 Kubernetes 型環境。 命令會在 `eastus` 中建立名為 `mydevenvironment` 的環境。
```cmd
vsce env create --name mydevenvironment --location eastus
```

支援的地區：`eastus`、`westeurope`

> [!Note]
> 這個命令約需 6 分鐘。 您可以繼續本指南，不用等候。
