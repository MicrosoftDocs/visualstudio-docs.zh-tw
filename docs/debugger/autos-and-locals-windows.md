---
title: 檢查變數-自動變數和區域變數視窗 |Microsoft Docs
ms.custom: seodec18
ms.date: 10/18/2018
ms.topic: conceptual
f1_keywords:
- vs.debug.autos
- vs.debug.locals
helpviewer_keywords:
- debugger, variable windows
- debugging [Visual Studio], variable windows
ms.assetid: bb6291e1-596d-4af0-9f22-5fd713d6b84b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b159f631534135ac568fb03dbffa46ae0360fc47
ms.sourcegitcommit: 0b90e1197173749c4efee15c2a75a3b206c85538
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/07/2019
ms.locfileid: "74904078"
---
# <a name="inspect-variables-in-the-autos-and-locals-windows"></a>檢查 [自動變數] 和 [區域變數] 視窗中的變數

當您進行調試時 **，[自動**變數] 和 [**區域變數**] 視窗會顯示變數值。 只有在進行調試過程時，才可以使用 windows。 [自動變數] 視窗會顯示目前中斷點周圍**使用的變數**。 [**區域變數**] 視窗會顯示本機範圍中定義的變數，這通常是目前的函式或方法。 如果這是您第一次嘗試偵錯工具代碼，您可能會想要在進行本文之前，先閱讀適用于徹底初學者和[偵錯工具技術和工具](../debugger/write-better-code-with-visual-studio.md) [的偵錯工具](../debugger/debugging-absolute-beginners.md)。

 [**自動**變數] 視窗適用C#于、Visual Basic C++、和 Python 程式碼，但不適用於 JavaScript F#或。

若要開啟 **[自動**變數] 視窗，請在 [調試] 時選取 [ **Debug** > **Windows** ** > 自動**變數]，或按**Ctrl**+**Alt**+**V** > **A**。

若要開啟 [**區域變數**] 視窗，請在 [調試] 時選取 [ **Debug** > **Windows** > **區域變數**]，或按**Alt**+**4**。

> [!NOTE]
> 本主題適用於 Windows 上的 Visual Studio。 如 Visual Studio for Mac，請參閱[Visual Studio for Mac 中的資料視覺效果](/visualstudio/mac/data-visualizations)。

## <a name="use-the-autos-and-locals-windows"></a>使用 [自動變數] 和 [區域變數] 視窗

陣列**和物件會在 [自動**變數] 和 [**區域變數**] 視窗中顯示為樹狀目錄控制項。 選取變數名稱左邊的箭號，以展開視圖以顯示欄位和屬性。 以下是 [**區域變數**] 視窗中 <xref:System.IO.FileStream?displayProperty=fullName> 物件的範例：

![區域變數-FileStream](../debugger/media/locals-filestream.png "區域變數 - FileStream")

[區域變數 **] 或**[自動**變數**] 視窗中的紅色值表示自上次評估之後，值已變更。 這項變更可能來自先前的調試階段，或因為您已變更視窗中的值。

偵錯工具視窗中的預設數值格式為 decimal。 若要將它變更為十六進位，以滑鼠右鍵按一下 [區域變數 **] 或**[自動**變數**] 視窗，然後選取 [**十六進位顯示**]。 這種變更會影響所有偵錯工具視窗。

## <a name="edit-variable-values-in-the-autos-or-locals-window"></a>編輯 [自動變數] 或 [區域變數] 視窗中的變數值

若要編輯 [自動變數] 或 [**區域變數**] 視窗中大部分變數的值，請按兩下值，然後輸入**新的值**。

您可以輸入值的運算式，例如 `a + b`。 偵錯工具接受大部分的有效語言運算式。

在原生 C++ 程式碼中，您可能必須限定變數名稱的內容。 如需詳細資訊，請參閱[內容運算子 (C++)](../debugger/context-operator-cpp.md)。

>[!CAUTION]
>在您變更值和運算式之前，請先確定您已瞭解這些結果。 一些可能的問題包括：
>
>- 評估某些運算式可能會變更變數的值，或是影響程式的狀態。 例如，評估 `var1 = ++var2` 會變更 `var1` 和 `var2`兩者的值。 這些運算式會被視為具有[副作用](https://en.wikipedia.org/wiki/Side_effect_\(computer_science\))。 如果您不知道，副作用可能會導致非預期的結果。
>
>- 由於分數元件的十進位至二進位轉換，編輯浮點數值會略微不精確。 即使看似無害的編輯，也可能會導致浮點變數中某些位的變更。

::: moniker range=">= vs-2019" 
## <a name="search-in-the-autos-or-locals-window"></a>在 [自動變數] 或 [區域變數] 視窗中搜尋

您可以使用每個視窗上方的搜尋列，在 [自動變數] 或 [**區域變數**] 視窗的 [名稱]、[值]**和 [類型**] 資料行中搜尋關鍵字。 按 ENTER 鍵或選取其中一個箭號來執行搜尋。 若要取消進行中的搜尋，請選取搜尋列中的 "x" 圖示。

使用左右箭號（分別 Shift + F3 和 F3）以流覽找到的相符專案。

![在 [區域變數] 視窗中搜尋](../debugger/media/ee-search-locals.png "在 [區域變數] 視窗中搜尋")

若要讓搜尋更多或更不全面，請**使用 [自動變數] 或 [** **區域變數**] 視窗頂端的 [**更深入搜尋**] 下拉式清單，選取您想要在多個嵌套物件中搜尋的深度層級。 

## <a name="pin-properties-in-the-autos-or-locals-window"></a>在 [自動變數] 或 [區域變數] 視窗中釘選屬性

> [!NOTE]
> .NET Core 3.0 或更高版本支援這項功能。

您可以使用 [**可固定屬性**] 工具，在 [自動變數] 和 [區域變數] 視窗中，以其屬性快速檢查物件。  若要使用此工具，請將滑鼠停留在屬性上，然後選取顯示的釘選圖示，或按一下滑鼠右鍵，然後在產生的內容功能表中選取 [**釘選成員為我的最愛**] 選項  這會將該屬性反升至物件之屬性清單的頂端，而屬性名稱和值會顯示在 [**值**] 資料行中。  若要取消固定屬性，請再次選取釘選圖示，或選取內容功能表中的 [**取消固定成員為我的最愛**] 選項。

![在 [區域變數] 視窗中釘選屬性](../debugger/media/basic-pin.gif "在 [區域變數] 視窗中釘選屬性")

在 [自動變數] 或 [區域變數] 視窗中查看物件的屬性清單時，您也可以切換屬性名稱，並篩選出未釘選的屬性。  您可以藉由選取 [自動變數] 或 [區域變數] 視窗上方工具列中的按鈕，來存取每個選項。

![篩選我的最愛屬性](../debugger/media/filter-pinned-properties-locals.png "篩選我的最愛屬性")
![切換屬性名稱](../debugger/media/toggle-property-names.gif "切換屬性名稱")

::: moniker-end

## <a name="change-the-context-for-the-autos-or-locals-window"></a>變更 [自動變數] 或 [區域變數] 視窗的內容

您可以使用 [**偵錯工具位置**] 工具列來選取所**需的函**式、執行緒或進程，以變更 [自動變數] 和 [**區域變數**] 視窗的內容。

若要啟用 [**偵錯工具位置**] 工具列，請按一下工具列區域的空白部分，然後從下拉式清單中選取 [ **Debug Location** ]，或選取 [ **View** > **工具列** > **debug location**]。

設定中斷點，並開始偵錯。 到達中斷點時，會暫停執行，而且您可以在 [**調試位置**] 工具列中看到位置。

![[調試位置] 工具列](../debugger/media/debuglocationtoolbar.png "偵錯位置工具列")

## <a name="bkmk_whatvariables"></a>[自動變數] 視窗中C#的C++變數（、、Visual Basic、Python）

不同的程式碼語言會**在 [自動**變數] 視窗中顯示不同的變數。

- 在 C# 和 Visual Basic 中，[自動變數] 視窗會顯示目前或前一行使用的任何變數。 例如，在或C# Visual Basic 程式碼中，宣告下列四個變數：

   ```csharp
       public static void Main()
       {
          int a, b, c, d;
          a = 1;
          b = 2;
          c = 3;
          d = 4;
       }
   ```

   在 `c = 3;`行上設定中斷點，並啟動偵錯工具。 當執行暫停時， **[自動**變數] 視窗將會顯示：

   ![自動變數-CSharp](../debugger/media/autos-csharp.png "Autos-CSharp")

   `c` 的值為0，因為尚未執行行 `c = 3`。

- 在C++中，[自動變數] 視窗會在執行暫停的目前行之前，顯示至少三行**中所使用**的變數。 例如，在程式C++代碼中，宣告六個變數：

   ```C++
       void main() {
           int a, b, c, d, e, f;
           a = 1;
           b = 2;
           c = 3;
           d = 4;
           e = 5;
           f = 6;
       }
   ```

    在行 `e = 5;` 上設定中斷點，並執行偵錯工具。 當執行停止時， **[自動**變數] 視窗將會顯示：

    ![自動C++](../debugger/media/autos-cplus.png "自動C++")

    變數 `e` 未初始化，因為尚未執行行 `e = 5`。

## <a name="bkmk_returnValue"></a> View return values of method calls
 在 .NET 和C++程式碼中，您可以在不進入或跳過方法呼叫**時，檢查 [自動**變數] 視窗中的傳回值。 當方法呼叫傳回值不是儲存在本機變數時，可能會很有用。 方法可用來做為參數，或做為另一個方法的傳回值。

 例如，下列C#程式碼會新增兩個函數的傳回值：

```csharp
static void Main(string[] args)
{
    int a, b, c, d;
    a = 1;
    b = 2;
    c = 3;
    d = 4;
    int x = sumVars(a, b) + subtractVars(c, d);
}

private static int sumVars(int i, int j)
{
    return i + j;
}

private static int subtractVars(int i, int j)
{
    return j - i;
}
```

若要查看 [自動變數] 視窗中 `sumVars()` 和 `subtractVars()` 方法呼叫的傳回值：

1. 在 `int x = sumVars(a, b) + subtractVars(c, d);` 行上設定中斷點。

1. 開始進行調試，並于中斷點暫停執行時 **，選取 [** 不進入函式] 或按**F10**。 您應該**會在 [自動變數] 視窗**中看到下列傳回值：

  ![自動變數傳回值C#](../debugger/media/autosreturnvaluecsharp2.png "自動變數傳回值C#")

## <a name="see-also"></a>請參閱

- [什麼是偵錯？](../debugger/what-is-debugging.md)
- [偵錯技術和工具](../debugger/write-better-code-with-visual-studio.md)
- [第一次查看調試](../debugger/debugger-feature-tour.md)
- [偵錯工具視窗](../debugger/debugger-windows.md)
