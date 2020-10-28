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
ms.openlocfilehash: 2d66181f5e6720348e18c34b735ef29e24c0111a
ms.sourcegitcommit: bd9417123c6ef67aa2215307ba5eeec511e43e02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/28/2020
ms.locfileid: "92796299"
---
# <a name="remote-debug-net-core-on-linux-using-ssh"></a>使用 SSH 在 Linux 上遠端偵錯 .NET Core

從 Visual Studio 2017 開始，您可以透過 SSH 連接到在 Linux 上執行的 .NET Core 進程。 本文說明如何設定偵測和如何進行調試。

## <a name="prerequisites"></a>必要條件

在 Visual Studio 電腦上，您必須安裝 **ASP.NET 和 網頁程式開發** 工作負載，或是 **.net Core 跨平臺開發** 工作負載。

在 Linux 伺服器上，您必須安裝 SSH 伺服器，並使用捲曲或 wget 進行解壓縮和安裝。 例如，在 Ubuntu 上，您可以執行下列動作來執行：

``` cmd
sudo apt-get install openssh-server unzip curl
```

## <a name="build-and-deploy-the-application"></a>建置並部署應用程式

若要準備您的應用程式以進行偵錯工具：

- 當您建立應用程式時，請考慮使用 Debug 設定。 將零售編譯的程式碼與偵錯工具編譯的程式碼)  (，比起偵錯工具的程式碼更難。 如果您需要使用發行設定，請先停用 Just My Code。 若要停用此設定，請選擇 [ **工具**  >  **選項**  >  **調試** ]，然後取消選取 [ **啟用 Just My Code** ]。

- 確定您的專案已設定為產生預設設定) 的 [便攜 pdb](https://github.com/OmniSharp/omnisharp-vscode/wiki/Portable-PDBs) (，並確定 pbd 位於與 DLL 相同的位置。 若要在 Visual Studio 中進行這項設定，請在專案上按一下滑鼠右鍵，然後選擇 [ **屬性**  >  **組建**  >  **Advanced** 錯]  >  **資訊** 。

您可以使用數種方法來部署應用程式，然後再進行偵錯工具。 例如，您可以：

- 將來源複製到目的電腦，並 ```dotnet build``` 在 Linux 電腦上建立。

- 在 Windows 上建立應用程式，然後將組建構件傳送至 Linux 電腦。  (組建成品是由應用程式本身、它可能依存的任何執行時間程式庫，以及檔案 *上的.deps.js* 所組成。 ) 

## <a name="attach-the-debugger"></a>附加偵錯工具

設定好電腦之後，請在 Linux 機器上啟動應用程式，然後您就可以附加偵錯工具。

1. 在 Visual Studio 中，選擇 [ **Debug**  >  **附加至進程 ...** ]。

1. 在 [ **連線類型** ] 清單中，選取 [ **SSH** ]。

1. 將 **連接目標** 變更為目的電腦的 IP 位址或主機名稱。

1. 尋找您想要進行偵錯工具的進程。

   您的程式碼會在唯一進程名稱或名為 dotnet 的進程中執行。 若要尋找您感興趣的進程，請檢查 [ **標題** ] 資料行，其中會顯示進程的命令列引數。

   在下列範例中，您會在 [ **附加至進程** ] 對話方塊中顯示的 SSH 傳輸上，看到來自遠端 Linux 電腦的進程清單。

   ![附加至 Linux 進程](media/remote-debug-linux-over-ssh-attach.png)

1. 選擇 [ **附加** ]。

1. 在出現的對話方塊中，選取您要進行偵錯工具的程式碼類型。 選擇 **受控 ( .Net Core For Unix)** 。

1. 使用 Visual Studio 偵錯工具功能來對應用程式進行偵錯工具。

   在下列範例中，您會在遠端 Linux 電腦上執行的程式碼中看到 Visual Studio 偵錯工具在中斷點上停止。

   ![叫用中斷點](media/remote-debug-linux-over-ssh-hit-breakpoint.png)