---
title: 自動套用產品金鑰
description: 了解部署 Visual Studio 時如何以程式設計方式套用產品金鑰。
ms.date: 09/24/2019
ms.custom: seodec18
ms.topic: conceptual
ms.assetid: d79260be-6234-4fd3-89b5-a9756b4a93c1
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 029c2829e1a31f3fc5329e38d1f369afafa17f6e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99868708"
---
# <a name="automatically-apply-product-keys-when-deploying-visual-studio"></a>在部署 Visual Studio 時自動套用產品金鑰

您能以程式設計方式套用您的產品金鑰，作為用來自動化部署 Visual Studio 的一部分指令碼。 您可以在 Visual Studio 安裝期間或完成安裝後，以程式設計方式在裝置上設定產品金鑰。

## <a name="apply-the-license-after-installation"></a>在安裝後套用授權

::: moniker range="vs-2017"

您可以在目標電腦上以無訊息模式使用 `StorePID.exe` 公用程式，利用產品金鑰來啟用已安裝的 Visual Studio 版本。 `StorePID.exe` 是與 Visual Studio 2017 一起安裝的公用程式，其預設位置如下： <br> `C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE`

::: moniker-end

::: moniker range="vs-2019"

您可以在目標電腦上以無訊息模式使用 `StorePID.exe` 公用程式，利用產品金鑰來啟用已安裝的 Visual Studio 版本。 `StorePID.exe` 是與 Visual Studio 2019 一起安裝的公用程式，其預設位置如下： <br> `C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise\Common7\IDE`

::: moniker-end

 使用 System Center 代理程式或提升權限的命令提示字元，以較高的權限執行 `StorePID.exe`。 之後，請使用產品金鑰和 Microsoft 產品代碼 (MPC)。

>[!IMPORTANT]
> 務必包含產品金鑰的破折號。

 ```cmd
 StorePID.exe [product key including the dashes] [MPC]
 ```

::: moniker range="vs-2017"

下列範例示範的命令列可套用 MPC 為 08860、產品金鑰為 `AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE` 並採用預設安裝位置的 Visual Studio 2017 Enterprise 授權：

```cmd
"C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\StorePID.exe" AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE 08860
```

::: moniker-end

::: moniker range="vs-2019"

下列範例示範的命令列可套用 MPC 為 09260、產品金鑰為 `AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE` 並採用預設安裝位置的 Visual Studio 2019 Enterprise 授權：

```cmd
"C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise\Common7\IDE\StorePID.exe" AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE 09260
```

::: moniker-end

::: moniker range="vs-2017"

 下表列出每個 Visual Studio 版本的 MPC 代碼：

| Visual Studio 版本                | MPC   |
|--------------------------------------|-------|
| Visual Studio Enterprise 2017        | 08860 |
| Visual Studio Professional 2017      | 08862 |
| Visual Studio Test Professional 2017 | 08866 |

::: moniker-end

::: moniker range="vs-2019"

| Visual Studio 版本                | MPC   |
|--------------------------------------|-------|
| Visual Studio Enterprise 2019        | 09260 |
| Visual Studio Professional 2019      | 09262 |

::: moniker-end

如果 `StorePID.exe` 成功套用產品金鑰，則會傳回值為 0 的 `%ERRORLEVEL%`。 如果發生錯誤，則會根據錯誤狀況傳回下列其中一個代碼：

| 錯誤                     | 程式碼 |
|---------------------------|------|
| `PID_ACTION_SUCCESS`      | 0    |
| `PID_ACTION_NOTINSTALLED` | 1    |
| `PID_ACTION_INVALID`      | 2    |
| `PID_ACTION_EXPIRED`      | 3    |
| `PID_ACTION_INUSE`        | 4    |
| `PID_ACTION_FAILURE`      | 5    |
| `PID_ACTION_NOUPGRADE`    | 6    |

> [!NOTE]
> 當您執行 Visual Studio 的虛擬實例時，請確定您也會將本機 AppData 資料夾和登錄虛擬化。 若要針對虛擬實例進行疑難排解，請執行 `C:\Program Files (x86)\Microsoft Visual Studio\<version>\Common7\IDE\DDConfigCA.exe` 。  

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>另請參閱

* [安裝 Visual Studio](../install/install-visual-studio.md)
* [建立 Visual Studio 的離線安裝](../install/create-an-offline-installation-of-visual-studio.md)
