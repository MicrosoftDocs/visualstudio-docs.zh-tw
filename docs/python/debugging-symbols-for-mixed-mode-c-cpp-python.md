---
title: Python/C++ 混和模式符號偵錯
description: Visual Studio 如何針對完全混合模式的 C++ 和 Python 偵錯提供載入符號的功能。
ms.date: 11/12/2018
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- python
- data-science
ms.openlocfilehash: 52eb7535430248f519654c09924541a6900336cc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99933085"
---
# <a name="install-debugging-symbols-for-python-interpreters"></a>安裝 Python 解譯器的偵錯符號

為提供完整的偵錯體驗，Visual Studio 中的[混合模式 Python 偵錯工具](debugging-mixed-mode-c-cpp-python-in-visual-studio.md)需要使用 Python 解譯器的偵錯符號，以便剖析許多內部資料結構。 例如 *python27.dll*，對應的符號檔是 *python27 .pdb*;針對 *python36.dll*，符號檔為 *python36 .pdb*。 每個版本的解譯器也提供各種不同模組的符號檔。

使用 Visual Studio 2017 和更新版本時，Python 3 和 Anaconda 3 解譯器會自動安裝其個別符號，而 Visual Studio 會自動尋找這些符號。 針對 Visual Studio 2015 及更早版本，或使用其他解譯器時，您必須個別下載符號，然後透過 [偵錯工具符號] 索引標籤中的 [工具  >  **選項**] 對話方塊，將 Visual Studio 指向這些符號  >   。這些步驟會在下列各節中詳細說明。

Visual Studio 會在需要符號時提示您，一般來說，這是指啟動混合模式偵錯工作階段的時候。 在此情況下，它會顯示內含兩個選擇的對話方塊：

- [開啟符號設定] 對話方塊會將 [選項] 對話方塊開啟至 [偵錯] > [符號] 索引標籤。
- [下載我的解譯器的符號] 會開啟這個存在的文件頁面，在此情況下，請選取 [工具] > [選項]，然後巡覽至 [偵錯] > [符號] 索引標籤以繼續。

    ![混合模式偵錯工具符號提示](media/mixed-mode-debugging-symbols-required.png)

## <a name="download-symbols"></a>載入符號

- Python 3.5 和更新版本：透過 Python 安裝程式取得偵錯符號。 依序選取 [自訂安裝] 和 [下一步] 移至 [進階選項]，然後選取 [下載偵錯符號] 和 [下載偵錯二進位檔案] 的方塊：

    ![包括偵錯符號的 Python 3.x 安裝程式](media/mixed-mode-debugging-symbols-installer35.png)

    符號檔 (*.pdb*) 會位於根安裝資料夾中，而個別模組的符號檔也在 *DLLs* 資料夾中。 因此，Visual Studio 會自動尋找這些檔案，您不需採取其他步驟。

- Python 3.4.x 和更早版本：您可透過 [官方發行版](#official-distributions)或 [Enthought Canopy](#enthought-canopy) 的可下載 *.zip* 檔案，取得符號。 下載之後，請將檔案解壓縮至本機資料夾 (例如 Python 資料夾內的 *Symbols* 資料夾) 以繼續。

    > [!Important]
    > Python 次要組建以及 32 位元和 64 位元組建之間的符號有所不同，因此您需要完全符合的版本。 若要檢查目前使用的解譯器，請展開 [方案總管] 中專案下方的 [Python 環境]**「節點」** ，並記下環境名稱。 然後切換到 [Python 環境] *視窗*，並記下安裝位置。 隨即在該位置開啟命令視窗，並啟動 *python.exe*，即會顯示其為 32 位元或 64 位元的正確版本。

- 若是協力廠商 Python 發行版，例如 ActiveState Python：請連絡該發行版的作者，並要求他們提供符號。 WinPython 結合了未經變更的標準 Python 解譯器，因此，請使用官方發行版對應版本號碼的符號。

## <a name="point-visual-studio-to-the-symbols"></a>將 Visual Studio 指向符號

如果您分別下載符號，請遵循下列步驟以讓 Visual Studio 知道它們的存在。 如果您已透過 Python 3.5 或更新版本的安裝程式來安裝符號，Visual Studio 會自動尋找這些符號。

1. 選取 [**工具**  >  **選項**] 功能表，然後流覽至 [**調試**  >  **符號**]。

1. 選取工具列上的 [新增] 按鈕 (如下所述)，輸入您要展開下載符號之資料夾 (*python.pdb* 的位置，例如 *c:\python34\Symbols*，如下所示)，然後選取 [確定]。

    ![混合模式偵錯工具符號選項](media/mixed-mode-debugging-symbols.png)

1. 偵錯工作階段期間，Visual Studio 也可能會提示您輸入 Python 解譯器的原始程式檔位置。 如果您已從 [python.org/downloads/](https://www.python.org/downloads/)下載原始程式檔 (（例如) ），當然也可以指向它們。

> [!Note]
> 對話方塊顯示的符號快取功能，可用來建立從線上來源取得之符號的本機快取。 既然符號已存在於本機，Python 解譯器的符號就不需要這些功能。 在任何情況下，請參閱 [Visual Studio 偵錯工具中的指定符號和原始程式](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) 檔，以取得詳細資料。

## <a name="official-distributions"></a>官方發行版

| Python 版本 | 下載 |
| --- | --- |
| 3.5 和更新版本 | 透過 Python 安裝程式來安裝符號。 |
| 3.4.4 | [32 位](https://www.python.org/ftp/python/3.4.4/python-3.4.4-pdb.zip)  - [64](https://www.python.org/ftp/python/3.4.4/python-3.4.4.amd64-pdb.zip)位 |
| 3.4.3 | [32 位](https://www.python.org/ftp/python/3.4.3/python-3.4.3-pdb.zip)  - [64](https://www.python.org/ftp/python/3.4.3/python-3.4.3.amd64-pdb.zip)位 |
| 3.4.2 | [32 位](https://www.python.org/ftp/python/3.4.2/python-3.4.2-pdb.zip)  - [64](https://www.python.org/ftp/python/3.4.2/python-3.4.2.amd64-pdb.zip)位 |
| 3.4.1 | [32 位](https://www.python.org/ftp/python/3.4.1/python-3.4.1-pdb.zip)  - [64](https://www.python.org/ftp/python/3.4.1/python-3.4.1.amd64-pdb.zip)位 |
| 3.4.0 | [32 位](https://www.python.org/ftp/python/3.4.0/python-3.4.0-pdb.zip)  - [64](https://www.python.org/ftp/python/3.4.0/python-3.4.0.amd64-pdb.zip)位 |
| 3.3.5 | [32 位](https://www.python.org/ftp/python/3.3.5/python-3.3.5-pdb.zip)  - [64](https://www.python.org/ftp/python/3.3.5/python-3.3.5.amd64-pdb.zip)位 |
| 3.3.4 | [32 位](https://www.python.org/ftp/python/3.3.4/python-3.3.4-pdb.zip)  - [64](https://www.python.org/ftp/python/3.3.4/python-3.3.4.amd64-pdb.zip)位 |
| 3.3.3 | [32 位](https://www.python.org/ftp/python/3.3.3/python-3.3.3-pdb.zip)  - [64](https://www.python.org/ftp/python/3.3.3/python-3.3.3.amd64-pdb.zip)位 |
| 3.3.2 | [32 位](https://www.python.org/ftp/python/3.3.2/python-3.3.2-pdb.zip)  - [64](https://www.python.org/ftp/python/3.3.2/python-3.3.2.amd64-pdb.zip)位 |
| 3.3.1 | [32 位](https://www.python.org/ftp/python/3.3.1/python-3.3.1-pdb.zip)  - [64](https://www.python.org/ftp/python/3.3.1/python-3.3.1.amd64-pdb.zip)位 |
| 3.3.0 | [32 位](https://www.python.org/ftp/python/3.3.0/python-3.3.0-pdb.zip)  - [64](https://www.python.org/ftp/python/3.3.0/python-3.3.0.amd64-pdb.zip)位 |
| 2.7.15 | [32 位](https://www.python.org/ftp/python/2.7.15/python-2.7.15-pdb.zip)  - [64](https://www.python.org/ftp/python/2.7.15/python-2.7.15.amd64-pdb.zip)位 |
| 2.7.14 | [32 位](https://www.python.org/ftp/python/2.7.14/python-2.7.14-pdb.zip)  - [64](https://www.python.org/ftp/python/2.7.14/python-2.7.14.amd64-pdb.zip)位 |
| 2.7.13 | [32 位](https://www.python.org/ftp/python/2.7.13/python-2.7.13-pdb.zip)  - [64](https://www.python.org/ftp/python/2.7.13/python-2.7.13.amd64-pdb.zip)位 |
| 2.7.12 | [32 位](https://www.python.org/ftp/python/2.7.12/python-2.7.12-pdb.zip)  - [64](https://www.python.org/ftp/python/2.7.12/python-2.7.12.amd64-pdb.zip)位 |
| 2.7.11 | [32 位](https://www.python.org/ftp/python/2.7.11/python-2.7.11-pdb.zip)  - [64](https://www.python.org/ftp/python/2.7.11/python-2.7.11.amd64-pdb.zip)位 |
| 2.7.10 | [32 位](https://www.python.org/ftp/python/2.7.10/python-2.7.10-pdb.zip)  - [64](https://www.python.org/ftp/python/2.7.10/python-2.7.10.amd64-pdb.zip)位 |
| 2.7.9 | [32 位](https://www.python.org/ftp/python/2.7.9/python-2.7.9-pdb.zip)  - [64](https://www.python.org/ftp/python/2.7.9/python-2.7.9.amd64-pdb.zip)位 |
| 2.7.8 | [32 位](https://www.python.org/ftp/python/2.7.8/python-2.7.8-pdb.zip)  - [64](https://www.python.org/ftp/python/2.7.8/python-2.7.8.amd64-pdb.zip)位 |
| 2.7.7 | [32 位](https://www.python.org/ftp/python/2.7.7/python-2.7.7-pdb.zip)  - [64](https://www.python.org/ftp/python/2.7.7/python-2.7.7.amd64-pdb.zip)位 |
| 2.7.6 | [32 位](https://www.python.org/ftp/python/2.7.6/python-2.7.6-pdb.zip)  - [64](https://www.python.org/ftp/python/2.7.6/python-2.7.6.amd64-pdb.zip)位 |
| 2.7.5 | [32 位](https://www.python.org/ftp/python/2.7.5/python-2.7.5-pdb.zip)  - [64](https://www.python.org/ftp/python/2.7.5/python-2.7.5.amd64-pdb.zip)位 |
| 2.7.4 | [32 位](https://www.python.org/ftp/python/2.7.4/python-2.7.4-pdb.zip)  - [64](https://www.python.org/ftp/python/2.7.4/python-2.7.4.amd64-pdb.zip)位 |
| 2.7.3 | [32 位](https://www.python.org/ftp/python/2.7.3/python-2.7.3-pdb.zip)  - [64](https://www.python.org/ftp/python/2.7.3/python-2.7.3.amd64-pdb.zip)位 |
| 2.7.2 | [32 位](https://www.python.org/ftp/python/2.7.2/python-2.7.2-pdb.zip)  - [64](https://www.python.org/ftp/python/2.7.2/python-2.7.2.amd64-pdb.zip)位 |
| 2.7.1 | [32 位](https://www.python.org/ftp/python/2.7.1/python-2.7.1-pdb.zip)  - [64](https://www.python.org/ftp/python/2.7.1/python-2.7.1.amd64-pdb.zip)位 |

## <a name="enthought-canopy"></a>Enthought Canopy

從 1.2 版開始，Enthought Canopy 提供二進位檔案的符號。 它們會自動隨發行版一起安裝，但是，如先前所述，您仍然需要將包含符號檔的資料夾手動新增至符號路徑。 針對 Canopy 典型的每個使用者安裝，如為 64 位元版本，符號位於 *%UserProfile%\AppData\Local\Enthought\Canopy\User\Scripts*，如為 32 位元版本，符號位於 *%UserProfile%\AppData\Local\Enthought\Canopy32\User\Scripts*。

Enthought Canopy 1.1 及更舊的版本和 Enthought Python 發行版 (EPD) 不提供解譯器符號，因此不相容於混合模式偵錯。
