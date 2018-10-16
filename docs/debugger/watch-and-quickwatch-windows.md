---
title: 在 Visual Studio 中的變數設定監看式 |Microsoft Docs
ms.custom: H1Hack27Feb2017
ms.date: 10/11/2018
ms.technology: vs-ide-debug
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ad08799c0dce3792e096291dfaf62d52e2515df4
ms.sourcegitcommit: 48bc8492973e93612e5afaba3b47d0f98aecf97c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2018
ms.locfileid: "49325012"
---
# <a name="set-a-watch-on-variables-using-the-watch-and-quickwatch-windows-in-visual-studio"></a>在使用監看式] 和 [快速監看式的視窗，在 Visual Studio 中的變數設定監看式

當您偵錯時，您可以使用**監看式**並**快速監看式**windows 監看變數和運算式。  其差異在於 [監看式]  視窗可以顯示數個變數，而 [快速監看式]  視窗一次僅可顯示單一變數。

在偵錯工作階段期間，才可以使用 windows。 若要開啟 **監看式** 視窗中，選擇**偵錯** > **Windows** > **監看式**，然後選擇  **監看式 1**，**監看式 2**，**監看式 3**，或**監看式 4**。 若要開啟 [**快速監看式**] 視窗中，請以滑鼠右鍵按一下變數，然後選擇**快速監看式**，或選取**偵錯** > **快速監看式**.

## <a name="observe-variables-with-the-watch-window"></a>觀察 監看式視窗變數

您可以觀察到多個變數**監看式**視窗。 例如，如果您有下列的程式碼：

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

新增三個變數的值**監看式**視窗，如下所示：

1. 選取`c = a + b;`列。

2. 設定中斷點 (藉由選擇**偵錯** > **切換中斷點**或按下 F9)。

3. 開始偵錯 (F5)。 執行會在中斷點停止。

4. 開啟**監看式** 視窗 (藉由選擇**偵錯** > **Windows** > **監看式** >  **監看式 1**，或按 Ctrl + Alt + W，1)。

5. 選取空白資料列，然後輸入變數`a`。 然後執行相同的動作變數`b`和`c`。

   ![監看變數](../debugger/media/watchvariables.png "WatchVariables")

6. 繼續按 f11 鍵，視需要進入偵錯工具偵錯。

您應會發現變數值隨著您逐一查看 `for` 迴圈而變更。

如果您在撰寫原生程式碼中，您有時可能需要限定變數名稱，或是具有變數名稱的運算式的內容。 內容是變數所在的函式、原始程式檔和模組。 如果您有限定內容，您可以使用內容運算子語法。 如需詳細資訊，請參閱 <<c0> [ 內容運算子 （c + +）](../debugger/context-operator-cpp.md)。

## <a name="observe-expressions-with-the-watch-window"></a>觀察 [監看式] 視窗使用的運算式

現在我們來試試改用運算式。 您可以加入偵錯工具所能辨識的任何有效運算式。

比方說，如果您在上一節中列出的程式碼，您可以使用此運算式來取得三個值的平均值：

![監看運算式](../debugger/media/watchexpression.png "WatchExpression")

運算式評估規則**監看式**視窗通常會與您的程式碼撰寫語言的運算式評估規則相同。 如果您的運算式有語法錯誤，預期您會看到程式碼編輯器中的相同編譯器錯誤。 以下為範例：

![監看運算式錯誤](../debugger/media/watchexpressionerror.png "WatchExpressionError")

## <a name="bkmk_refreshWatch"></a> 重新整理已過期的監看值

在評估運算式時，重新整理圖示 （循環箭號） 可能會出現**監看式**視窗。 如果您已關閉屬性評估 (藉由選擇**工具** > **選項** > **偵錯** >  **一般**，然後清除**啟用屬性評估及其他隱含函式呼叫**)，而且也撰寫了下列程式碼：

```csharp
static void Main(string[] args)
{
    List<string> list = new List<string>();
    list.Add("hello");
    list.Add("goodbye");
}

```

您若應該會看到如下圖所示的項目上設定監看式`Count`清單屬性：

![RefreshWatch](../debugger/media/refreshwatch.png "RefreshWatch")

上圖顯示的錯誤或已過期的值。 您通常會重新整理值選取圖示，但在某些情況下您可能不想要重新整理它。 首先，您需要知道為何沒有評估值。

工具提示會提供資訊如果您指向圖示不評估運算式的原因。 如果出現環繞箭號，不被評估運算式，其中一個原因如下：

- 當評估運算式時發生錯誤。 例如，發生逾時或變數超出範圍。

- 運算式具有函式呼叫，可能會觸發應用程式中的副作用 (請參閱[副作用和運算式](#bkmk_sideEffects)區段)。

- 您已關閉的屬性自動評估和隱含函式會呼叫偵錯工具 (選擇**工具** > **選項** > **偵錯** > **一般**，然後清除**啟用屬性評估及其他隱含函式呼叫**)。 無法自動評估運算式然後。

若要重新整理值，請選取 [重新整理] 圖示，或按空格鍵。 偵錯工具會嘗試重新評估運算式。 因為屬性及其他隱含函式呼叫的自動評估已關閉，可能會出現重新整理圖示。 在此情況下，偵錯工具可以評估的運算式。

可能會出現圖示，類似螺紋的兩條波浪線的圓形。 這個圖示表示偵錯工具不會評估運算式，因為潛在的跨執行緒相依性。 也就是說，若要評估程式碼，需要暫時執行應用程式中的其他執行緒。 當您處於中斷模式時，通常會停止應用程式中的所有執行緒。 允許暫時執行其他執行緒可能會對程式的狀態造成無法預期的結果，且可能導致偵錯工具忽略中斷點之類的事件，並在這些執行緒中擲回例外狀況。

## <a name="bkmk_sideEffects"></a> 副作用和運算式

評估某些運算式可能會變更變數的值，或是影響程式的狀態。 例如，評估下列運算式會變更 `var1`的值：

```csharp
var1 = var2
```

此程式碼可能會造成[副作用](https://en.wikipedia.org/wiki/Side_effect_\(computer_science\))。 副作用會變更程式運作的方式，導致偵錯更加困難。

已知有副作用的運算式會評估一次，當您第一次輸入它。 進一步評估都會停用。 您可以手動選取值旁邊的更新圖示覆寫此行為。

避免所有副作用的一種方法是關閉自動函式評估 (藉由選擇**工具** > **選項** > **偵錯** > **一般**，然後清除**啟用屬性評估及其他隱含函式呼叫**)。

當關閉屬性評估或隱含函式呼叫時，您可以使用 **ac** 格式修飾詞 (僅適用 C#) 強制評估。 請參閱[格式規範，在 C#](../debugger/format-specifiers-in-csharp.md)。

## <a name="bkmk_objectIds"></a> 在 [監看式] 視窗 （C# 和 Visual Basic） 中使用物件識別碼

有時候您想要觀察特定物件的行為。 例如，您可能要追蹤所參考的本機變數之後，該變數已超出範圍的物件。 在 C# 和 Visual Basic 中，您可以建立參考類型的特定執行個體的物件識別碼，並使用它們**監看式**視窗和中斷點條件中。 物件 ID 是由 Common Language Runtime (CLR) 偵錯服務所產生並與物件相關聯。

> [!NOTE]
> 物件 Id 會建立不會阻止物件進行記憶體回收的弱式參考。 它們僅針對目前的偵錯工作階段才有效。

在下列程式碼，其中一種方法會建立`Person`使用本機變數，但您想要了解什麼`Person`的名稱位於不同的方法：

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

您可以在 [監看式] `Person`**視窗中將參考加入這個** 物件，如下所示：

1. 選取的行中的程式碼，在建立物件，就會發生。

2. 設定中斷點 (藉由選擇**偵錯** > **切換中斷點**或按下 F9)。

3. 開始偵錯。

4. 當在中斷點停止執行時，開啟**區域變數** 視窗 (藉由選擇**偵錯** > **Windows** > **區域變數**)，以滑鼠右鍵按一下變數，然後選取**設定物件 ID**。

   您應該會看到以貨幣符號 (**$**) 再加上數字**區域變數**視窗中，也就是物件識別碼。

   > [!NOTE]
   > 如果您想要查看物件的屬性，例如`Person.Name`，您必須藉由選擇啟用屬性評估**工具** > **選項** >  **偵錯** > **一般**，然後設定**啟用屬性評估及其他隱含函式呼叫**。

5. 新增至的物件識別碼**監看式**視窗中的貨幣符號和數字，以滑鼠右鍵按一下，然後選擇**加入監看式**。

6. 設定中斷點，您想要觀察物件的行為。  在上述程式碼中，這可能會在`DoSomething()`方法。

7. 繼續偵錯。 執行時停止`DoSomething()`方法中，**監看式** 視窗會顯示`Person`物件。

## <a name="use-registers-in-the-watch-window-c-only"></a>使用暫存器中監看式視窗 （僅 c + +）

您可以將暫存器名稱和使用的變數名稱 **$\<註冊&nbsp;名稱 >** 或是 **@\<註冊&nbsp;名稱 >** 偵錯原生程式碼時。 如需詳細資訊，請參閱 [Pseudovariables](../debugger/pseudovariables.md)。

## <a name="dynamic-view-and-the-watch-window"></a>動態檢視和監看式視窗

某些指令碼語言 （例如 JavaScript 或 Python） 使用動態或[typing](https://en.wikipedia.org/wiki/Duck_typing)，和.NET 語言 （4.0 或更新版本） 支援物件很難正常的偵錯視窗觀察的因為它們可能有執行階段屬性和方法，所以無法顯示。

**監看式** 視窗會顯示動態物件，這建立從型別可實作<xref:System.Dynamic.IDynamicMetaObjectProvider>介面。 偵錯工具顯示此物件時，請加入一個特殊**動態檢視**如果您開啟的物件名稱的子節點**自動變數**視窗 (藉由選擇**偵錯** >  **Windows** > **[自動變數]**)。 此節點會顯示動態物件的動態成員，但不允許編輯成員值。

若要插入新的監看式變數，會轉換成動態物件的物件：

1. 以滑鼠右鍵按一下任何子系**動態檢視**。
2. 選擇**新增監看式**。 然後`object.name`會變成`((dynamic) object).name`。

評估 [動態檢視]  的成員時可能有副作用。 如需副作用為何的說明，請參閱 <<c0> [ 副作用和運算式](#bkmk_sideEffects)一節。 適用於 C# 中，偵錯工具不會自動重新評估中顯示的值**動態檢視**當您逐步執行至新的程式碼行。 若是 Visual Basic，則會自動重新整理透過 [動態檢視]  加入的運算式。

如需有關如何重新整理的指示**動態檢視**值，請參閱[過期的重新整理監看值](#bkmk_refreshWatch)一節。

如果您想要只顯示**動態檢視**物件，您可以使用**動態**格式規範，在**監看式**視窗：

- C#: `ObjectName, dynamic`
- Visual Basic：`$dynamic, ObjectName`

[動態檢視]  也強化了 COM 物件的偵錯體驗。 當偵錯工具取得 COM 物件包裝在**System.__ComObject**，它會新增**動態檢視**物件節點。

## <a name="observe-a-single-variable-or-expression-with-quickwatch"></a>觀察單一變數或快速監看式運算式

您可以使用 [快速監看式]  視窗觀察單一變數。 例如，如果您有下列的程式碼：

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

您可以觀察中的變數**快速監看式**視窗，如下所示：

1. 在 `a = a + b;` 行上設定中斷點。

2. 開始偵錯。 執行會在中斷點停止。

3. 選取的變數`a`。

4. 選擇**偵錯** > **快速監看式**或按**Shift + F9**。 **快速監看式** 視窗隨即出現。 在 [**值**] 方塊中，`a`變數會顯示值為 1。

   ![快速監看式變數](../debugger/media/quickwatchvariable.png "QuickWatchVariable")

   若要評估的運算式中使用該變數，請輸入運算式這類`a + b`要**運算式**方塊，然後按一下**重新評估**。

   ![快速監看式運算式](../debugger/media/quickwatchexpression.png "QuickWatchExpression")

   若要加入的變數或運算式**監看式**從視窗**快速監看式**，選擇**加入監看式**。

   > [!NOTE]
   > **快速監看式**視窗是強制回應對話方塊視窗中，因此您無法繼續偵錯，只要已開啟。

5. 關閉 [快速監看式]  視窗。 現在，您就可以一邊觀察 [監看式] **視窗中將參考加入這個** 視窗。

## <a name="see-also"></a>另請參閱

[偵錯工具視窗](../debugger/debugger-windows.md)
