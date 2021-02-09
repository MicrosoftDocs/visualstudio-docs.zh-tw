---
title: 對遠端 Linux 電腦上的 Python 程式碼進行偵錯
description: 使用 Visual Studio 對在遠端 Linux 電腦上執行的 Python 程式碼進行偵錯，包括必要的組態步驟、安全性和疑難排解。
ms.date: 05/12/2020
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: dcc5d9746a556af54ea206528fcb9a402e25d700
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99916616"
---
Visual Studio 可以在 Windows 電腦本機和遠端啟動 Python 應用程式並進行偵錯工具 (查看 [遠端偵錯](../../../debugger/remote-debugging.md)) 。 它也可以使用 [debugpy 程式庫](https://pypi.org/project/debugpy/)，在 CPython 以外的不同作業系統、裝置或 Python 執行上進行遠端偵錯。

使用 debugpy 時，所要調試的 Python 程式碼會裝載 Visual Studio 可以附加的 debug server。 這項裝載需要稍微修改您的程式碼以匯入和啟用伺服器，並可能需要遠端電腦上的網路或防火牆組態允許 TCP 連線。

> [!NOTE]
> 針對 Visual Studio 2019 16.4 版及更早版本，會使用 [ptvsd 程式庫](https://pypi.python.org/pypi/ptvsd) 。 Debugpy 程式庫已取代 Visual Studio 2019 16.5 版中的 ptvsd 4。

## <a name="set-up-a-linux-computer"></a>設定 Linux 電腦

若要遵循本逐步解說，需要下列項目：

- 執行 Python 的遠端電腦，作業系統為 Mac OS 或 Linux。
- 已開啟上述電腦的防火牆連接埠 5678 (輸入)，其為遠端偵錯的預設值。

> [!NOTE]
> 本逐步解說是以 Visual Studio 2019 16.6 版為基礎。

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

1. 使用 `pip3 install debugpy`，將 `debugpy` 封裝安裝到您的環境。
   >[!NOTE]
   >最好記錄安裝的 debugpy 版本，以防您需要它進行疑難排解; [debugpy 清單](https://pypi.org/project/debugpy/) 也會顯示可用的版本。

1. 盡早在 *guessing-game.py* 中的其他程式碼之前加入下列程式碼，以啟用遠端偵錯。 (雖然不是嚴格要求，但在呼叫 `listen` 函式前，無法對繁衍 (Spawn) 的任何背景執行緒進行偵錯。)

   ```python
   import debugpy
   debugpy.listen(5678)
   ```

1. 請儲存檔案，然後執行 `python3 guessing-game.py`。 `listen` 的呼叫會在背景執行，並等待您與程式互動時的連入連線。 如有需要，可以在 `listen` 之後呼叫 `wait_for_client` 函式來封鎖程式，直到偵錯工具附加為止。

> [!Tip]
> 除了和之外 `listen` `wait_for_client` ，debugpy 也會提供 helper 函式 `breakpoint` ，以在附加偵錯工具時做為程式設計的中斷點。 還有一個 `is_client_connected` 函式會在偵錯工具附加時傳回 `True` (請注意，在呼叫其他 `debugpy` 之前，不需檢查這個結果)。

## <a name="attach-remotely-from-python-tools"></a>從 Python 工具遠端附加

在這些步驟中，我們會設定中斷點以停止遠端程序。

1. 在本機電腦上建立遠端檔案的複本，然後在 Visual Studio 中開啟它。 檔案所在位置並不重要，但其名稱應符合遠端電腦上的指令碼名稱。

1.  (選擇性) 在本機電腦上具有 debugpy 的 IntelliSense，請將 debugpy 套件安裝到您的 Python 環境中。

1. 選取 [ **Debug**  >  **附加至進程**]。

1. 在出現的 [ **附加至進程** ] 對話方塊中，將 [ **連線類型** ] 設定為 [ **Python 遠端 (debugpy)**。

1. 在 [ **連接目標** ] 欄位中，輸入 `tcp://<ip_address>:5678` `<ip_address>` 遠端電腦 (的位置，它可以是明確的位址或名稱，例如 myvm.cloudapp.net) ，而 `:5678` 是遠端偵錯程式埠號碼。

1. 按 **enter** 鍵，以填入該電腦上可用的 debugpy 進程清單：

    ![輸入連線目標，並列出處理序](../../media/remote-debugging-attach.png)

    填入此清單之後，如果您剛好在遠端電腦上啟動另一個程式，請選取 [重新整理] 按鈕。

1. 選取要偵錯的處理序，再選取 [附加]，或按兩下處理序。

1. Visual Studio 即會切換至偵錯模式，而遠端電腦仍會繼續執行指令碼，並提供所有一般[偵錯](../../debugging-python-in-visual-studio.md)功能。 例如，在 `if guess < number:` 行上設定中斷點，然後切換到遠端電腦，並輸入另一種猜測。 進行上述作業之後，本機電腦的 Visual Studio 會在該中斷點停駐，並顯示本機變數等等：

    ![Visual Studio 會在到達中斷點時暫停偵錯](../../media/remote-debugging-breakpoint-hit.png)

1. 當您停止偵錯時，Visual Studio 會中斷連結程式，而遠端電腦仍會繼續執行該程式。 debugpy 也會繼續接聽附加偵錯工具，因此您可以隨時重新附加至進程。

### <a name="connection-troubleshooting"></a>連線疑難排解

1. 確定您已為連線 **類型** 選取 **Python 遠端 (debugpy)**
1. 檢查 **連接目標** 中的密碼是否完全符合遠端程式碼中的密碼。
1. 檢查 **連接目標** 中的 IP 位址是否與遠端電腦的 IP 位址相符。
1. 請確認您已在遠端電腦上開啟遠端偵錯程式埠，而且您已在連接目標中包含埠尾碼，例如 `:5678` 。
    - 如果您需要使用不同的埠，您可以在中指定它 `listen` ，如下所示 `debugpy.listen((host, port))` 。 在此情況下，請開啟防火牆中的特定連接埠。
1. 檢查在遠端電腦上安裝的 debugpy 版本 `pip3 list` 是否符合您在下表 Visual Studio 中所使用的 Python 工具版本所使用的版本，以符合所傳回的版本。 如有必要，請更新遠端電腦上的 debugpy。

    | Visual Studio 版本 | Python tools/debugpy 版本 |
    | --- | --- |
    | 2019 16。6 | 1.0.0 b5 |
    | 2019 16。5 | 1.0.0 b1 |

> [!NOTE]
> Visual Studio 2019 16.0 版-16.4 利用 ptvsd，而非 debugpy。 本逐步解說中針對這些版本的程式很類似，但函數名稱不同。 Visual Studio 2019 16.5 版使用 debugpy，但函數名稱與 ptvsd 中的名稱相同。 相反地 `listen` ，您會使用 `enable_attach` 。 相反地 `wait_for_client` ，您會使用 `wait_for_attach` 。 相反地 `breakpoint` ，您會使用 `break_into_debugger` 。

## <a name="using-ptvsd-3x-for-legacy-debugging"></a>使用 ptvsd 3.x 進行舊版的偵錯工具
Visual Studio 2017 15.8 版及更新版本使用以 ptvsd 4.1+ 版為基礎的偵錯工具。 Visual Studio 2019 版本16.5 和更新版本會使用以 debugpy 為基礎的偵錯工具。 這些版本的偵錯工具相容于 Python 2.7 和 Python 3.5 +。 如果您是使用 Python 2.6、3.1 到3.4 或 IronPython，Visual Studio 會顯示錯誤， **偵錯工具不支援此 Python 環境**。 下列資訊僅適用于使用 ptvsd 3.x 進行遠端偵錯。

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
