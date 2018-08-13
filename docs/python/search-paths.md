---
title: 如何套用 Python 搜尋路徑
description: Visual Studio 如何在環境和專案中使用 Python 搜尋路徑的概觀。
ms.date: 06/27/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: 64958097b7a5fe86cda1d2b7dee62c69cd2fea63
ms.sourcegitcommit: 56ae5032d99d948aae0548ae318ca2bae97ea962
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/07/2018
ms.locfileid: "39586413"
---
# <a name="how-visual-studio-uses-python-search-paths"></a>Visual Studio 如何使用 Python 搜尋路徑

在典型的 Python 用法中，`PYTHONPATH` 環境變數 (或 `IRONPYTHONPATH` 等) 會提供模組檔案的預設搜尋路徑。 也就是說，當您使用 `from <name> import...` 或 `import <name>` 陳述式時，Python 會在下列位置搜尋相符的名稱：

1. Python 的內建模組。
1. 包含您正在執行之 Python 程式碼的資料夾。
1. 適用的環境變數所定義的「模組搜尋路徑」。 (請參閱核心 Python 文件中的[模組搜尋路徑 (英文)](https://docs.python.org/2/tutorial/modules.html#the-module-search-path) 和[環境變數 (英文)](https://docs.python.org/2/using/cmdline.html#envvar-PYTHONPATH))。

不過，即使針對整個系統設定了搜尋路徑環境變數，Visual Studio 也會將它忽略。 實際上，正因為它是針對整個系統設定的，並會提出「所參考的模組是用於 Python 2.7 還是 Python 3.6？」這類無法自動回答的問題，所以才要忽略它。 它們是否將覆寫標準程式庫程式庫模組？ 開發人員是否知道此行為，或它是否是惡意的劫持嘗試？

因此，Visual Studio 提供一個可在環境和專案中直接指定搜尋路徑的方法。 您在 Visual Studio 中執行或偵錯的程式碼，會從 `PYTHONPATH` (和其他對等的變數) 值來接收搜尋路徑。 透過新增搜尋路徑，Visual Studio 便會檢查那些位置中的程式庫，並視需要為它們建置 IntelliSense 資料庫 (Visual Studio 2017 15.5 版及較早版本；視程式庫的數目而定，建構資料庫可能需要一些時間)。

若要新增搜尋路徑，請在 [方案總管] 中的 [搜尋路徑] 項目上按一下滑鼠右鍵、選取 [ 將資料夾新增至搜尋路徑]，然後選取要包含的資料夾。 這個路徑會用於與該專案關聯的所有環境。 (如果是 Python 3 環境，且您嘗試將搜尋路徑新增至 Python 2.7 模組，則可能會出現錯誤)。

您也可以新增副檔名為 *.zip* 或 *.egg* 的檔案作為搜尋路徑，方法是選取 [ Zip 封存新增至搜尋路徑]。 與使用資料夾時相同，系統會掃描這些檔案的內容並提供給 IntelliSense 使用。

如果您固定使用相同的搜尋路徑且內容不常變更，則將它安裝到您的站台套件資料夾中可能會較有效率。 搜尋路徑接著會被分析並儲存在 IntelliSense 資料庫中、一律會與其預期的環境建立關聯，而且不需要將搜尋路徑新增至每個專案。

### <a name="see-also"></a>另請參閱

- [在 Visual Studio 中管理 Python 環境](managing-python-environments-in-visual-studio.md)
- [選取專案的解譯器](selecting-a-python-environment-for-a-project.md)
- [為相依性使用 requirements.txt](managing-required-packages-with-requirements-txt.md)
- [Python 環境視窗參考](python-environments-window-tab-reference.md)