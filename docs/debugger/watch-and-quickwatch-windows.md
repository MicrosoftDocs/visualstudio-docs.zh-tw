---
title: 在變數上設定監看式 |Microsoft Docs
description: 當您進行調試時，請參閱 Watch 和快速監看式中的變數和運算式。 Watch 可以顯示數個變數、只快速監看式，而且只在中斷時才顯示。
ms.custom: SEO-VS-2020, seodec18
ms.date: 10/11/2018
ms.topic: how-to
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
ms.openlocfilehash: d13ee6163ebe8cf0f706cbe95e7451c2ebc7c411
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/13/2021
ms.locfileid: "98149478"
---
# <a name="watch-variables-with-watch-windows-and-quickwatch"></a>使用監看式視窗和快速監看變數

在進行調試時，您可以使用 **[監看式]** 視窗和 [ **快速** 監看式] 來監看變數和運算式 只有在進行調試過程時，才可以使用 windows。

**監看** 式視窗可以在進行調試時，一次顯示數個變數。 [ **快速** 監看式] 對話方塊一次會顯示一個變數，且必須先關閉，才能繼續進行調試。

> [!NOTE]
> 如果這是您第一次嘗試進行程式碼的偵錯工具，您可能會想要在進行這篇文章之前，先閱讀絕對初學者和[調試](../debugger/write-better-code-with-visual-studio.md)[程式的偵錯工具](../debugger/debugging-absolute-beginners.md)。

## <a name="observe-variables-with-a-watch-window"></a>觀察具有監看式視窗的變數

您可以開啟多個 **[監看** 式] 視窗，並在 **[監看** 式] 視窗中觀察一個以上的變數。

例如，若要在 `a` `b` 下列程式碼中，對、和的值設定監看式 `c` ：

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

1. 在 `c = a + b;` 左邊界中按一下、選取 [ **Debug**  >  **切換中斷點**] 或按 **F9**，以在行上設定中斷點。

1. 選取綠色 **開始** 箭號或 **Debug**  >  **開始** 偵錯工具，或按 **F5**，開始進行偵錯工具。 執行會在中斷點暫停。

1. 選取 [ **Debug** Windows   >    >  **watch**  >  **watch 1**]，或按 **Ctrl** + **Alt** + **W**  >  **1** 以開啟 [監看式] 視窗。

   您可以選取 [windows **2**]、[ **3**] 或 [ **4**] 來開啟其他的 **監看** 式視窗。

1. 在 [ **監看** 式] 視窗中，選取空白資料列，然後輸入 variable `a` 。 對和進行相同的動作 `b` `c` 。

   ![監看式變數](../debugger/media/watchvariables.png "WatchVariables")

1. 依需要選取 [ **Debug**  >  **Step** ] 或按 **F11** 鍵來繼續進行偵錯工具。 當您逐一查看迴圈時，[ **監看** 式] 視窗中的變數值會變更 `for` 。

>[!NOTE]
>僅適用于 c + +，
>- 您可能需要限定變數名稱的內容，或使用變數名稱的運算式。 內容是變數所在的函式、原始程式檔或模組。 如果您必須限定內容，請在 [**監看** 式] 視窗的 **名稱** 中使用 [內容運算子 (c + +)](../debugger/context-operator-cpp.md)語法。
>
>- 您可以使用或在 [ **$\<register&nbsp;name>** **@\<register&nbsp;name>** **監看** 式] 視窗中的 **名稱** 加入暫存器名稱和變數名稱。 如需詳細資訊，請參閱 [Pseudovariables](../debugger/pseudovariables.md)。

## <a name="use-expressions-in-a-watch-window"></a>在監看式視窗中使用運算式

您可以在 [ **監看** 式] 視窗中觀察偵錯工具所能辨識的任何有效運算式。

例如，針對上一節中的程式碼，您可以 `(a + b + c) / 3` 在 [ **監看** 式] 視窗中輸入，來取得三個值的平均值：

![監看運算式](../debugger/media/watchexpression.png "監看運算式")

在 [ **監看** 式] 視窗中評估運算式的規則，通常與在程式碼語言中用來評估運算式的規則相同。 如果運算式有語法錯誤，則會預期程式碼編輯器中的相同編譯器錯誤。 例如，上述運算式中的打字錯誤會在 [ **監看** 式] 視窗中產生這個錯誤：

![監看運算式錯誤](../debugger/media/watchexpressionerror.png "監看運算式錯誤")

具有兩條波浪線圖示的圓形可能會出現在 [ **監看** 式] 視窗中。 此圖示表示偵錯工具不會評估運算式，因為可能的跨執行緒相依性。 評估程式碼需要您應用程式中的其他執行緒暫時執行，但因為您處於中斷模式，所以您應用程式中的所有線程通常會停止。 允許其他執行緒暫時執行可能會對您的應用程式狀態造成非預期的影響，而偵錯工具可能會忽略這些執行緒上的事件，例如中斷點和例外狀況。

::: moniker range=">= vs-2019" 
## <a name="search-in-the-watch-window"></a>在監看式視窗中搜尋

您可以使用每個視窗上方的搜尋列，在 [ **監看** 式] 視窗的 [名稱]、[值] 和 [類型] 欄中搜尋關鍵字。 按 ENTER 鍵或選取其中一個箭號以執行搜尋。 若要取消進行中的搜尋，請選取搜尋列中的 "x" 圖示。

使用向左和向右箭號 (Shift + F3 和 F3 分別) ，以流覽找到的相符專案。

![在 [監看式] 視窗中搜尋](../debugger/media/ee-search-watch.png "在 [監看式] 視窗中搜尋")

若要讓您的搜尋更多或更少，請使用 [**監看** 式] 視窗頂端的 [**更深入搜尋**] 下拉式清單，選取您要搜尋到嵌套物件的深度層級。 

## <a name="pin-properties-in-the-watch-window"></a>釘選監看式視窗中的屬性

>[!NOTE]
> .NET Core 3.0 或更高版本支援此功能。

您可以使用 [ **可釘選屬性** ] 工具，在監看式視窗中快速檢查物件的屬性。  若要使用此工具，請將滑鼠停留在屬性上，然後選取出現的釘選圖示，或按一下滑鼠右鍵，然後在產生的內容功能表中選取 [ **釘選成員** ] 選項。  這會將該屬性反升到物件之屬性清單的最上方，而屬性名稱和值會顯示在 [ **值** ] 資料行中。  若要取消釘選屬性，請再次選取 [釘選] 圖示，或在內容功能表中選取 [取消釘選 **成員** ] 選項。

![釘選監看式視窗中的屬性](../debugger/media/basic-pin-watch.gif "釘選監看式視窗中的屬性")

在監看式視窗中查看物件的屬性清單時，您也可以切換屬性名稱，並篩選出未釘選的屬性。  您可以選取 [監看式] 視窗上方工具列中的按鈕來存取這兩個選項。

::: moniker-end

### <a name="refresh-watch-values"></a><a name="bkmk_refreshWatch"></a> 重新整理監看值

在評估運算式時，[ **監看** 式] 視窗中會出現重新整理圖示 (圓形箭號) 。 重新整理圖示表示錯誤或已過期的值。

若要重新整理值，請選取 [重新整理] 圖示，或按下空格鍵。 偵錯工具會嘗試重新評估運算式。 不過，您可能不想要或無法重新評估運算式，這取決於未評估值的原因。

將滑鼠停留在重新整理圖示上，或查看 **值** 資料行以找出運算式未評估的原因。 原因包括：

- 評估運算式時發生錯誤，如先前的範例所示。 可能會發生超時，或變數可能超出範圍。

- 運算式有可能會在應用程式中觸發副作用的函式呼叫。 請參閱 [運算式](#bkmk_sideEffects)的副作用。

- 屬性的自動評估和隱含函式呼叫已停用。

如果出現重新整理圖示是因為屬性的自動評估和隱含函式呼叫已停用，您可以在 [**工具** 選項] 中選取 [**啟用屬性評估及其他隱含函式呼叫**] 來啟用它  >    >    >  ****。

若要示範如何使用重新整理圖示：

1. 在 [**工具**  >  **選項**] 的  >    >  **[一般**] 選項中，清除 [**啟用屬性評估及其他隱含函式呼叫**] 核取方塊。

1. 輸入下列程式碼，然後在 [ **監看** 式] 視窗中，設定屬性的監看式 `list.Count` 。

   ```csharp
   static void Main(string[] args)
   {
       List<string> list = new List<string>();
       list.Add("hello");
       list.Add("goodbye");
   }
   ```

1. 開始偵錯。 [ **監看** 式] 視窗會顯示類似下列的訊息：

   ![重新整理監看](../debugger/media/refreshwatch.png "重新整理監看")

1. 若要重新整理值，請選取 [重新整理] 圖示，或按下空格鍵。 偵錯工具會重新評估運算式。

### <a name="expression-side-effects"></a><a name="bkmk_sideEffects"></a> 運算式的副作用

評估一些運算式可能會變更變數的值，否則會影響應用程式的狀態。 例如，評估下列運算式會變更 `var1`的值：

```csharp
var1 = var2
```

這段程式碼可能會造成 [副作用](https://en.wikipedia.org/wiki/Side_effect_\(computer_science\))。 副作用可能會變更應用程式的運作方式，讓偵錯工具更困難。

具有副作用的運算式只會在您第一次輸入時評估一次。 之後，運算式在 [ **監看** 式] 視窗中會顯示為灰色，並停用進一步的評估。 [工具提示] 或 [ **值** ] 資料行說明運算式會造成副作用。 您可以選取值旁邊顯示的重新整理圖示，以強制重新評估。

防止產生副作用的其中一種方法是關閉自動函式評估。 在 [**工具**  >  **選項**] 的  >    >  **[一般**] 選項中，取消選取 [**啟用屬性評估及其他隱含函式呼叫**]。

僅限 c #，當關閉屬性評估或隱含函式呼叫時，您可以在 [**監看** 式] 視窗中將 [ **ac** 格式修飾詞] 新增至變數 **名稱**，藉以強制評估。 請參閱 [c # 中的格式](../debugger/format-specifiers-in-csharp.md)規範。

## <a name="use-object-ids-in-the-watch-window-c-and-visual-basic"></a><a name="bkmk_objectIds"></a> 使用監看式視窗 (c # 和 Visual Basic 中的物件識別碼) 

有時候您會想要觀察特定物件的行為。 例如，您可能想要在變數超出範圍之後，追蹤區域變數所參考的物件。 在 c # 和 Visual Basic 中，您可以針對參考型別的特定實例建立物件識別碼，並在 [ **監看** 式] 視窗和中斷點條件中使用它們。 物件識別碼由 Common Language Runtime (CLR) 偵錯服務產生，會與物件建立關聯。

> [!NOTE]
> 物件識別碼會建立弱式參考，而不會防止物件被垃圾收集。 它們僅針對目前的偵錯工作階段才有效。

在下列程式碼中， `MakePerson()` 方法會 `Person` 使用本機變數建立：

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

若要 `Person` 在方法中找出的名稱 `DoSomething()` ，您可以 `Person` 在 [ **監看** 式] 視窗中加入物件識別碼的參考。

1. 在建立物件之後的程式碼中設定中斷點 `Person` 。

1. 開始偵錯。

1. 當執行在中斷點暫停時，請選擇 [ **Debug**  >  **Windows**  >  **區域變數**] 來開啟 [區域變數] 視窗。

1. 在 [ **區域變數** ] 視窗中，以滑鼠右鍵按一下 `Person` 變數，然後選取 [ **建立物件識別碼**]。

   您應該會 **$** 在 [ **區域變數** ] 視窗中看到貨幣符號 () 加上數位，也就是物件識別碼。

1. 以滑鼠右鍵按一下物件識別碼，然後選取 [**新增監看** 式]，將物件識別碼新增至 [**監看** 式] 視窗。

1. 在方法中設定另一個中斷點 `DoSomething()` 。

1. 繼續偵錯。 當執行在方法中暫停時 `DoSomething()` ，[ **監看** 式] 視窗會顯示 `Person` 物件。

   > [!NOTE]
   > 如果您想要查看物件的屬性，例如 `Person.Name` ，您必須選取 [**工具**  >  **選項**]、  >    >  **[一般]、[**  >  **啟用屬性評估及其他隱含函式呼叫**] 來啟用屬性評估。

## <a name="dynamic-view-and-the-watch-window"></a>動態視圖和監看式視窗

某些指令碼語言 (例如，JavaScript 或 Python) 使用 [動態或打字](https://en.wikipedia.org/wiki/Duck_typing) 型別，而 .net 4.0 版和更新版本則支援在正常的偵錯工具視窗中不容易觀察到的物件。

[ **監看** 式] 視窗會將這些物件顯示為動態物件，這些物件是從執行介面的型別所建立 <xref:System.Dynamic.IDynamicMetaObjectProvider> 。 動態物件節點會顯示動態物件的動態成員，但不允許編輯成員值。

若要重新整理 **動態視圖** 值，請選取動態物件節點旁的重新整理 [圖示](#bkmk_refreshWatch) 。

若只要顯示物件的 **動態視圖**，請在 [**監看** 式] 視窗中的動態物件名稱之後加入 **動態** 格式規範：

- 若為 C#：`ObjectName, dynamic`
- 若為 Visual basic：`$dynamic, ObjectName`

>[!NOTE]
>- 當您逐步執行到下一行程式碼時，c # 偵錯工具不會自動重新評估 **動態視圖** 中的值。
>- Visual Basic 偵錯工具會自動重新整理透過 **動態視圖** 加入的運算式。
>- 評估 **動態視圖** 的成員可能有 [副作用](https://en.wikipedia.org/wiki/Side_effect_\(computer_science\))。

**若要插入新的監看式變數，將物件轉換成動態物件：**

1. 以滑鼠右鍵按一下 **動態視圖** 的任何子系。
1. 選擇 [ **新增監看式]**。 `object.name` `((dynamic) object).name` 隨即出現，並出現在新的 **[監看** 式] 視窗中。

偵錯工具也 **會在 [自動變數] 視窗** 中加入物件的 **動態視圖** 子節點。 若 **要在調試期間開啟 [自動** 變數] 視窗，請選取 [ **Debug**  >  **Windows** 自動變數]  >  ****。

**動態視圖** 也增強了 COM 物件的偵錯工具。 當偵錯工具到達包裝在 **System.__ComObject** 中的 COM 物件時，它會加入物件的 **動態視圖** 節點。

## <a name="observe-a-single-variable-or-expression-with-quickwatch"></a>使用 [快速監看式] 觀察單一變數或運算式

您可以使用 [ **快速** 監看式] 來觀察單一變數。

例如，針對下列程式碼：

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

若要觀察 `a` 變數，

1. 在 `a = a + b;` 行上設定中斷點。

1. 開始偵錯。 執行會在中斷點暫停。

1. `a`在程式碼中選取變數。

1. 選取 [ **Debug** 快速監看式]  >  ****、按 **Shift** + **F9**，或按一下滑鼠右鍵並選取 [**快速** 監看式]

   [ **快速** 監看式] 對話方塊隨即出現。 `a`變數位於 [**運算式**] 方塊中，**值** 為 **1**。

   ![快速監看式變數](../debugger/media/quickwatchvariable.png "快速監看式變數")

1. 若要使用變數來評估運算式，請 `a + b` 在 [ **運算式** ] 方塊中輸入運算式，例如，然後選取 [重新 **評估**]。

   ![快速監看式運算式](../debugger/media/quickwatchexpression.png "快速監看式運算式")

1. 若要從 [**快速** 監看式] 將變數或運算式新增至 [**監看** 式] 視窗，請選取 [**新增**

1. 選取 [ **關閉** ] 以關閉 [ **快速** 監看式] 視窗。  ([ **快速** 監看式] 是強制回應對話方塊，所以只要開啟它，就不能繼續進行偵錯工具 ) 

1. 繼續偵錯。 您可以觀察 [ **監看** 式] 視窗中的變數。

## <a name="see-also"></a>另請參閱
- [什麼是偵錯？](../debugger/what-is-debugging.md)
- [偵錯技術和工具](../debugger/write-better-code-with-visual-studio.md)
- [先查看調試](../debugger/debugger-feature-tour.md)
- [偵錯工具視窗](../debugger/debugger-windows.md)
