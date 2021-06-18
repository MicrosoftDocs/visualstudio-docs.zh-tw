---
title: 停用或移動套件快取
description: 了解如何停用、啟用或移動 Visual Studio 部署的套件快取。
ms.date: 04/14/2017
ms.custom: seodec18
ms.topic: conceptual
f1_keywords:
- cache
- nocache
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 2429993A-3F0E-41C5-9562-FEA6AE994440
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 0584673880a56bbde0ef44ad14c24acca252c5a2
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/17/2021
ms.locfileid: "112307475"
---
# <a name="disable-or-move-the-package-cache"></a>停用或移動套件快取

套件快取能提供已安裝套件的來源，以防您需要在沒有網際網路連線的情況下修復 Visual Studio 或其他相關產品。 不過，針對某些磁碟機或系統設定，您可能不會想要保留那些套件。
安裝程式會在需要套件時下載它們，因此如果您想要節省或復原磁碟空間，可以停用或移動套件快取。

## <a name="disable-the-package-cache"></a>停用套件快取

在您使用新的安裝程式安裝、修改或修復 Visual Studio 或其他產品之前，可以針對安裝程式使用 `--nocache` 參數來啟動安裝程式。

```shell
"%ProgramFiles(x86)%\Microsoft Visual Studio\Installer\vs_installer.exe" --nocache
```

您對任何產品所做的任何作業，都會移除該產品所有的現有套件，並會避免在安裝套件之後儲存它們。 如果您在需要套件的情況下修改或修復 Visual Studio，系統會自動下載這些套件，並在安裝完成後移除它們。

如果您想要重新啟用快取，請改為傳遞 `--cache`。 系統只會針對所需的套件進行快取，因此如果您需要還原所有套件，便應該在中斷網路連線之前修復 Visual Studio。

```shell
"%ProgramFiles(x86)%\Microsoft Visual Studio\Installer\vs_installer.exe" repair --passive --norestart --cache
```

您也可以設定 `KeepDownloadedPayloads` [登錄原則](set-defaults-for-enterprise-deployments.md)來在安裝、修改或修復 Visual Studio 之前停用快取。

## <a name="move-the-package-cache"></a>移動套件快取

常見的系統組態是將 Windows 安裝在 SSD 上，並針對開發需求 (例如原始程式碼、程式二進位檔等) 使用容量較大的硬碟。 如果您想要離線工作，可以改為移動套件快取。

若要這麼做，目前的唯一方式是在安裝、修改或修復 Visual Studio 之前設定 `CachePath` [登錄原則](set-defaults-for-enterprise-deployments.md)。

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>另請參閱

* [安裝 Visual Studio](install-visual-studio.md)
* [設定企業部署的預設](set-defaults-for-enterprise-deployments.md)
* [使用命令列參數來安裝 Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
