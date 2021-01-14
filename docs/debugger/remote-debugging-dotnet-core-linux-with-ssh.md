---
title: 在 Linux 上對 .NET Core 偵錯
description: 藉由附加至進程，使用安全殼層 (SSH) 來在 Linux 上進行 .NET Core 的偵錯工具。 準備您的應用程式以進行偵錯工具。 建立並部署應用程式。 附加偵錯工具。
ms.custom: SEO-VS-2020
ms.date: 02/26/2020
ms.topic: conceptual
helpviewer_keywords:
- remote debugging, linux
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bde5bb8722e0f95a10991019bdc9cba9c8a48ec3
ms.sourcegitcommit: a436ba564717b992eb1984b28ea0aec801eacaec
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/14/2021
ms.locfileid: "98204887"
---
# <a name="debug-net-core-on-linux-using-ssh-by-attaching-to-a-process"></a>藉由附加至進程，使用 SSH 在 Linux 上進行 .NET Core 的偵錯工具

從 Visual Studio 2017 開始，您可以透過 SSH 附加至在本機或遠端 Linux 部署上執行的 .NET Core 進程。 本文說明如何設定偵測和如何進行調試。 如需使用 Docker 容器的偵錯工具案例，請參閱 [附加至在 docker 容器上](../debugger/attach-to-process-running-in-docker-container.md) 執行的進程。

## <a name="prerequisites"></a>先決條件

- 在 Visual Studio 電腦上，您必須安裝 **ASP.NET 和 網頁程式開發** 工作負載，或是 **.net Core 跨平臺開發** 工作負載。

- 在 Linux 伺服器上，您必須安裝 SSH 伺服器，並使用捲曲或 wget 進行解壓縮和安裝。 例如，在 Ubuntu 上，您可以執行下列動作來執行：

  ``` cmd
  sudo apt-get install openssh-server unzip curl
  ```

- 在 Linux 伺服器上，在 [linux 上安裝 .net 執行時間](/dotnet/core/install/linux)，並尋找符合您 Linux 散發套件的頁面 (例如 Ubuntu) 。 不需要 .NET SDK。

- 如需完整的 ASP.NET Core 指示，請參閱 linux 上 [使用 Nginx 的主機 ASP.NET Core](/aspnet/core/host-and-deploy/linux-nginx) 和 [使用 Apache 的 Linux 上的主機 ASP.NET Core](/aspnet/core/host-and-deploy/linux-apache)。

## <a name="prepare-your-application-for-debugging"></a>準備您的應用程式以進行偵錯工具

若要準備您的應用程式以進行偵錯工具：

- 當您建立應用程式時，請考慮使用 Debug 設定。 將零售編譯的程式碼與偵錯工具編譯的程式碼)  (，比起偵錯工具的程式碼更難。 如果您需要使用發行設定，請先停用 Just My Code。 若要停用此設定，請選擇 [**工具**  >  **選項**  >  **調試**]，然後取消選取 [**啟用 Just My Code**]。

- 確定您的專案已設定為產生 [可移植 pdb](https://github.com/OmniSharp/omnisharp-vscode/wiki/Portable-PDBs) (這是) 的預設設定，並確定 PDB 與 DLL 位於相同的位置。 若要在 Visual Studio 中進行這項設定，請在專案上按一下滑鼠右鍵，然後選擇 [**屬性**  >  **組建**  >  **Advanced** 錯]  >  **資訊**。

## <a name="build-and-deploy-the-application"></a>建置並部署應用程式

您可以使用數種方法來部署應用程式，然後再進行偵錯工具。 例如，您可以：

- 將來源複製到目的電腦，並 ```dotnet build``` 在 Linux 電腦上建立。

- 在 Windows 上建立應用程式，然後將組建構件傳送至 Linux 電腦。  (組建成品是由應用程式本身、可移植 Pdb、任何可能相依的執行時間程式庫，以及檔案 *上的.deps.js* 所組成。 ) 

部署應用程式之後，請啟動應用程式。

## <a name="attach-the-debugger"></a>附加偵錯工具

當應用程式在 Linux 機器上執行時，您就可以準備附加偵錯工具。

1. 在 Visual Studio 中，選擇 [ **Debug**  >  **附加至進程 ...**]。

1. 在 [ **連線類型** ] 清單中，選取 [ **SSH**]。

1. 將 **連接目標** 變更為目的電腦的 IP 位址或主機名稱。

   如果您尚未提供認證，系統會提示您輸入密碼和/或私密金鑰檔案。

   除了執行 SSH 伺服器的埠之外，沒有任何埠需求需要進行設定。

1. 尋找您想要進行偵錯工具的進程。

   您的程式碼會在唯一進程名稱或名為 dotnet 的進程中執行。 若要尋找您感興趣的進程，請檢查 [ **標題** ] 資料行，其中會顯示進程的命令列引數。

   在下列範例中，您會在 [ **附加至進程** ] 對話方塊中顯示的 SSH 傳輸上，看到來自遠端 Linux 電腦的進程清單。

   ![附加至 Linux 進程](media/remote-debug-linux-over-ssh-attach.png)

1. 選擇 [ **附加**]。

1. 在出現的對話方塊中，選取您要進行偵錯工具的程式碼類型。 選擇 **受控 ( .Net Core For Unix)**。

1. 使用 Visual Studio 偵錯工具功能來對應用程式進行偵錯工具。

   在下列範例中，您會在遠端 Linux 電腦上執行的程式碼中看到 Visual Studio 偵錯工具在中斷點上停止。

   ![叫用中斷點](media/remote-debug-linux-over-ssh-hit-breakpoint.png)