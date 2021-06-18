---
title: 選取安裝位置
description: 了解如何將下載快取、共用元件、SDK 和工具的位置變更為不同的磁碟機，來減少 Visual Studio 在系統磁碟機上的安裝磁碟使用量。 例如，將一些檔案從 C 磁碟機移至 D 磁碟機。
ms.date: 03/30/2019
ms.custom: acquisition
ms.topic: how-to
helpviewer_keywords:
- change installation locations for Visual Studio
- select an installation location for Visual Studio files
- move installation files to different drives
- use the D drive
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 0e780cca2515118b92b71c406368d29424f7017c
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/17/2021
ms.locfileid: "112307618"
---
# <a name="select-the-installation-locations-in-visual-studio"></a>在 Visual Studio 2017 中選取安裝位置

::: moniker range=">=vs-2019"

您可以變更某些檔案的位置，來減少 Visual Studio 在系統磁碟機上的安裝磁碟使用量。 具體而言，您可以針對下載快取、共用元件、SDK 和工具檔案使用不同的位置。

::: moniker-end

::: moniker range="vs-2017"

**15.7 版的新** 功能：您可以藉由變更部分檔案的位置，來減少系統磁片磁碟機上的 Visual Studio 安裝空間。 具體而言，您可以針對下載快取、共用元件、SDK 和工具檔案使用不同的位置。

::: moniker-end

   > [!NOTE]
   > 某些工具和 SDK 對於可安裝的位置有不同的規則。 這類工具和 SDK 會安裝在您的系統磁碟機上，即使您選擇其他位置也一樣。

準備開始使用了嗎？ 方法如下。

::: moniker range="vs-2017"

1. 當您安裝 Visual Studio 時，選擇 [安裝位置] 索引標籤。

   ![Visual Studio 2017-選取安裝位置](media/vs-installation-locations.png "選取安裝位置。")

1. 在 [Visual Studio IDE] 區段中，接受預設。 Visual Studio 會安裝核心產品，並包含本版 Visual Studio 的特定檔案。

   ![[安裝位置] 索引標籤的 Visual Studio IDE 區段](media/vs-installation-locations-ide.png "接受 [安裝位置] 索引標籤的 [Visual Studio IDE] 區段的預設值。")

   > [!TIP]
   > 如果您的系統磁碟機是固態硬碟 (SSD)，建議您接受系統磁碟機上的預設位置。 理由何在？ 當您使用 Visual Studio 開發時，您會讀取並寫入大量檔案，其會增加磁碟 I/O 活動。 最好選擇最快的磁碟機來處理負載。

1. 在 [下載快取] 區段中，決定是否要保留下載快取，然後決定要儲存其檔案的位置。

     ![[安裝位置] 索引標籤的 [下載快取] 區段](media/vs-installation-locations-cache.png "選擇是否要在安裝後保留下載快取，然後指定要儲存檔案的磁片磁碟機。")

    1. 核取或取消核取 [在安裝後保留下載快取]。

       如果您決定不要保留下載快取，則只會暫時使用此位置。 此動作不會影響或刪除先前安裝的檔案。

    1. 指定您要從下載快取儲存安裝檔案和資訊清單的磁碟機。

        例如，如果您選取 [使用 C++ 的桌面開發] 工作負載，暫時會需要系統磁碟機上 1.58 GB 的大小，然後會在安裝完成時予以釋放。

       > [!IMPORTANT]
       > 此位置會在您第一次安裝時設定，而且之後無法從安裝程式 UI 變更。 相反地，您必須[使用命令列參數](use-command-line-parameters-to-install-visual-studio.md)來移動下載快取。

1. 在 [共用的元件、工具及 SDK] 區段中，指定您要儲存檔案以供並存 Visual Studio 安裝共用的磁碟機。 SDK 和工具也會儲存在此目錄中。

   ![[安裝位置] 索引標籤的 [共用元件、工具及 Sdk] 區段](media/vs-installation-locations-shared.png "指定您要儲存共用元件、工具和 Sdk 的位置。")

::: moniker-end

::: moniker range=">=vs-2019"

1. 當您安裝 Visual Studio 時，選擇 [安裝位置] 索引標籤。

   ![Visual Studio 2019-選取安裝位置](media/vs-2019/vs-installer-installation-locations.png "選取安裝位置。")

1. 在 [Visual Studio IDE] 區段中，接受預設。 Visual Studio 會安裝核心產品，並包含本版 Visual Studio 的特定檔案。

   > [!TIP]
   > 如果您的系統磁碟機是固態硬碟 (SSD)，建議您接受系統磁碟機上的預設位置。 理由何在？ 當您使用 Visual Studio 開發時，您會讀取並寫入大量檔案，其會增加磁碟 I/O 活動。 最好選擇最快的磁碟機來處理負載。

1. 在 [下載快取] 區段中，決定是否要保留下載快取，然後決定要儲存其檔案的位置。

    * 核取或取消核取 [在安裝後保留下載快取]。

       如果您決定不要保留下載快取，則只會暫時使用此位置。 此動作不會影響或刪除先前安裝的檔案。

    * 指定您要從下載快取儲存安裝檔案和資訊清單的磁碟機。

        例如，如果您選取 [使用 C++ 的桌面開發] 工作負載，暫時會需要系統磁碟機上 1.58 GB 的大小，然後會在安裝完成時予以釋放。

       > [!IMPORTANT]
       > 此位置會在您第一次安裝時設定，而且之後無法從安裝程式 UI 變更。 相反地，您必須[使用命令列參數](use-command-line-parameters-to-install-visual-studio.md)來移動下載快取。

1. 請注意，[共用的元件、工具及 SDK] 區段中所使用磁碟機和您在 [下載快取] 區段中選擇的磁碟機一樣。 \Microsoft\VisualStudio\Shared 目錄是 Visual Studio 儲存並排顯示 Visual Studio 安裝共用檔案的位置。 SDK 和工具也會儲存在此目錄中。

::: moniker-end

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>另請參閱

* [安裝 Visual Studio](install-visual-studio.md)
* [更新 Visual Studio 2017](update-visual-studio.md)
* [修改 Visual Studio 2017](update-visual-studio.md)
* [解除安裝 Visual Studio](uninstall-visual-studio.md)
