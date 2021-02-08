---
title: Docker 教學課程-第2部分：更新您的應用程式
description: 說明如何更新 Docker 應用程式。
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jmartens
ms.technology: vs-azure
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: df2102c38250aa5c1bda52b4324cba808501db3a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99841740"
---
# <a name="update-the-app"></a>更新應用程式

當您沒有任何 todo 清單專案時，產品小組會要求您變更「空白文字」，這是小型的功能要求。 他們想要將它轉換成下列內容：

> 您還沒有 todo 專案！ 新增上述各項！

相當簡單，對吧？ 讓我們進行變更。

## <a name="update-the-source-code"></a>更新原始程式碼

1. 在檔案中 `src/static/js/app.js` ，更新行56以使用新的空文字。

    ```diff
    -                <p className="text-center">No items yet! Add one above!</p>
    +                <p className="text-center">You have no todo items yet! Add one above!</p>
    ```

1. 使用您先前使用的相同命令，建立映射的更新版本。

    ```bash
    docker build -t getting-started .
    ```

1. 使用更新的程式碼啟動新的容器。

    ```bash
    docker run -dp 3000:3000 getting-started
    ```

**喔！** 您可能會看到類似下面的錯誤 (識別碼將會不同) ：

```bash
docker: Error response from daemon: driver failed programming external connectivity on endpoint laughing_burnell 
(bb242b2ca4d67eba76e79474fb36bb5125708ebdabd7f45c8eaf16caaabde9dd): Bind for 0.0.0.0:3000 failed: port is already allocated.
```

那麼，發生了什麼事呢？ 因為您的舊容器仍在執行中，所以無法啟動新的容器。 這是問題的原因，是因為容器正在使用主機的埠3000，而電腦上只有一個進程 (容器包含) 可以接聽特定埠。 若要修正此問題，請移除舊的容器。

## <a name="replace-the-old-container"></a>取代舊的容器

若要移除容器，必須先將它停止。 一旦停止之後，就可以將它移除。 您有兩種方式可以移除舊的容器。 請隨意選擇您最熟悉的路徑。

### <a name="remove-a-container-using-the-cli"></a>使用 CLI 移除容器

1. 使用命令取得容器的識別碼 `docker ps` 。

    ```bash
    docker ps
    ```

1. 使用 `docker stop` 命令來停止容器。

    ```bash
    # Swap out <the-container-id> with the ID from docker ps
    docker stop <the-container-id>
    ```

1. 容器停止後，您可以使用命令將其移除 `docker rm` 。

    ```bash
    docker rm <the-container-id>
    ```

> [!TIP]
> 您可以在命令中新增「強制」旗標，以在單一命令中停止和移除容器 `docker rm` 。 例如：`docker rm -f <the-container-id>`

### <a name="remove-a-container-using-the-docker-view"></a>使用 Docker view 移除容器

如果您開啟 VS Code 擴充功能，只要按兩下滑鼠就可以移除容器！ 這當然比查詢容器識別碼和移除容器識別碼來得簡單得多。

1. 開啟擴充功能後，流覽至容器，然後按一下滑鼠右鍵。

1. 按一下 [ **移除** ] 選項。

1. 確認移除完成後，您就完成了！

![Docker view-移除容器](media/vs-removing-container.png)

### <a name="start-the-updated-app-container"></a>啟動已更新的應用程式容器

1. 現在，啟動已更新的應用程式。

    ```bash
    docker run -dp 3000:3000 getting-started
    ```

1. 重新整理您的瀏覽器 [http://localhost:3000](http://localhost:3000) ，您應該會看到已更新的解說文字！

![更新的應用程式已更新空白文字](media/todo-list-updated-empty-text.png)

## <a name="recap"></a>概括回顧

雖然您可以建立更新，但您可能已經注意到兩件事：

- Todo 清單中的所有現有專案都已消失！ 這並不是很好的應用程式！ 我們很快就會討論到。
- 這項小變更牽涉到 *許多* 步驟。 在下一節中，您將瞭解如何在每次進行變更時，查看程式碼更新，而不需要重建和啟動新的容器。

在瞭解持續性之前，您將快速瞭解如何與其他人共用這些映射。

## <a name="next-steps"></a>下一步

繼續進行本教學課程！

> [!div class="nextstepaction"]
> [共用您的應用程式](share-your-app.md)
