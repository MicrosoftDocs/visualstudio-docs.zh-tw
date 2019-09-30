---
title: 在本機 Docker 容器中偵錯工具 |Microsoft Docs
description: 瞭解如何修改在本機 Docker 容器中執行的應用程式、透過 [編輯] 和 [重新整理] 重新整理容器，然後設定 [偵錯工具中斷點]。
ms.author: ghogen
author: ghogen
manager: jillfra
ms.assetid: 480e3062-aae7-48ef-9701-e4f9ea041382
ms.topic: conceptual
ms.workload: multiple
ms.date: 07/25/2019
ms.technology: vs-azure
ms.openlocfilehash: 5af092bbcb987f45b10121f37d40eaa5466c3da5
ms.sourcegitcommit: 2db01751deeee7b2bdb1db25419ea6706e6fcdf8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71062179"
---
# <a name="debug-apps-in-a-local-docker-container"></a>在本機 Docker 容器中的偵錯工具

Visual Studio 提供一致的方式，在 Docker 容器中進行開發，並在本機驗證您的應用程式。 您不需要在每次進行程式碼變更時重新開機容器。

本文說明如何使用 Visual Studio 在本機 Docker 容器中啟動 ASP.NET Core web 應用程式、進行變更，然後重新整理瀏覽器以查看變更。 本文也會示範如何針對容器化 ASP.NET Core web 應用程式和 .NET Framework 主控台應用程式，設定中斷點以進行偵錯工具。

## <a name="prerequisites"></a>必要條件

若要在本機 Docker 容器中偵錯工具，必須安裝下列工具：

::: moniker range="vs-2017"

* 已安裝 Web 開發工作負載的[Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)

::: moniker-end

::: moniker range="vs-2019"

* 已安裝 Web 開發工作負載的[Visual Studio 2019](https://visualstudio.microsoft.com/downloads)

::: moniker-end

若要在本機執行 Docker 容器，您必須擁有本機 Docker 用戶端。 您可以使用[Docker 工具箱](https://www.docker.com/products/docker-toolbox)，這需要停用 hyper-v。 您也可以使用[適用於 Windows 的 Docker](https://www.docker.com/get-docker)（使用 hyper-v），而且需要 Windows 10。 

Docker 容器適用于 .NET Framework 和 .NET Core 專案。 讓我們來看以下兩個範例。 首先，我們會查看 .NET Core web 應用程式。 然後，我們會查看 .NET Framework 的主控台應用程式。

## <a name="create-a-web-app"></a>建立 Web 應用程式

::: moniker range="vs-2017"
[!INCLUDE [create-aspnet5-app](../azure/includes/create-aspnet5-app.md)]
::: moniker-end
::: moniker range=">= vs-2019"
[!INCLUDE [create-aspnet5-app-2019](../azure/includes/vs-2019/create-aspnet5-app-2019.md)]
::: moniker-end

### <a name="edit-your-code-and-refresh"></a>編輯您的程式碼並重新整理

若要快速反復查看變更，您可以在容器中啟動應用程式。 然後，繼續進行變更，如同使用 IIS Express 一樣加以查看。

1. 將**解決方案**設定設為**Debug**。 然後，按下**Ctrl** + **F5**來建立您的 Docker 映射，並在本機執行。

    建立容器映射並在 Docker 容器中執行時，Visual Studio 會在預設瀏覽器中啟動 web 應用程式。

2. 移至 [*索引*] 頁面。 我們將在此頁面上進行變更。
3. 返回 Visual Studio，然後開啟*Index. cshtml*。
4. 將下列 HTML 內容新增至檔案結尾，然後儲存變更。

    ```html
    <h1>Hello from a Docker container!</h1>
    ```

5. 在 [輸出] 視窗中，當 .NET 組建完成時，您會看到下列幾行，切換回您的瀏覽器並重新整理頁面：

   ```output
   Now listening on: http://*:80
   Application started. Press Ctrl+C to shut down.
   ```

已套用您的變更！

### <a name="debug-with-breakpoints"></a>使用中斷點進行偵錯

變更通常需要進一步的檢查。 您可以使用 Visual Studio 的偵錯工具功能進行這項工作。

1. 在 Visual Studio 中，開啟*Index.cshtml.cs*。
2. 將`OnGet`方法的內容取代為下列程式碼：

   ```csharp
       ViewData["Message"] = "Your application description page from within a container";
   ```

3. 在程式程式碼的左邊，設定中斷點。
4. 若要開始進行調試，並叫用中斷點，請按 F5。
5. 切換至 Visual Studio 以查看中斷點。 檢查值。

   ![中斷點](media/edit-and-refresh/breakpoint.png)

## <a name="create-a-net-framework-console-app"></a>建立 .NET Framework 主控台應用程式

當您使用 .NET Framework 主控台應用程式專案時，不支援新增不含協調流程之 Docker 支援的選項。 您仍然可以使用下列程式，即使您只使用單一 Docker 專案也一樣。

1. 建立新的 .NET Framework 主控台應用程式專案。
1. 在方案總管中，以滑鼠右鍵按一下專案節點，然後選取 [**新增** > **容器協調流程支援**]。  在出現的對話方塊中，選取 [ **Docker Compose**]。 系統會將 Dockerfile 新增至您的專案，並加入具有相關聯支援檔案的 Docker Compose 專案。

### <a name="debug-with-breakpoints"></a>使用中斷點進行偵錯

1. 在方案總管中，開啟*Program.cs*。
2. 將`Main`方法的內容取代為下列程式碼：

   ```csharp
       System.Console.WriteLine("Hello, world!");
   ```

3. 在程式程式碼的左側設定中斷點。
4. 按 F5 開始進行調試，並叫用中斷點。
5. 切換至 Visual Studio 以查看中斷點並檢查值。

   ![中斷點](media/edit-and-refresh/breakpoint-console.png)

## <a name="container-reuse"></a>容器重複使用

在開發週期期間，Visual Studio 只會在您變更 Dockerfile 時，只重建您的容器映射和容器本身。 如果您未變更 Dockerfile，Visual Studio 會重複使用先前執行的容器。

如果您手動修改了您的容器，並想要使用全新的容器映射重新開機，請使用 Visual Studio 中的 [**組建** > ] [**清除**] 命令，然後以一般方式建立。

## <a name="troubleshoot"></a>疑難排解

瞭解如何針對[Docker 開發 Visual Studio 進行疑難排解](troubleshooting-docker-errors.md)。

## <a name="more-about-docker-with-visual-studio-windows-and-azure"></a>深入瞭解使用 Visual Studio、Windows 和 Azure 的 Docker

* 深入瞭解[使用 Visual Studio 的容器開發](/visualstudio/containers)。
* 若要建立和部署 Docker 容器，請參閱[Azure Pipelines 的 docker 整合](https://aka.ms/dockertoolsforvsts)。
* 如需 Windows Server 和 Nano Server 文章的索引，請參閱[windows 容器資訊](https://aka.ms/containers)。
* 瞭解[Azure Kubernetes Service](https://azure.microsoft.com/services/kubernetes-service/)並參閱[Azure Kubernetes Service 檔](/azure/aks)。
