---
title: 如何套用 Python 搜尋路徑
description: Visual Studio 提供更具體方法來指定環境和專案的搜尋路徑，以避免使用全系統變數。
ms.date: 03/13/2019
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 43d24d38fcb9ba07d4cc8c58d7b544256171b049
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99902374"
---
# <a name="how-visual-studio-uses-python-search-paths"></a>Visual Studio 如何使用 Python 搜尋路徑

在典型的 Python 用法中，`PYTHONPATH` 環境變數 (或 `IRONPYTHONPATH` 等) 會提供模組檔案的預設搜尋路徑。 也就是說，當您使用 `from <name> import...` 或 `import <name>` 陳述式時，Python 會在下列位置搜尋相符的名稱：

1. Python 的內建模組。
1. 包含您正在執行之 Python 程式碼的資料夾。
1. 適用的環境變數所定義的「模組搜尋路徑」。 (請參閱核心 Python 文件中的[模組搜尋路徑 (英文)](https://docs.python.org/2/tutorial/modules.html#the-module-search-path) 和[環境變數 (英文)](https://docs.python.org/2/using/cmdline.html#envvar-PYTHONPATH))。

不過，即使針對整個系統設定了搜尋路徑環境變數，Visual Studio 也會將它忽略。 事實上，它會被忽略， *因為* 它是針對整個系統設定的，因此會引發無法自動回答的特定問題：所參考的模組是否適用于 python 2.7 或 Python 3.6 +？ 它們是否將覆寫標準程式庫程式庫模組？ 開發人員是否知道此行為，或它是否是惡意的劫持嘗試？

因此，Visual Studio 提供一個可在環境和專案中直接指定搜尋路徑的方法。 您在 Visual Studio 中執行或偵錯的程式碼，會從 `PYTHONPATH` (和其他對等的變數) 值來接收搜尋路徑。 透過新增搜尋路徑，Visual Studio 便會檢查那些位置中的程式庫，並視需要為它們建置 IntelliSense 資料庫 (Visual Studio 2017 15.5 版及較早版本；視程式庫的數目而定，建構資料庫可能需要一些時間)。

若要新增搜尋路徑，請移至 **方案總管**，展開專案節點，以滑鼠右鍵按一下 [ **搜尋路徑**]，然後選取 [ **將資料夾新增至搜尋路徑**]：

::: moniker range="vs-2017"
![[方案總管] 中，搜尋路徑上的 [將資料夾新增至搜尋路徑] 命令](media/search-paths-command.png)
::: moniker-end
::: moniker range=">=vs-2019"
![[方案總管] 中，搜尋路徑上的 [將資料夾新增至搜尋路徑] 命令](media/search-paths-command-2019.png)
::: moniker-end

此命令會顯示瀏覽器，然後您會在其中選取要包含的資料夾。

如果您的 `PYTHONPATH` 環境變數已經包含您想要的資料夾，請使用 [將 PYTHONPATH 新增至搜尋路徑] 作為方便的捷徑。

一旦資料夾新增至搜尋路徑，Visual Studio 會將這些路徑用於與專案建立關聯的任何環境。 (如果是 Python 3 環境，且您嘗試將搜尋路徑新增至 Python 2.7 模組，則可能會出現錯誤)。

您也可以新增副檔名為 *.zip* 或 *.egg* 的檔案作為搜尋路徑，方法是選取 [ 新增 ZIP 封存至搜尋路徑] 命令。 與使用資料夾時相同，系統會掃描這些檔案的內容並提供給 IntelliSense 使用。

## <a name="see-also"></a>另請參閱

- [在 Visual Studio 中管理 Python 環境](managing-python-environments-in-visual-studio.md)
- [選取專案的解譯器](selecting-a-python-environment-for-a-project.md)
- [為相依性使用 requirements.txt](managing-required-packages-with-requirements-txt.md)
- [Python 環境視窗參考](python-environments-window-tab-reference.md)
