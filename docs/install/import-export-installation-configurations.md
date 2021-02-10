---
title: 匯入或匯出安裝組態
titleSuffix: ''
description: 了解如何將安裝設定匯出為 .vsconfig 檔案以和其他人共用，以及如何將它匯入以進行複製。
ms.date: 05/18/2019
ms.topic: how-to
f1_keywords:
- vs.about
helpviewer_keywords:
- import installation configuration
- export installation configuration
- install Visual Studio
- Visual Studio installer
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 043622d08b5389db8bf4cce80450f62c070a0ace
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99949463"
---
# <a name="import-or-export-installation-configurations"></a>匯入或匯出安裝組態

您可以使用安裝設定檔來跨整個組織設定 Visual Studio。 若要這樣做，只需使用 Visual Studio 安裝程式將工作負載和元件資訊匯出到 .vsconfig 檔案即可。 然後，您可以將設定匯入新的安裝或現有的安裝，以及與其他人共用。

方法如下。

::: moniker range="vs-2017"

> [!NOTE]
> 僅在 Visual Studio 2017 15.9 版和更新版本提供這項功能。

::: moniker-end

## <a name="export-a-configuration"></a>匯出組態

您可以選擇從先前安裝的 Visual Studio 執行個體，或目前正在安裝的執行個體中匯出安裝設定檔。

1. 開啟 Visual Studio 安裝程式。

1. 在產品卡上，選擇 [更多] 按鈕，然後再選取 [匯出設定]。

   ![從 Visual Studio 安裝程式中的產品卡匯出設定](../install/media/vs-2019/vs-installer-export-config.png)

1. 瀏覽至或鍵入您要儲存 .vsconfig 檔案的位置，然後選擇 [檢閱詳細資料]。

   ![從 Visual Studio 安裝程式匯出設定](../install/media/vs-2019/export-configuration-confirmation.png)

1. 請確定您已獲得所需的工作負載和元件，然後選擇 [匯出]。

## <a name="import-a-configuration"></a>匯入組態

準備好匯入安裝設定檔時，請遵循下列步驟。

1. 開啟 Visual Studio 安裝程式。

1. 在產品卡上，選擇 [更多] 按鈕，然後再選取 [匯入設定]。

1. 找出要匯入的 .vsconfig 檔案，然後選擇 [檢閱詳細資料]。

1. 請確定您已獲得所需的工作負載和元件，然後選擇 [關閉]。

::: moniker range="vs-2019"

## <a name="automatically-install-missing-components"></a>自動安裝遺漏的元件

**Visual Studio 2019 中的新** 功能：當您將 .vsconfig 檔案儲存至方案根目錄，然後開啟方案時，Visual Studio 會自動偵測遺失的元件，並提示您安裝它們。

![[方案總管] 建議使用其他元件](../install/media/vs-2019/solution-explorer-config-file.png)

您還可以直接從 [方案總管] 中產生 .vsconfig 檔案。

1. 以滑鼠右鍵按一下您的方案檔案。

1. 選擇 [新增]**[安裝組態檔]** > 。

1. 確認您要儲存 .vsconfig 檔案的位置，然後選擇 [檢閱詳細資料]。

1. 請確定您已獲得所需的工作負載和元件，然後選擇 [匯出]。

::: moniker-end

> [!NOTE]
> 如需詳細資訊，請參閱[使用 .vsconfig 在整個組織中設定 Visual Studio](https://devblogs.microsoft.com/setup/configure-visual-studio-across-your-organization-with-vsconfig/) 部落格文章。

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>另請參閱

* [建立 Visual Studio 的網路安裝](create-a-network-installation-of-visual-studio.md)
* [更新 Visual Studio 的網路型安裝](update-a-network-installation-of-visual-studio.md)
* [控制 Visual Studio 部署的更新](controlling-updates-to-visual-studio-deployments.md)
* [設定企業部署的預設](set-defaults-for-enterprise-deployments.md)
