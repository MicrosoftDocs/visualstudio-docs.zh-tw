---
title: Linux 上的遠端偵錯 .NET Core |Microsoft Docs
ms.date: 02/26/2020
ms.topic: conceptual
helpviewer_keywords:
- remote debugging, linux
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 23bc0fa990a79b1855ec382f42248a0f847c3c9c
ms.sourcegitcommit: 3d64bfb9bf85395357effe054db9a9afaa0be5ea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/29/2020
ms.locfileid: "78200920"
---
# <a name="remote-debug-net-core-on-linux-using-ssh"></a>Linux 上使用 SSH 的遠端偵錯 .NET Core

從 Visual Studio 2017 開始，您可以附加至透過 SSH 在 Linux 上執行的 .NET Core 進程。 本文說明如何設定調試和如何進行調試。

## <a name="prerequisites"></a>Prerequisites

在 Visual Studio 電腦上，您必須安裝**ASP.NET 和 網頁程式開發**工作負載或 **.net Core 跨平臺開發**工作負載。

在 Linux 伺服器上，您必須安裝 SSH 伺服器，並使用捲曲或 wget 進行解壓縮和安裝。 例如，在 Ubuntu 上，您可以執行下列動作來進行：

``` cmd
sudo apt-get install openssh-server unzip curl
```

## <a name="build-and-deploy-the-application"></a>建置並部署應用程式

若要準備您的應用程式以進行偵錯工具：

- 當您建立應用程式時，請考慮使用 Debug 設定。 比起經過編譯的程式碼，要比對零售編譯的程式碼（發行設定）困難很多。 如果您需要使用發行設定，請先停用 Just My Code。 若要停用此設定，請選擇 [**工具**] > **選項** > [**調試**]，然後取消選取 [**啟用 Just My Code**]。

- 請確定您的專案已設定為產生[便攜 pdb](https://github.com/OmniSharp/omnisharp-vscode/wiki/Portable-PDBs) （這是預設設定），並確定 PBD 與 DLL 位於相同的位置。 若要在 Visual Studio 中進行此設定，請以滑鼠右鍵按一下專案，然後選擇 [**屬性**] [ > **組建**] > [ **Advanced** > **調試資訊**]。

在進行偵錯工具之前，您可以使用數種方法來部署應用程式。 例如，您可以：

- 將來源複製到目的電腦，並使用 Linux 電腦上的 ```dotnet build``` 建立。

- 在 Windows 上建立應用程式，並將組建成品轉移至 Linux 電腦。 （組建成品包含應用程式本身、可能相依的任何執行時間程式庫，以及 *.deps.json json*檔案）。

## <a name="attach-the-debugger"></a>附加偵錯工具

設定電腦之後，請在 Linux 機器上啟動應用程式，然後您就可以開始附加偵錯工具。

1. 在 Visual Studio 中，選擇  **Debug**  > **附加至進程**...。

1. 在 [連線**類型**] 清單中，選取 [ **SSH**]。

1. 將 [**連接目標**] 變更為目的電腦的 IP 位址或主機名稱。

1. 尋找您要進行偵錯工具的進程。

   您的程式碼會在唯一的進程名稱或名為 dotnet 的進程中執行。 若要尋找您感興趣的處理常式，請檢查 [**標題**] 欄，其中會顯示進程的命令列引數。

   在下列範例中，您會在 [**附加至進程**] 對話方塊中顯示的 SSH 傳輸上，看到來自遠端 Linux 電腦的處理常式清單。

   ![附加至 Linux 進程](media/remote-debug-linux-over-ssh-attach.png)

1. 選擇 [ **附加**]。

1. 在出現的對話方塊中，選取您想要進行 debug 的程式碼類型。 選擇 [**受控] （適用于 Unix 的 .Net Core）** 。

1. 使用 Visual Studio 的偵錯工具功能來對應用程式進行 debug。

   在下列範例中，您會看到在遠端 Linux 電腦上執行的程式碼中，中斷點停止了 Visual Studio 偵錯工具。

   ![叫用中斷點](media/remote-debug-linux-over-ssh-hit-breakpoint.png)