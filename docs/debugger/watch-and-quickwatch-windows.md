---
title: 設置變數上的監視 |微軟文檔
ms.custom: seodec18
ms.date: 10/11/2018
ms.topic: conceptual
f1_keywords:
- vs.debug.watch
helpviewer_keywords:
- debugging [Visual Studio], Watch window
- expressions [debugger], evaluating
- variables [debugger], evaluating
- expression evaluation
- registers, evaluating
- debugging [Visual Studio], expression evaluation
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ea3d2a1e82e92473859fef29754fbb831cf3685b
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302004"
---
# <a name="watch-variables-with-watch-windows-and-quickwatch"></a>使用"監看視窗"和"快速監視"觀看變數

調試時，可以使用 **"監視"** 視窗和**QuickWatch**監視變數和運算式。 這些視窗僅在調試會話期間可用。

**監視**視窗在調試時一次可以顯示多個變數。 **"QuickWatch"** 對話方塊一次顯示單個變數，必須先關閉，然後才能繼續調試。

如果這是您第一次嘗試調試代碼，則可能需要在閱讀本文之前閱讀[絕對初學者](../debugger/debugging-absolute-beginners.md)調試以及[調試技術和工具](../debugger/write-better-code-with-visual-studio.md)。

## <a name="observe-variables-with-a-watch-window"></a>使用"監視"視窗觀察變數

您可以打開多個 **"監視"** 視窗，並在 **"監視"** 視窗中觀察多個變數。

例如，要設置 值 上的監視`a`，`b`請`c`放在 和 在以下代碼中：

```C++
int main()
{
    int a, b, c;
    a = 1;
    b = 2;
    c = 0;

    for (int i = 0; i < 10; i++)
    {
        a++;
        b *= 2;
        c = a + b;
    }

    return 0;
}

```

1. 通過按一下左邊距、選擇`c = a + b;`**調試** > **切換中斷點**或按**F9**在行上設置中斷點。

1. 通過選擇綠色 **"開始"** 箭頭或**調試** > **開始調試**，或按**F5**啟動調試。 執行在中斷點處暫停。

1. 通過選擇 **"調試** > **視窗** > **監視** > **1"** 或按**Ctrl**+**Alt**+**W** > **1**打開**監視**視窗。

   您可以通過選擇視窗**2、3**或**4**來打開其他 **"監視"** 視窗。 **3**

1. 在 **"監視"** 視窗中，選擇一個空行，並`a`鍵入變數 。 對 和`c``b`執行相同的操作。

   ![監視變數](../debugger/media/watchvariables.png "手錶變數")

1. 根據需要選擇 **"調試** > **步驟"** 或按**F11**以繼續調試。 當您迴圈流覽`for`迴圈時，"**監視"** 視窗中的變數值會發生變化。

>[!NOTE]
>僅對於C++，
>- 您可能需要限定變數名稱的上下文或使用變數名稱的運算式。 上下文是變數所在的函數、原始檔案或模組。 如果必須限定上下文，請使用 **"監視"** 視窗中 **"名稱**"中的[上下文運算子 （C++）](../debugger/context-operator-cpp.md)語法。
>
>- ** $您可以使用\<寄存器&nbsp;名稱>** 或**@&nbsp;寄存器名稱>將寄存器名稱和變數名稱添加到"監視"視窗中的"名稱"中>。 \< ** **Name** **Watch** 如需詳細資訊，請參閱 [Pseudovariables](../debugger/pseudovariables.md)。

## <a name="use-expressions-in-a-watch-window"></a>在"監視"視窗中使用運算式

您可以在 **"監視"** 視窗中觀察調試器識別的任何有效運算式。

例如，對於上一節中的代碼，您可以通過在`(a + b + c) / 3`**"監視"** 視窗中輸入來獲取三個值的平均值：

![觀看運算式](../debugger/media/watchexpression.png "觀看運算式")

在**Watch**視窗中計算運算式的規則通常與計算代碼語言中的運算式的規則相同。 如果運算式存在語法錯誤，則預期與代碼編輯器中的編譯器錯誤相同。 例如，前面的運算式中的拼寫錯誤在 **"監視"** 視窗中生成此錯誤：

![監視運算式錯誤](../debugger/media/watchexpressionerror.png "監視運算式錯誤")

**"監視"** 視窗中可能會出現一個帶有兩個波浪線圖示的圓圈。 此圖示表示調試器不會由於潛在的跨執行緒依賴關係而計算運算式。 評估代碼需要應用中的其他執行緒暫時運行，但由於您處於中斷模式，因此應用中的所有線程通常都會停止。 允許其他執行緒暫時運行可能會對應用的狀態產生意外影響，調試器可能會忽略這些執行緒上的中斷點和異常等事件。

::: moniker range=">= vs-2019" 
## <a name="search-in-the-watch-window"></a>在"監視"視窗中搜索

您可以使用每個視窗上方的搜索欄在 **"監視"** 視窗的"名稱"、"值"和"類型"列中搜索關鍵字。 點擊 ENTER 或選擇其中一個箭頭以執行搜索。 要取消正在進行的搜索，請選擇搜索欄中的"x"圖示。

使用左箭頭和右箭頭（分別使用 Shift_F3 和 F3）在找到的匹配項之間導航。

![在監看視窗中搜索](../debugger/media/ee-search-watch.png "在監看視窗中搜索")

要使搜索更加徹底，請使用 **"監視"** 視窗頂部的 **"搜索更深**"下拉式功能表來選擇要搜索到嵌套物件的深度級別。 

## <a name="pin-properties-in-the-watch-window"></a>"監視"視窗中的固定屬性

>[!NOTE]
> .NET 核心 3.0 或更高版本支援此功能。

您可以使用"**可固定屬性**"工具在"監視"視窗中按其屬性快速檢查物件。  要使用此工具，請將滑鼠懸停在屬性上，然後選擇顯示或按右鍵的引腳圖示，並在生成的內容功能表中選擇 **"固定成員"作為"我的最愛**"選項。  這將該屬性氣泡到物件的屬性清單的頂部，並且屬性名稱和值顯示在 **"值"** 列中。  要取消固定屬性，請再次選擇固定圖示，或在內容功能表中選擇 **"取消固定成員"作為"我的最愛**"選項。

!["監視"視窗中的固定屬性](../debugger/media/basic-pin-watch.gif ""監視"視窗中的固定屬性")

在"監視"視窗中查看物件的屬性清單時，還可以切換屬性名稱並篩選出非固定屬性。  您可以通過選擇監看視窗上方的工具列中的按鈕來訪問這兩個選項。

::: moniker-end

### <a name="refresh-watch-values"></a><a name="bkmk_refreshWatch"></a>刷新手錶值

計算運算式時 **，"監視"** 視窗中可能會出現刷新圖示（圓形箭頭）。 刷新圖示指示錯誤或過期的值。

要刷新值，請選擇刷新圖示，或按空格鍵。 偵錯工具會嘗試重新評估運算式。 但是，您可能不希望或能夠重新評估運算式，具體取決於未計算該值的原因。

將滑鼠懸停在刷新圖示上，或查看 **"值"** 列，瞭解運算式未計算的原因。 原因包括：

- 計算運算式時發生錯誤，如上一個示例所示。 可能會出現超時，或者變數可能出自範圍。

- 運算式具有一個函式呼叫，該調用可能會在應用中觸發副作用。 請參閱[運算式副作用](#bkmk_sideEffects)。

- 禁用屬性和隱式函式呼叫的自動計算。

如果刷新圖示由於禁用屬性和隱式函式呼叫而出現，則可以通過在**工具** > **選項** > **調試** > **一般**中選擇**啟用屬性計算和其他隱式函式呼叫**來啟用它。

要演示使用刷新圖示：

1. 在**工具** > **選項** > **Debugging**調試 > **一般**中，清除**啟用屬性計算和其他隱式函式呼叫**核取方塊。

1. 輸入以下代碼，在 **"監視"** 視窗中，在`list.Count`屬性上設置監視。

   ```csharp
   static void Main(string[] args)
   {
       List<string> list = new List<string>();
       list.Add("hello");
       list.Add("goodbye");
   }
   ```

1. 開始偵錯。 **"監視"** 視窗顯示類似以下內容的消息：

   ![刷新手錶](../debugger/media/refreshwatch.png "刷新手錶")

1. 要刷新值，請選擇刷新圖示，或按空格鍵。 調試器重新評估運算式。

### <a name="expression-side-effects"></a><a name="bkmk_sideEffects"></a>運算式副作用

評估某些運算式可能會更改變數的值，或者以其他方式影回應用的狀態。 例如，評估下列運算式會變更 `var1`的值：

```csharp
var1 = var2
```

此代碼可能會導致[副作用](https://en.wikipedia.org/wiki/Side_effect_\(computer_science\))。 副作用可能會通過更改應用的操作方式使調試更加困難。

首次輸入具有副作用的運算式僅計算一次。 之後，運算式在 **"監視"** 視窗中顯示為灰色，並禁用進一步評估。 工具提示或**值**列說明運算式會導致副作用。 您可以通過選擇值旁邊的刷新圖示來強制重新評估。

防止副作用指定的方法之一是關閉自動功能評估。 在**工具** > **選項** > **Debugging**調試 > **一般**中，取消選擇**啟用屬性計算和其他隱式函式呼叫**。

僅對於 C#，當關閉屬性或隱式函式呼叫的評估時，可以通過在 **"監視"** 視窗中將**ac**格式修改器添加到變數**Name**來強制評估。 請參閱[C# 中的格式指定器](../debugger/format-specifiers-in-csharp.md)。

## <a name="use-object-ids-in-the-watch-window-c-and-visual-basic"></a><a name="bkmk_objectIds"></a>在"監視"視窗中使用物件指示（C# 和視覺基本）

有時，您希望觀察特定物件的行為。 例如，您可能希望跟蹤本地變數引用的物件，該變數已不在範圍之內。 在 C# 和 Visual Basic 中，可以為參考型別的特定實例創建物件 I，並在 **"監視"** 視窗和中斷點條件下使用它們。 物件識別碼由 Common Language Runtime (CLR) 偵錯服務產生，會與物件建立關聯。

> [!NOTE]
> 物件指示創建不阻止物件被垃圾回收的弱引用。 它們僅針對目前的偵錯工作階段才有效。

在以下代碼中，`MakePerson()`該方法使用區域變數`Person`創建 一個變數：

```csharp
class Person
{
    public Person(string name)
    {
        Name = name;
    }
    public string Name { get; set; }
}

public class Program
{
    static List<Person> _people = new List<Person>();
    public static void Main(string[] args)
    {
        MakePerson();
        DoSomething();
    }

    private static void MakePerson()
    {
        var p = new Person("Bob");
        _people.Add(p);
    }

    private static void DoSomething()
    {
        // more processing
         Console.WriteLine("done");
    }
}
```

要找出`Person`方法中 的名稱，`DoSomething()`可以在`Person`**"監視"** 視窗中添加對物件識別碼 的引用。

1. 創建`Person`物件後，在代碼中設置中斷點。

1. 開始偵錯。

1. 當執行在中斷點暫停時，通過選擇 **"調試** > **Windows** > **區域變數**"打開 **"區域變數**"視窗。

1. 在 **"區域變數"** 視窗中，右鍵`Person`按一下變數並選擇 **"使物件識別碼**"。

   您應該在 **"區域變數"** 視窗中**$** 看到一個貨幣符號 （ ） 加上一個數位，該視窗是物件識別碼。

1. 通過按右鍵物件識別碼 並選擇"**添加監視"** 將物件識別碼 添加到 **"監視"** 視窗。

1. 在`DoSomething()`方法中設置另一個中斷點。

1. 繼續偵錯。 當`DoSomething()`執行在 方法中暫停時，"**監視"** 視窗將顯示`Person`該物件。

   > [!NOTE]
   > `Person.Name`如果要查看物件的屬性，如 ，必須通過選擇 **"工具** > **選項** > **調試** > **常規** > **啟用屬性"屬性計算和其他隱式函式呼叫**來啟用屬性計算。

## <a name="dynamic-view-and-the-watch-window"></a>動態視圖和監看視窗

某些指令碼語言（例如 JavaScript 或 Python）使用動態或[鴨子](https://en.wikipedia.org/wiki/Duck_typing)類型，.NET 版本 4.0 和更高版本支援在正常調試視窗中難以觀察到的物件。

**"監視"** 視窗將這些物件顯示為動態物件，這些物件是從實現<xref:System.Dynamic.IDynamicMetaObjectProvider>介面的類型創建的。 動態物件節點顯示動態物件的動態成員，但不允許編輯成員值。

要刷新**動態視圖**值，請選擇動態物件節點旁邊的[刷新圖示](#bkmk_refreshWatch)。

要僅顯示物件的**動態視圖**，請在 **"監視"** 視窗中的動態物件名稱之後添加**動態**格式指定器：

- 若為 C#：`ObjectName, dynamic`
- 若為 Visual basic：`$dynamic, ObjectName`

>[!NOTE]
>- 當您踏進下一行代碼時，C# 調試器不會自動重新評估**動態視圖中**的值。
>- 視覺化基本調試器會自動刷新通過**動態視圖**添加的運算式。
>- 評估**動態視圖**的成員可能有[副作用](https://en.wikipedia.org/wiki/Side_effect_\(computer_science\))。

**要插入將物件強制轉換為動態物件的新監視變數，請：**

1. 按右鍵**動態視圖**的任何子級。
1. 選擇 **"添加手錶**"。 成為`object.name``((dynamic) object).name`並顯示在新的 **"監視"** 視窗中。

調試器還會將物件的**動態視圖**子節點添加到 **"自動"** 視窗。 要打開 **"自動"** 視窗，請在調試期間選擇 **"調試** > **Windows** > **自動**"。

**動態視圖**還增強了 COM 物件的調試。 當調試器到達在**System.__ComObject**中包裝的 COM 物件時，它會為該物件添加**一個動態視圖**節點。

## <a name="observe-a-single-variable-or-expression-with-quickwatch"></a>使用 QuickWatch 觀察單個變數或運算式

您可以使用**QuickWatch**觀察單個變數。

例如，對於以下代碼：

```csharp
static void Main(string[] args)
{
    int a, b;
    a = 1;
    b = 2;
    for (int i = 0; i < 10; i++)
    {
        a = a + b;
    }
}
```

為了觀察變數`a`，

1. 在 `a = a + b;` 行上設定中斷點。

1. 開始偵錯。 執行在中斷點處暫停。

1. 在代碼中選擇`a`變數。

1. 選擇**調試** > **快速觀看**，按**Shift**+**F9**，或按右鍵並選擇 **"快速觀看**"。

   將顯示 **"快速監視"** 對話方塊。 變數`a`位於"**運算式"** 框中，**值**為**1**。

   ![快速觀察變數](../debugger/media/quickwatchvariable.png "快速觀察變數")

1. 要使用變數計算運算式，請在 **"運算式"** 框中鍵入運算式`a + b`，然後選擇 **"重計算**"。

   ![快速觀察運算式](../debugger/media/quickwatchexpression.png "快速觀察運算式")

1. 要將"**快速監視"** 中的變數或運算式添加到 **"監視"** 視窗，請選擇"**添加監視**"。

1. 選擇 **"關閉**"以關閉 **"快速監視"** 視窗。 **（QuickWatch**是一種強制回應對話方塊，因此只要它是打開的，您就無法繼續調試。

1. 繼續偵錯。 您可以在 **"監視"** 視窗中觀察變數。

## <a name="see-also"></a>另請參閱
- [什麼是偵錯？](../debugger/what-is-debugging.md)
- [偵錯技術和工具](../debugger/write-better-code-with-visual-studio.md)
- [首先查看調試](../debugger/debugger-feature-tour.md)
- [調試器視窗](../debugger/debugger-windows.md)
