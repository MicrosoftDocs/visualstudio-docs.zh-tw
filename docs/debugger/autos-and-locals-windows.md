---
title: 檢查變數-自動變數和區域變數視窗 |Microsoft Docs
description: 在 Visual Studio 中進行調試時，檢查 [自動變數] 和 [區域變數] 視窗中的變數。 當您進行調試時，[自動變數] 和 [區域變數] 視窗會顯示變數值。
ms.custom: SEO-VS-2020, seodec18
ms.date: 10/18/2018
ms.topic: how-to
f1_keywords:
- vs.debug.autos
- vs.debug.locals
helpviewer_keywords:
- debugger, variable windows
- debugging [Visual Studio], variable windows
ms.assetid: bb6291e1-596d-4af0-9f22-5fd713d6b84b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 61378b697b8cf2d50851926bb9f9b64b50878a59
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99857938"
---
# <a name="inspect-variables-in-the-autos-and-locals-windows"></a>在 [自動變數] 和 [區域變數] 視窗中檢查變數

當您進行調試時 **，[自動** 變數] 和 [ **區域變數** ] 視窗會顯示變數值。 只有在進行調試過程時，才可以使用 windows。 [自動變數] 視窗會顯示目前中斷點周圍 **使用的變數** 。 [ **區域變數** ] 視窗會顯示在區域範圍中定義的變數，這通常是目前的函式或方法。

> [!NOTE]
> 如果這是您第一次嘗試進行程式碼的偵錯工具，您可能會想要在進行這篇文章之前，先閱讀絕對初學者和[調試](../debugger/write-better-code-with-visual-studio.md)[程式的偵錯工具](../debugger/debugging-absolute-beginners.md)。

 [自動變數] 視窗 **適用于 c** #、Visual Basic、c + + 和 Python 程式碼，但不適用於 JavaScript 或 F #。

若 **要在進行** 調試時開啟 [自動變數] 視窗，請選取 [ **Debug** Windows 自動變數]  >    >  ****，或按 **Ctrl** + **Alt** + **V**  >  **A**。

若要開啟 [**區域變數**] 視窗，請在 [調試] 中選取 [ **Debug**  >  **Windows**  >  **區域變數**]，或按 **Alt** + **4**。

> [!NOTE]
> 本主題適用於 Windows 上的 Visual Studio。 如 Visual Studio for Mac，請參閱 [Visual Studio for Mac 中的資料視覺效果](/visualstudio/mac/data-visualizations)。

## <a name="use-the-autos-and-locals-windows"></a>使用自動變數和區域變數視窗

陣列 **和物件會在 [自動** 變數] 和 [ **區域變數** ] 視窗中顯示為樹狀目錄控制項。 選取變數名稱左邊的箭號來展開視圖，以顯示欄位和屬性。 以下是 <xref:System.IO.FileStream?displayProperty=fullName> [ **區域變數** ] 視窗中的物件範例：

![[區域變數] 視窗的螢幕擷取畫面，其中檔案設定為 system.string 值。](../debugger/media/locals-filestream.png)

[區域變數 **] 或**[自動 **變數**] 視窗中的紅色值表示自上次評估之後的值已變更。 變更可能來自先前的調試會話，或是因為您已變更視窗中的值。

偵錯工具視窗中的預設數值格式為 decimal。 若要將它變更為十六進位，請以滑鼠右鍵按一下 [區域變數 **] 或**[自動 **變數**] 視窗並選取 [**十六進位顯示**]。 此變更會影響所有偵錯工具視窗。

## <a name="edit-variable-values-in-the-autos-or-locals-window"></a>編輯 [自動變數] 或 [區域變數] 視窗中的變數值

若要在 [自動變數 **] 或 [** **區域變數** ] 視窗中編輯大部分變數的值，請按兩下值，然後輸入新值。

您可以輸入值的運算式，例如 `a + b`。 偵錯工具接受大部分的有效語言運算式。

在原生 C++ 程式碼中，您可能必須限定變數名稱的內容。 如需詳細資訊，請參閱 [ (c + +) 的內容運算子 ](../debugger/context-operator-cpp.md)。

>[!CAUTION]
>在變更值和運算式之前，請確定您瞭解這些結果。 可能的問題包括：
>
>- 評估某些運算式可能會變更變數的值，或是影響程式的狀態。 例如，評估會 `var1 = ++var2` 變更和兩者的值 `var1` `var2` 。 這些運算式被視為有 [副作用](https://en.wikipedia.org/wiki/Side_effect_\(computer_science\))。 如果您不知道副作用，可能會導致非預期的結果。
>
>- 由於分數元件的十進位至二進位轉換，編輯浮點數值會略微不精確。 即使看似無害的編輯也可能造成浮點變數中部分的部分變更。

::: moniker range=">= vs-2019" 
## <a name="search-in-the-autos-or-locals-window"></a>在 [自動變數] 或 [區域變數] 視窗中搜尋

您可以使用每個視窗上方的搜尋列，在 [自動變數] 或 [**區域變數**]**視窗的 [** 名稱]、[值] 和 [類型] 欄中搜尋關鍵字。 按 ENTER 鍵或選取其中一個箭號以執行搜尋。 若要取消進行中的搜尋，請選取搜尋列中的 "x" 圖示。

使用向左和向右箭號 (Shift + F3 和 F3 分別) ，以流覽找到的相符專案。

![在 [區域變數] 視窗中搜尋](../debugger/media/ee-search-locals.png "在 [區域變數] 視窗中搜尋")

若要讓您的搜尋更多或更少，請使用 [自動變數 **] 或 [** **區域變數**] 視窗頂端的 [**更深入搜尋**] 下拉式清單，選取您要搜尋到嵌套物件的深度層級。 

## <a name="pin-properties-in-the-autos-or-locals-window"></a>在 [自動變數] 或 [區域變數] 視窗中釘選屬性

> [!NOTE]
> .NET Core 3.0 或更高版本支援此功能。

您可以使用 [ **可釘選屬性** ] 工具，在 [自動變數] 和 [區域變數] 視窗中快速檢查物件的屬性。  若要使用此工具，請將滑鼠停留在屬性上，然後選取出現的釘選圖示，或按一下滑鼠右鍵，然後在產生的內容功能表中選取 [ **釘選成員** ] 選項。  這會將該屬性反升到物件之屬性清單的最上方，而屬性名稱和值會顯示在 [ **值** ] 資料行中。  若要取消釘選屬性，請再次選取 [釘選] 圖示，或在內容功能表中選取 [取消釘選 **成員** ] 選項。

![在 [區域變數] 視窗中釘選屬性](../debugger/media/basic-pin.gif "在 [區域變數] 視窗中釘選屬性")

當您在 [自動變數] 或 [區域變數] 視窗中查看物件的屬性清單時，您也可以切換屬性名稱，並篩選出未釘選的屬性。  您可以在 [自動變數] 或 [區域變數] 視窗上方的工具列中，選取按鈕來存取每個選項。

![篩選我的最愛屬性](../debugger/media/filter-pinned-properties-locals.png "篩選我的最愛屬性") 
![切換屬性名稱](../debugger/media/toggle-property-names.gif "切換屬性名稱")

::: moniker-end

## <a name="change-the-context-for-the-autos-or-locals-window"></a>變更 [自動變數] 或 [區域變數] 視窗的內容

您可以使用 [ **偵錯工具位置** ] 工具列來選取所 **需的函** 式、執行緒或進程，以變更 [自動變數] 和 [ **區域變數** ] 視窗的內容。

若要啟用 [**偵錯工具位置**] 工具列，請按一下工具列區域的空白部分，然後從下拉式清單中選取 [偵錯工具 **位置**]，或選取 [**查看**  >  **工具列** 的  >  **偵錯工具位置**]。

設定中斷點，並開始偵錯。 當叫用中斷點時，會暫停執行，而且您可以在 [ **偵錯工具位置** ] 工具列中看到位置。

![調試位置工具列](../debugger/media/debuglocationtoolbar.png "偵錯位置工具列")

## <a name="variables-in-the-autos-window-c-c-visual-basic-python"></a><a name="bkmk_whatvariables"></a> [自動變數] 視窗中的變數 (c #、c + +、Visual Basic、Python) 

不同的程式碼語言會 **在 [自動** 變數] 視窗中顯示不同的變數。

- 在 C# 和 Visual Basic 中，[自動變數] 視窗會顯示目前或前一行使用的任何變數。 例如，在 c # 或 Visual Basic 程式碼中，宣告下列四個變數：

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

   在該行設定中斷點 `c = 3;` ，然後啟動偵錯工具。 當執行暫停時， **[自動** 變數] 視窗將會顯示：

   ![[自動變數] 視窗的螢幕擷取畫面，將 c 的值設定為0。](../debugger/media/autos-csharp.png)

   的值 `c` 為0，因為行尚未 `c = 3` 執行。

- 在 c + + 中，[自動變數] 視窗會在執行暫停的目前行 **之前，至少** 顯示三行中所使用的變數。 例如，在 c + + 程式碼中，宣告六個變數：

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

    在行上設定中斷點 `e = 5;` 並執行偵錯工具。 當停止執行時， **[自動** 變數] 視窗將會顯示：

    ![[自動變數] 視窗的螢幕擷取畫面，其中已醒目提示顯示值為3的 int c 的行。](../debugger/media/autos-cplus.png)

    變數 `e` 未初始化，因為該行尚未 `e = 5` 執行。

## <a name="view-return-values-of-method-calls"></a><a name="bkmk_returnValue"></a> View return values of method calls
 在 .NET 和 c + + 程式碼中，當您跳過或跳過方法呼叫 **時，可以在 [自動** 變數] 視窗中檢查傳回值。 當方法呼叫傳回值不是儲存在本機變數中時，它會很有用。 方法可以當做參數使用，或做為另一個方法的傳回值。

 例如，下列 c # 程式碼會加入兩個函式的傳回值：

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

若要 `sumVars()` `subtractVars()` 在 [自動變數] 視窗中查看和方法呼叫的傳回值：

1. 在 `int x = sumVars(a, b) + subtractVars(c, d);` 行上設定中斷點。

1. 開始調試，當執行在中斷點暫停時，請選取 [不 **執行** ] 或按 **F10**。 您應該 **會在 [自動變數] 視窗** 中看到下列傳回值：

  ![自動變數傳回值 C#](../debugger/media/autosreturnvaluecsharp2.png "自動變數傳回值 C#")

## <a name="see-also"></a>另請參閱

- [什麼是偵錯？](../debugger/what-is-debugging.md)
- [偵錯技術和工具](../debugger/write-better-code-with-visual-studio.md)
- [先查看調試](../debugger/debugger-feature-tour.md)
- [偵錯工具視窗](../debugger/debugger-windows.md)
