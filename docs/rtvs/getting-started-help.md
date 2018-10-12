---
title: R 說明視窗
description: R 說明已直接整合至 Visual Studio 的互動式視窗。 方塊。
ms.date: 01/24/2018
ms.prod: visual-studio-dev15
ms.technology: vs-rtvs
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- data-science
ms.openlocfilehash: 6576a701abe699bfe47666acfc21c848dde1f53a
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "35666679"
---
# <a name="help-in-r-tools-for-visual-studio"></a>Visual Studio R 工具中的說明

R 說明已直接整合至 Visual Studio 的互動式視窗。 每當您使用 `?` 命令，例如 `?mtcars` 時，R 文件中的說明會出現在 Visual Studio 視窗︰

![Visual Studio 的 [說明] 視窗](media/help-window.png)

> [!Tip]
> [說明] 視窗就像 Visual Studio 的所有其他視窗，可以讓您隨心所欲地排列和停駐。 請參閱[在 Visual Studio 中自訂視窗版面配置](../ide/customizing-window-layouts-in-visual-studio.md)。
>
> 若要在瀏覽器中開啟說明結果，請選取 [R 工具] > [選項] 功能表，並將 [R 說明瀏覽器] 屬性設為 `External`。 請參閱[選項](options-for-r-tools-in-visual-studio.md)。

若要搜尋說明，請使用 `??` 命令，後面接著搜尋詞彙。 如果搜尋條件包含空格，請使用引號括住：

```R
??"Motor Trend"
```

![說明搜尋結果](media/help-search1.png)

[說明] 視窗也有搜尋輸入欄位，讓您可以直接在 R 文件中執行進一步搜尋︰

![使用輸入欄位的說明搜尋結果](media/help-search2.png)

## <a name="integrated-help-lookup"></a>整合式說明查閱

開發人員經常在 R 文件中搜尋函式名稱、資料集以及其他項目的說明。 Visual Studio R 工具 (RTVS) 藉由直接在編輯器和互動式視窗中整合說明查閱來簡化程序。

- 在自動完成的作業期間按 **F1** 鍵，會產生符合子字串的說明結果清單。
- 以滑鼠右鍵按一下搜尋字詞 (例如函式)，然後選取 [Help on] (說明於) 命令，即可開啟該函式的說明。 您也可以對任何選取範圍叫用 [說明於]。

    ![透過以滑鼠右鍵按一下的操作功能表叫用說明](media/help-right-click.png)

> [!Tip]
> 若要在瀏覽器中開啟整合式說明，請選取 [R 工具] > [選項]，並將 [F1 網頁瀏覽器] 設定為 `External`。 請參閱[選項](options-for-r-tools-in-visual-studio.md)。

## <a name="integrated-stackoverflow-search"></a>整合式 StackOverflow 搜尋

除了在 R 文件中搜尋之外，開發人員也經常在撰寫程式碼時搜尋 StackOverflow。 RTVS 也可以簡化這個程序。 以滑鼠右鍵按一下字詞或選取項目、選取 [在網路上搜尋] 命令 (**Ctrl**+**F1**)，Visual Studio 就會開啟一個視窗，且搜尋結果範圍只限於 StackOverflow：

![Visual Studio 中的網路搜尋結果](media/help-web-search-results.png)

您可以變更附加的範圍字串 `R site:stackoverflow`，藉由透過 [R 工具] > [選項] > [F1 網路搜尋字串] 選項︰

![變更 F1 網路搜尋字串選項](media/options-dialog.png)

如果您想要在瀏覽器中顯示結果，請變更 [F1 網頁瀏覽器] 選項，如[選項](options-for-r-tools-in-visual-studio.md)中所述。