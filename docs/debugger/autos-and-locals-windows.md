---
title: 檢查 [自動變數] 和 [區域變數] 視窗中的變數 |Microsoft Docs
ms.custom: H1Hack27Feb2017
ms.date: 10/18/2018
ms.technology: vs-ide-debug
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7e94c520ca01a92b65ba05a4ff91aaa4c01e7b8d
ms.sourcegitcommit: a811f6a194ccd40d844e74e618d847df87c85c16
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 11/29/2018
ms.locfileid: "52621467"
---
# <a name="inspect-variables-in-the-autos-and-locals-windows"></a>檢查 [自動變數] 和 [區域變數] 視窗中的變數

**自動變數**並**區域變數**在偵錯時，windows 會顯示變數的值。 在偵錯工作階段期間，才可以使用 windows。 **自動變數**視窗會顯示目前中斷點周圍使用的變數。 **區域變數**視窗會顯示在本機的範圍中，通常是目前函式或方法定義的變數。 如果這是您第一次您嘗試偵錯程式碼時，您可能想要讀取[修正 bug，藉由撰寫更好C#程式碼](../debugger/write-better-code-with-visual-studio.md)並[偵錯適用於徹底初學者](../debugger/debugging-absolute-beginners.md)再通過這篇文章。

 **自動變數**視窗可供C#，Visual Basic、 c + + 和 Python 程式碼，但不適用於 JavaScript 或F#。
  
若要開啟 **自動變數**視窗中的，偵錯時，選取**偵錯** > **Windows** > **自動變數**，或按**Ctrl**+**Alt**+**V** > **A**。  

若要開啟 **區域變數**視窗中的，偵錯時，選取**偵錯** > **Windows** > **區域變數**，或按**Alt**+**4**。

> [!NOTE]
> 本主題適用於 Windows 上的 Visual Studio。 Visual Studio for Mac，請參閱 <<c0> [ 在 Visual Studio for Mac 中的資料視覺效果](/visualstudio/mac/data-visualizations)。

## <a name="use-the-autos-and-locals-windows"></a>使用 [自動變數] 和 [區域變數] 視窗

陣列和物件會顯示在**自動變數**並**區域變數**windows 以樹狀結構控制項。 選取的可展開檢視來顯示欄位和屬性的變數名稱左邊的箭號。 以下是範例<xref:System.IO.FileStream?displayProperty=fullName>中的物件**區域變數**視窗：

![[區域變數] FileStream](../debugger/media/locals-filestream.png "區域變數 FileStream")

中的紅色值**區域變數**或是**自動變數**視窗表示值已在上次評估以後。 變更可能是從先前的偵錯工作階段，或因為您已變更 視窗中的值。

在 偵錯工具視窗的預設數值格式為十進位。 若要將它變更為十六進位，以滑鼠右鍵按一下**區域變數**或是**自動變數**視窗，然後選取**十六進位顯示**。 這項變更會影響所有偵錯工具視窗。

## <a name="edit-variable-values-in-the-autos-or-locals-window"></a>編輯 [自動變數] 或 [區域變數] 視窗中的變數值

若要編輯的中的大部分變數值**自動變數**或是**區域變數**windows 中，按兩下值，並輸入新值。

您可以輸入值的運算式，例如 `a + b`。 偵錯工具接受大部分的有效語言運算式。

在原生 C++ 程式碼中，您可能必須限定變數名稱的內容。 如需詳細資訊，請參閱[內容運算子 (C++)](../debugger/context-operator-cpp.md)。

>[!CAUTION]
>請確定您瞭解後果，再變更值和運算式。 一些可能的問題是：
>
>-   評估某些運算式可能會變更變數的值，或是影響程式的狀態。 例如，評估`var1 = ++var2`變更的值都`var1`和`var2`。 這些運算式被視為具有[副作用](https://en.wikipedia.org/wiki/Side_effect_\(computer_science\))。 如果您不知道它們的存在，副作用會造成非預期的結果。
>
>-   由於分數元件的十進位至二進位轉換，編輯浮點數值會略微不精確。 即使表面上無害的編輯也可能造成浮點變數中的位元的某些變更。

## <a name="change-the-context-for-the-autos-or-locals-window"></a>[自動變數] 或 [區域變數] 視窗的內容變更

您可以使用**偵錯位置**工具列選取想要的函式、 執行緒或處理程序，變更的內容**自動變數**並**區域變數**windows。

若要啟用**偵錯位置**工具列上，按一下工具列區域和選取的空白部分**偵錯位置**從下拉式清單中或選取**檢視** >  **工具列** > **偵錯位置**。

設定中斷點，並開始偵錯。 當叫用中斷點時，暫停執行，而且您可以看到中的位置**偵錯位置**工具列。

![偵錯位置工具列](../debugger/media/debuglocationtoolbar.png "偵錯位置工具列")

## <a name="bkmk_whatvariables"></a> 在 [自動變數] 視窗中的變數 (C#，c + +、 Visual Basic、 Python)

 不同的程式碼的語言會顯示在不同的變數**自動變數**視窗。

 - 在 C# 和 Visual Basic 中，[自動變數] 視窗會顯示目前或前一行使用的任何變數。 例如，在C#或 Visual Basic 程式碼中，宣告下列四個變數：

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

   在該行設定中斷點`c = 3;`，並開始偵錯工具。 當執行暫停**自動變數**視窗會顯示：

   ![[自動變數] CSharp](../debugger/media/autos-csharp.png "自動變數 CSharp")

   值`c`為 0，因為列`c = 3`尚未執行。

 - C + +**自動變數**視窗會顯示已暫停執行目前這一行之前至少三行中所使用的變數。 例如，在 c + + 程式碼中，宣告六個變數：

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

    在該行設定中斷點`e = 5;`並執行偵錯工具。 當執行停止時，**自動變數**視窗會顯示：

    ![[自動變數] c + +](../debugger/media/autos-cplus.png "自動變數-c + +")

    變數`e`未初始化，因為列`e = 5`尚未執行。

##  <a name="bkmk_returnValue"></a> View return values of method calls
 在.NET 和 c + + 程式碼中，您可以檢查中的傳回值**自動變數**不進入或者跳離方法呼叫時，視窗。 檢視方法呼叫傳回時不會儲存在本機變數，值可能很有用。 無法使用的方法，做為參數，或為另一種方法的傳回值。

 例如，下列C#程式碼會加入兩個函式的傳回值：

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

若要查看的傳回值`sumVars()`和`subtractVars()`方法會呼叫 [自動變數] 視窗中：

1. 在 `int x = sumVars(a, b) + subtractVars(c, d);` 行上設定中斷點。  
   
1. 開始偵錯，以及時的中斷點處暫停執行，選取**不進入函式**或按**F10**。 您應該會看到下列中的傳回值**自動變數**視窗：  
   
  ![自動變數傳回值C# ](../debugger/media/autosreturnvaluecsharp2.png "自動變數傳回值C#")  
  
## <a name="see-also"></a>另請參閱  
 [什麼是偵錯？](../debugger/what-is-debugging.md)  
 [透過撰寫更好的 C# 程式碼來修正 Bug](../debugger/write-better-code-with-visual-studio.md)  
 [第一次查看偵錯](../debugger/debugger-feature-tour.md)[偵錯工具視窗](../debugger/debugger-windows.md)
