---
title: 教學課程：開始使用 Docker & Visual Studio Code
description: 本教學課程涵蓋使用 Docker 搭配 Visual Studio Code 的基本概念。
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jmartens
ms.topic: tutorial
ms.workload:
- azure
next_page: app.md
ms.openlocfilehash: 75a51f478e4e58700f6025dd6a87fcc38439ed87
ms.sourcegitcommit: 8b75524dc544e34d09ef428c3ebbc9b09f14982d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2021
ms.locfileid: "113222652"
---
# <a name="tutorial-get-started-with-docker"></a>教學課程：開始使用 Docker

在本教學課程中，您將瞭解如何建立和部署 Docker 應用程式，包括搭配資料庫使用多個容器，以及使用 Docker Compose。 您也會將容器化應用程式部署到 Azure。

## <a name="start-the-tutorial"></a>開始教學課程

如果您已經執行此命令來開始進行教學課程，恭喜您！  如果沒有，請開啟命令提示字元或 bash 視窗，然後執行下列命令：

```cli
docker run -d -p 80:80 docker/getting-started
```

您會發現有幾個旗標正在使用。 以下是一些詳細資訊：

- `-d` -在背景中以卸離模式執行容器 () 
- `-p 80:80` -將主機的埠80對應至容器中的埠80
- `docker/getting-started` -要使用的映射

> [!TIP]
> 您可以結合單一字元旗標來縮短完整的命令。
> 例如，上述命令可以撰寫為：
>
> ```cli
> docker run -dp 80:80 docker/getting-started
> ```

## <a name="the-vs-code-extension"></a>VS Code 擴充功能

在走到太遠之前，我們想要強調 Docker VS Code 擴充功能，讓您快速瞭解在電腦上執行的容器。 它可讓您快速存取容器記錄，讓您可以在容器內取得 shell，並讓您輕鬆管理容器生命週期 (停止、移除等) 。

若要存取擴充功能，請遵循 [此處](https://code.visualstudio.com/docs/containers/overview)的指示。 使用左側的 Docker 圖示來開啟 Docker view。 如果您現在開啟延伸模組，您將會看到此教學課程正在執行！ ) 下的容器名稱 (`angry_taussig` 是隨機建立的名稱。 因此，您可能會有不同的名稱。

![在 Docker 擴充功能中執行的教學課程容器](media/vs-tutorial-in-extension.png)

## <a name="what-is-a-container"></a>什麼是容器

現在您已執行容器，什麼 *是* 容器？ 簡單來說，容器只是電腦上的另一個程式，與主機電腦上的所有其他進程隔離。 該隔離會利用 [核心命名空間和 cgroups](https://medium.com/@saschagrunert/demystifying-containers-part-i-kernel-space-2c53d6979504)，在 Linux 中已有很長一段時間的功能。 Docker 已經努力讓這些功能平易近人且容易使用。

> [!NOTE]
> **從頭開始建立容器** 如果您想要瞭解如何從頭開始建立容器，從青色安全性 Liz Rice 有一段影片，讓她從頭開始建立容器：
>
> [!VIDEO https://www.youtube-nocookie.com/embed/8fi7uSYlOdc]

## <a name="what-is-a-container-image"></a>什麼是容器映射

執行容器時，它會使用隔離檔案系統。 此自訂檔案系統是由 **容器映射** 提供。 因為映射包含容器的檔案系統，所以它必須包含執行應用程式所需的所有專案，包括所有相依性、設定、腳本、二進位檔等等。 映射也包含容器的其他設定，例如環境變數、要執行的預設命令，以及其他中繼資料。

我們稍後會深入探討影像，其中涵蓋了分層、最佳作法等主題。

> [!NOTE]
> 如果您很熟悉 `chroot` ，請將容器視為的擴充版本 `chroot` 。 檔案系統只是來自映射。 但是，當您只使用 chroot 時，容器會新增額外的隔離。

## <a name="next-steps"></a>下一步

繼續進行本教學課程！

> [!div class="nextstepaction"]
> [應用程式](your-application.md)
