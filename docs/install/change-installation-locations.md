---
title: 變更 Visual Studio 2017 中的安裝位置
description: 了解如何將下載快取、共用元件、SDK 和工具的位置變更為不同的磁碟機，來減少系統磁碟機上的安裝使用量。
ms.date: 05/07/2018
ms.technology: vs-acquisition
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- change installation locations for Visual Studio
- move installation files to different drives
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 87698421c4992d0349e04740c120d491aa54fcc3
ms.sourcegitcommit: 6b092e7d466377f06913d49d183dbbdca16730f0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/28/2018
ms.locfileid: "43138962"
---
# <a name="change-the-installation-locations-in-visual-studio-2017"></a>變更 Visual Studio 2017 中的安裝位置

**15.7 的新功能**：您可以將下載快取、共用元件、SDK 和工具移至不同的磁碟機，來減少系統磁碟機上的安裝使用量。

方式如下：

1. 當您安裝 Visual Studio 時，選擇 [安裝選項] 索引標籤。

  ![Visual Studio 2017 - 變更安裝位置](media/installation-options-by-location.png "變更安裝位置")

  > [!IMPORTANT]
  > 如果您暫停安裝並於稍後繼續，Visual Studio 會從停止的地方繼續。 換句話說，其安裝進度會以剩餘的下載項目與安裝項目為基準，而不會從上一個計數開始。

2. 在 [Visual Studio IDE] 區段中，接受預設。 這會安裝核心產品，並包含本版 Visual Studio 的特定檔案。

 > [!IMPORTANT]
 > 如果您的系統磁碟機是固態硬碟 (SSD)，以下是我們建議您接受系統磁碟機上預設位置的原因：當您使用 Visual Studio 開發時，您會讀取並寫入大量檔案，而增加磁碟 I/O 活動。  最好選擇最快的磁碟機來處理負載。

2. 在 [下載快取] 區段中，決定是否要保留下載快取，然後據以核取或取消核取 [Keep download cache] \(保留下載快取\)。 <br><br>如果您決定不要保留下載快取，則只會暫時使用此位置。 此外，此動作不會影響或刪除先前安裝的檔案。 (若要清除所有安裝套件，您必須另外修改先前的安裝)。

3. 在 [下載快取] 區段中，指定您要儲存安裝檔案和資訊清單的磁碟機。 <br><br>例如，如果您選取 [使用 C++ 的桌面開發] 工作負載，暫時會需要系統磁碟機上 1.58 GB 的大小，然後會在安裝完成時予以釋放。

 > [!NOTE]
 > 檔案會先下載到您系統磁碟機上的暫存資料夾，並在 Visual Studio 確認並將其移至下載快取資料夾之後予以刪除。 如果您選取將下載快取保留到不同的磁碟機，Visual Studio 仍然需要相當於系統磁碟機上下載快取大小的磁碟空間。
 > [!IMPORTANT]
 > 此位置會在您第一次安裝時設定，而且之後無法從安裝程式 UI 變更。 相反地，您必須[使用命令列參數](use-command-line-parameters-to-install-visual-studio.md)來移動下載快取

4. 在 [Shared components, tools, and SDKs] \(共用元件、工具 和 SDK\) 區段中，指定您要儲存檔案以供並存 Visual Studio 安裝共用的磁碟機。 讓 Visual Studio 安裝程式變更其安裝位置的 SDK 和工具也會儲存在此目錄中。

 > [!NOTE]
 > 某些工具和 SDK 對於可安裝的位置有不同的規則。 這些工具和 SDK 仍然會安裝在您的系統磁碟機上，即使您選擇其他位置也一樣。

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>另請參閱

* [安裝 Visual Studio 2017](install-visual-studio.md)
* [更新 Visual Studio 2017](update-visual-studio.md)
* [修改 Visual Studio 2017](update-visual-studio.md)
* [解除安裝 Visual Studio 2017](uninstall-visual-studio.md)
