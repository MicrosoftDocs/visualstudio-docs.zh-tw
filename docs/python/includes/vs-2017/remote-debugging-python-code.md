---
title: 對遠端 Linux 電腦上的 Python 程式碼進行偵錯
description: 使用 Visual Studio 對在遠端 Linux 電腦上執行的 Python 程式碼進行偵錯，包括必要的組態步驟、安全性和疑難排解。
ms.date: 12/06/2018
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: a58af8098a49992e81380c6567755c31709d1dc3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99916614"
---
Visual Studio 可以在 Windows 電腦本機和遠端啟動 Python 應用程式並進行偵錯工具 (查看 [遠端偵錯](../../../debugger/remote-debugging.md)) 。 它也可在其他作業系統、裝置或使用 [ptvsd 程式庫](https://pypi.python.org/pypi/ptvsd)的 Python 實作 (不同於 CPython) 上進行遠端偵錯。

使用 ptvsd 時，進行偵錯的 Python 程式碼會裝載 Visual Studio 可以附加到的偵錯伺服器。 這項裝載需要稍微修改您的程式碼以匯入和啟用伺服器，並可能需要遠端電腦上的網路或防火牆組態允許 TCP 連線。

![影片的電影攝影機圖示](../../../install/media/video-icon.png "觀看影片") 如需遠端偵錯程式的簡介，請參閱 [深入探討：跨平臺遠端偵錯](https://youtu.be/y1Qq7BrV6Cc) 程式 (youtube.com，6m22s) ，適用于 Visual Studio 2015 和2017。

## <a name="set-up-a-linux-computer"></a>設定 Linux 電腦

若要遵循本逐步解說，需要下列項目：

- 執行 Python 的遠端電腦，作業系統為 Mac OS 或 Linux。
- 已開啟上述電腦的防火牆連接埠 5678 (輸入)，其為遠端偵錯的預設值。

您可以輕鬆地建立 [Azure 上的 Linux 虛擬機器](/azure/virtual-machines/linux/creation-choices)，並透過 Windows [使用遠端桌面進行存取](/azure/virtual-machines/linux/use-remote-desktop)。 適用於 VM 的 Ubuntu 預設會安裝 Python，因此是很方便的選項；否則，請參閱[安裝您所選的 Python 解譯器](../../installing-python-interpreters.md)上的清單，以取得其他的 Python 下載位置。

如需建立 Azure VM 防火牆規則的詳細資訊，請參閱[使用 Azure 入口網站對 Azure 中的 VM 開啟連接埠](/azure/virtual-machines/windows/nsg-quickstart-portal)。

## <a name="prepare-the-script-for-debugging"></a>準備偵錯指令碼

1. 在遠端電腦上，使用下列程式碼建立稱為 *guessing-game.py* 的 Python 檔案：

    ```python
    import random

    guesses_made = 0
    name = input('Hello! What is your name?\n')
    number = random.randint(1, 20)
    print('Well, {0}, I am thinking of a number between 1 and 20.'.format(name))

    while guesses_made < 6:
        guess = int(input('Take a guess: '))
        guesses_made += 1
        if guess < number:
            print('Your guess is too low.')
        if guess > number:
            print('Your guess is too high.')
        if guess == number:
            break
    if guess == number:
        print('Good job, {0}! You guessed my number in {1} guesses!'.format(name, guesses_made))
    else:
        print('Nope. The number I was thinking of was {0}'.format(number))
    ```

1. 使用 `pip3 install ptvsd`，將 `ptvsd` 封裝安裝到您的環境。
   >[!NOTE]
   >建議您將 ptvsd 的安裝版本記錄起來，以免需要進行疑難排解；[ptvsd 清單](https://pypi.python.org/pypi/ptvsd)中也會顯示可用的版本。

1. 盡早在 *guessing-game.py* 中的其他程式碼之前加入下列程式碼，以啟用遠端偵錯。 (雖然不是嚴格要求，但在呼叫 `enable_attach` 函式前，無法對繁衍 (Spawn) 的任何背景執行緒進行偵錯。)

   ```python
   import ptvsd
   ptvsd.enable_attach()
   ```

1. 請儲存檔案，然後執行 `python3 guessing-game.py`。 `enable_attach` 的呼叫會在背景執行，並等待您與程式互動時的連入連線。 如有需要，可以在 `enable_attach` 之後呼叫 `wait_for_attach` 函式來封鎖程式，直到偵錯工具附加為止。

> [!Tip]
> 除了 `enable_attach` 和`wait_for_attach` 以外，ptvsd 也提供協助程式函式 `break_into_debugger`，其在偵錯工具附加時可做為程式設計的中斷點。 還有一個 `is_attached` 函式會在偵錯工具附加時傳回 `True` (請注意，在呼叫其他 `ptvsd` 之前，不需檢查這個結果)。

## <a name="attach-remotely-from-python-tools"></a>從 Python 工具遠端附加

在這些步驟中，我們會設定中斷點以停止遠端程序。

1. 在本機電腦上建立遠端檔案的複本，然後在 Visual Studio 中開啟它。 檔案所在位置並不重要，但其名稱應符合遠端電腦上的指令碼名稱。

1. (選擇性) 若要讓本機電腦具有適用於 ptvsd 的 IntelliSense，請將 ptvsd 套件安裝到您的 Python 環境中。

1. 選取 [ **Debug**  >  **附加至進程**]。

1. 在隨即顯示的 [附加至處理序] 對話方塊中，將 [連線類型] 設為 [Python remote (ptvsd)] (Python 遠端 (ptvsd)) (在舊版 Visual Studio 中，這些命令名稱為 [傳輸] 和 [Python 遠端偵錯])。

1. 在 [連線目標] 欄位 (舊版為 [限定詞]) 中，輸入 `tcp://<ip_address>:5678`，其中 `<ip_address>` 是遠端電腦的明確位址或名稱 (如 myvm.cloudapp.net)，而 `:5678` 是遠端偵錯的連接埠號碼。

1. 按 **enter** 鍵，以填入該電腦上可用的 ptvsd 進程清單：

    ![輸入連線目標，並列出處理序](../../media/remote-debugging-qualifier.png)

    填入此清單之後，如果您剛好在遠端電腦上啟動另一個程式，請選取 [重新整理] 按鈕。

1. 選取要偵錯的處理序，再選取 [附加]，或按兩下處理序。

1. Visual Studio 即會切換至偵錯模式，而遠端電腦仍會繼續執行指令碼，並提供所有一般[偵錯](../../debugging-python-in-visual-studio.md)功能。 例如，在 `if guess < number:` 行上設定中斷點，然後切換到遠端電腦，並輸入另一種猜測。 進行上述作業之後，本機電腦的 Visual Studio 會在該中斷點停駐，並顯示本機變數等等：

    ![Visual Studio 會在到達中斷點時暫停偵錯](../../media/remote-debugging-breakpoint-hit.png)

1. 當您停止偵錯時，Visual Studio 會中斷連結程式，而遠端電腦仍會繼續執行該程式。 ptvsd 也會繼續接聽以便附加偵錯工具，因此您可以隨時將其重新附加至處理序。

### <a name="connection-troubleshooting"></a>連線疑難排解

1. 請確定您已針對 [連線類型] 選取 [Python remote (ptvsd)]\(Python 遠端 (ptvsd)) (舊版則選取 [傳輸] 的 [Python 遠端偵錯])。
1. 請檢查 [連線目標]\(或 [限定詞]) 中的密碼是否完全符合遠端程式碼中的密碼。
1. 請檢查 [連線目標] (或 [限定詞]) 中的 IP 位址是否完全符合遠端程式碼中的 IP 位址。
1. 請檢查遠端電腦上是否已開啟遠端偵錯連接埠，以及連接埠尾碼中是否包含連線目標，例如 `:5678`。
    - 如果您需要使用不同的連接埠，可以在 `enable_attach` 呼叫中使用 `address` 引數進行指定，如同在 `ptvsd.enable_attach(address = ('0.0.0.0', 8080))` 中一樣。 在此情況下，請開啟防火牆中的特定連接埠。
1. 請檢查 `pip3 list` 所傳回的遠端電腦 ptvsd 安裝版本，是否符合您在 Visual Studio 中使用的 Python 工具版本 (如下表所示)。 如果有必要，請更新遠端電腦上的 ptvsd。

    | Visual Studio 版本 | Python 工具/ptvsd 版本 |
    | --- | --- |
    | 2017 15.8 | 4.1.1a9 (舊版偵錯工具：3.2.1.0) |
    | 2017 15.7 | 4.1.1a1 (舊版偵錯工具：3.2.1.0) |
    | 2017 15.4, 15.5, 15.6 | 3.2.1.0 |
    | 2017 15.3 | 3.2.0 |
    | 2017 15.2 | 3.1.0 |
    | 2017 15.0, 15.1 | 3.0.0 |
    | 2015 | 2.2.6 |
    | 2013 | 2.2.2 |
    | 2012, 2010 | 2.1 |

## <a name="using-ptvsd-3x"></a>使用 ptvsd 3.x

下列資訊僅適用於使用 ptvsd 3.x 進行遠端偵錯，其中包含 ptvsd 4.x 中已移除某些功能。

1. 使用 ptvsd 3.x 時，`enable_attach` 函式會要求您傳遞 "secret"，作為限制存取執行中指令碼的第一個引數。 連結遠端偵錯工具時，您可以輸入此密碼。 您也可以使用 `enable_attach(secret=None)`，允許任何人連線，但並不建議這麼做。

1. 連線目標 URL 為 `tcp://<secret>@<ip_address>:5678`，其中 `<secret>` 是將 `enable_attach` 傳入 Python 程式碼中的字串。

根據預設，與 ptvsd 3.x 遠端偵錯伺服器的連線只有受到密碼的保護，並會以純文字傳遞所有的資料。 如需更安全的連線，ptvsd 3.x 支援使用 `tcsp` 通訊協定的 SSL，您可依下列方式設定︰

1. 在遠端電腦上，使用 openssl 來產生個別的自我簽署憑證和金鑰檔案：

    ```command
    openssl req -new -x509 -days 365 -nodes -out cert.cer -keyout cert.key
    ```

    當 openssl 出現提示時，請依據您用以連接的項目，在 [一般名稱] 中使用主機名稱或 IP 位址 

    (如需詳細資訊，請參閱 Python `ssl` 模組文件中的 [Self-signed certificates](https://docs.python.org/3/library/ssl.html#self-signed-certificates) (自我簽署的憑證)。 請注意，這些文件中的命令只會產生單一合併檔案)。

1. 在程式碼中，使用檔名作為值，將 `enable_attach` 的呼叫修改為包含 `certfile` 和 `keyfile` 引數 (這些引數與標準 `ssl.wrap_socket` Python 函式具有相同的意義)：

    ```python
    ptvsd.enable_attach(secret='my_secret', certfile='cert.cer', keyfile='cert.key')
    ```

    您也可以在本機電腦上的程式碼檔案進行相同變更，但這個程式碼並不會實際執行，因為不是絕對必要。

1. 重新啟動遠端電腦上的 Python 程式，使其準備好開始偵錯。

1. 將憑證新增至安裝 Visual Studio 之 Windows 電腦上的受信任根 CA，以確保通道安全：

    1. 將遠端電腦的憑證檔案複製到本機電腦。
    1. 開啟 [控制台] 並巡覽至 [系統管理工具] > [管理電腦憑證]。
    1. 在出現的視窗中，展開左側的 [受信任的根憑證授權單位]，以滑鼠右鍵按一下 [憑證]，然後選取 [所有工作] > [匯入]。
    1. 巡覽至並選取從遠端電腦複製的 *.cer* 檔案，然後按一下所有對話方塊以完成匯入。

1. 現在，將 `tcps://` 作為 [連線目標]\(或 [限定詞]) 的通訊協定，以在 Visual Studio 中重複附加程序，如先前所述。

    ![選擇使用 SSL 進行遠端偵錯傳輸](../../media/remote-debugging-qualifier-ssl.png)

1. 透過 SSL 連線時，Visual Studio 會提示您潛在的憑證問題。 您可以略過警告並繼續進行，但即使通道仍會加密以防竊聽，依然可能受到攔截式攻擊。

    1. 如果您看到下面的 [ **遠端憑證不受信任** ] 警告，表示您未正確將憑證新增至受信任的根 CA。 檢查這些步驟，並再試一次。

        ![受信任的 SSL 憑證警告](../../media/remote-debugging-ssl-warning.png)

    1. 如果您看到 **遠端憑證名稱與下方的主機名稱** 警告不符，這表示您在建立憑證時，未使用適當的主機名稱或 IP 位址作為 **一般名稱** 。

        ![SSL 憑證主機名稱警告](../../media/remote-debugging-ssl-warning2.png)
