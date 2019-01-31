---
title: 選取安裝位置
description: 了解如何將下載快取、共用元件、SDK 和工具的位置變更為不同的磁碟機，來減少 Visual Studio 在系統磁碟機上的安裝磁碟使用量。
ms.date: 11/07/2018
ms.custom: seodec18
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- change installation locations for Visual Studio
- select an installation location for Visual Studio files
- move installation files to different drives
- use the D drive
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 522b27093c97101df66aca2e5b4d969bcdaa3bc5
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "55003221"
---
# <a name="select-the-installation-locations-in-visual-studio-2017"></a>在 Visual Studio 2017 中選取安裝位置

**15.7 中的新功能**：您可以變更某些檔案的位置，來減少 Visual Studio 在系統磁碟機上的安裝磁碟使用量。 具體而言，您可以針對下載快取、共用元件、SDK 和工具檔案使用不同的位置。

   > [!NOTE]
   > 某些工具和 SDK 對於可安裝的位置有不同的規則。 這類工具和 SDK 會安裝在您的系統磁碟機上，即使您選擇其他位置也一樣。

準備好開始著手了嗎？ 方式如下：

1. 當您安裝 Visual Studio 時，選擇 [安裝位置] 索引標籤。

   ![Visual Studio 2017 - 選取安裝位置](media/vs-installation-locations.png "選取安裝位置。")

1. 在 [Visual Studio IDE] 區段中，接受預設。 Visual Studio 會安裝核心產品，並包含本版 Visual Studio 的特定檔案。

   ![[安裝位置] 索引標籤的 [Visual Studio IDE] 區段](media/vs-installation-locations-ide.png "接受 [安裝位置] 索引標籤中 [Visual Studio IDE] 區段的預設值。")

   > [!TIP]
   > 如果您的系統磁碟機是固態硬碟 (SSD)，建議您接受系統磁碟機上的預設位置。 理由何在？ 當您使用 Visual Studio 開發時，您會讀取並寫入大量檔案，其會增加磁碟 I/O 活動。 最好選擇最快的磁碟機來處理負載。

1. 在 [下載快取] 區段中，決定是否要保留下載快取，然後決定要儲存其檔案的位置。

     ![[安裝位置] 索引標籤的 [下載快取] 區段](media/vs-installation-locations-cache.png "選擇是否要在安裝後保留下載快取，然後指定要儲存檔案的磁碟機。")

    1. 核取或取消核取 [在安裝後保留下載快取]。

       如果您決定不要保留下載快取，則只會暫時使用此位置。 此動作不會影響或刪除先前安裝的檔案。

    1. 指定您要從下載快取儲存安裝檔案和資訊清單的磁碟機。

        例如，如果您選取 [使用 C++ 的桌面開發] 工作負載，暫時會需要系統磁碟機上 1.58 GB 的大小，然後會在安裝完成時予以釋放。

       > [!IMPORTANT]
       > 此位置會在您第一次安裝時設定，而且之後無法從安裝程式 UI 變更。 相反地，您必須[使用命令列參數](use-command-line-parameters-to-install-visual-studio.md)來移動下載快取。

1. 在 [共用的元件、工具及 SDK] 區段中，指定您要儲存檔案以供並存 Visual Studio 安裝共用的磁碟機。 SDK 和工具也會儲存在此目錄中。

   ![[安裝位置] 索引標籤的 [共用的元件、工具及 SDK] 區段](media/vs-installation-locations-shared.png "指定您要儲存共用元件、工具和 SDK 的位置。")

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>另請參閱

* [安裝 Visual Studio 2017](install-visual-studio.md)
* [更新 Visual Studio 2017](update-visual-studio.md)
* [修改 Visual Studio 2017](update-visual-studio.md)
* [解除安裝 Visual Studio 2017](uninstall-visual-studio.md)
