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
ms.openlocfilehash: 944347f6afc371775afca1b58bae77271b60359c
ms.sourcegitcommit: a811f6a194ccd40d844e74e618d847df87c85c16
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 11/29/2018
ms.locfileid: "52621639"
---
# <a name="watch-variables-with-watch-windows-and-quickwatch"></a>監看式變數使用監看式視窗和快速監看式 

當您偵錯時，您可以使用**監看式**windows 並**快速監看式**監看變數和運算式。 在偵錯工作階段期間，才可以使用 windows。

**監看式**視窗可以顯示數個變數，偵錯時，一次。 **快速監看式**對話方塊顯示單一變數一次，而且必須關閉偵錯才能繼續。

如果這是您第一次您嘗試偵錯程式碼時，您可能想要讀取[修正 bug，藉由撰寫更好C#程式碼](../debugger/write-better-code-with-visual-studio.md)並[偵錯適用於徹底初學者](../debugger/debugging-absolute-beginners.md)再通過這篇文章。

## <a name="observe-variables-with-a-watch-window"></a>觀察 監看式視窗變數

您可以開啟多個**監看式** 視窗中，並觀察中的多個變數**監看式**視窗。 

例如，若要設定的值上的 監看式`a`， `b`，和`c`下列程式碼：

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

1. 上設定中斷點`c = a + b;`列按一下左邊界中，選取**偵錯** > **切換中斷點**，或按**F9**。
   
1. 開始偵錯選取綠色**開始**箭號或**偵錯** > **開始偵錯**，或按**F5**。 執行的中斷點處暫停。
   
1. 開啟**監看式**視窗中的選取**偵錯** > **Windows** > **監看式** >  **監看式 1**，或按下**Ctrl**+**Alt**+**W** > **1**.
   
   您可以開啟其他**監看式**視窗中的，選取 windows **2**， **3**，或**4**。
   
1. 在 **監看式**視窗中，選取空白資料列，並輸入變數`a`。 執行相同的動作`b`和`c`。
   
   ![監看變數](../debugger/media/watchvariables.png "WatchVariables")
   
1. 繼續選取偵錯**偵錯** > **逐步**或按下**F11**視前進。 變數值會在**監看式** 視窗變更為您逐一查看`for`迴圈。
   
>[!NOTE]
>僅限 c + + 
>- 您可能需要限定變數名稱或使用變數名稱的運算式的內容。 內容是函式、 原始程式檔或變數所在的模組。 如果您限定內容，請使用[內容運算子 （c + +）](../debugger/context-operator-cpp.md)中的語法**名稱**中**監看式**視窗。 
>  
>- 您可以將暫存器名稱和使用的變數名稱 **$\<註冊&nbsp;名稱 >** 或是 **@\<註冊&nbsp;名稱 >** 要**名稱**中**監看式**視窗。 如需詳細資訊，請參閱 [Pseudovariables](../debugger/pseudovariables.md)。

## <a name="use-expressions-in-a-watch-window"></a>在 監看式視窗中使用運算式

您可以觀察到任何有效的運算式在偵錯工具辨識**監看式**視窗。

例如，在上一節中的程式碼，您可以取得三個值的平均輸入`(a + b + c) / 3`中**監看式**視窗：

![監看運算式](../debugger/media/watchexpression.png "監看運算式")

運算式評估規則**監看式**視窗通常是在程式碼語言中的運算式評估規則相同。 如果運算式有語法錯誤，會預期相同的編譯器錯誤，如程式碼編輯器中所示。 例如，上述運算式中的錯字會產生此錯誤在**監看式**視窗：

![監看運算式錯誤](../debugger/media/watchexpressionerror.png "監看運算式錯誤")

中會有兩條波浪線圖示的圓形**監看式**視窗。 這個圖示表示偵錯工具不會評估運算式，因為潛在的跨執行緒相依性。 評估程式碼需要暫時執行應用程式中的其他執行緒，但通常是因為您處於中斷模式時，會停止您的應用程式中的所有執行緒。 允許暫時執行其他執行緒可以有未預期的影響，在您的應用程式與偵錯工具的狀態可能會忽略事件，例如中斷點和在這些執行緒的例外狀況。

### <a name="bkmk_refreshWatch"></a> 重新整理監看值

重新整理圖示 （循環箭號） 可能會出現在**監看式**評估運算式時的視窗。 重新整理圖示會指出錯誤或已過期的值。 

若要重新整理值，請選取 [重新整理] 圖示，或按空格鍵。 偵錯工具會嘗試重新評估運算式。 不過，您可能不想要或能夠重新評估運算式，根據為何未評估值。 

留在重新整理圖示，或請參閱**值**原因不評估運算式的資料行。 原因包括：

- 當評估運算式，如同先前的範例，就會發生錯誤。 逾時可能會發生，或變數可能會超出範圍。
  
- 運算式包含無法觸發副作用的應用程式中的函式呼叫。 請參閱[運算式的副作用](#bkmk_sideEffects)。
  
- 已停用的自動評估屬性和隱含函式呼叫。 
  
如果因為已停用的自動評估屬性和隱含函式呼叫，就會出現重新整理圖示，您可以啟用它藉由選取**啟用屬性評估及其他隱含函式呼叫**在**工具**  > **選項** > **偵錯** > **一般**。

若要示範如何使用重新整理圖示：

1. 在 **工具** > **選項** > **偵錯** > **一般**，清除  **啟用屬性評估及其他隱含函式呼叫**核取方塊。 
   
1. 輸入下列程式碼，然後在**監看式**視窗中，在 設定監看式`list.Count`屬性。 
   
   ```csharp
   static void Main(string[] args)
   {
       List<string> list = new List<string>();
       list.Add("hello");
       list.Add("goodbye");
   }
   ```
   
1. 開始偵錯。 **監看式**視窗會顯示類似下列訊息：
   
   ![重新整理監看式](../debugger/media/refreshwatch.png "重新整理監看式")
   
1. 若要重新整理值，請選取 [重新整理] 圖示，或按空格鍵。 偵錯工具會重新評估運算式。 

### <a name="bkmk_sideEffects"></a> 運算式的副作用 

評估某些運算式，可以變更變數的值，或會影響您的應用程式的狀態。 例如，評估下列運算式會變更 `var1`的值：

```csharp
var1 = var2
```

此程式碼可能會造成[副作用](https://en.wikipedia.org/wiki/Side_effect_\(computer_science\))。 副作用會使得偵錯更加困難藉由變更您的應用程式的運作的方式。

具有副作用的運算式會評估一次，當您第一次輸入它。 在那之後，運算式會出現在灰色**監看式**視窗中，並進一步評估已停用。 工具提示或**值**專欄說明運算式會造成副作用。 您可以選取值旁邊的 [重新整理] 圖示，以強制重新評估。

若要避免的副作用指定的一個方法是關閉自動函式評估。 在 **工具** > **選項** > **偵錯** > **一般**，取消選取**啟用屬性評估及其他隱含函式呼叫**。

針對C#，當屬性評估或隱含函式呼叫關閉時，您可以強制評估加**ac**格式修飾詞的變數**名稱**中**監看式**視窗。 請參閱 [Format specifiers in C#](../debugger/format-specifiers-in-csharp.md) (C# 中的格式規範)。

## <a name="bkmk_objectIds"></a> 在 [監看式] 視窗中使用物件識別碼 (C#和 Visual Basic)

有時您想要觀察特定物件的行為。 例如，您可能要追蹤所參考的本機變數之後，該變數已超出範圍的物件。 在 C# 和 Visual Basic 中，您可以針對參考型別的特定執行個體建立物件識別碼，並在 [監看式] 視窗和中斷點條件中加以使用。 物件識別碼由 Common Language Runtime (CLR) 偵錯服務產生，會與物件建立關聯。

> [!NOTE]
> 物件 Id 會建立不會阻止物件進行記憶體回收的弱式參考。 它們僅針對目前的偵錯工作階段才有效。

下列程式碼中，`MakePerson()`方法會建立`Person`使用本機變數： 

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

若要了解的名稱`Person`中`DoSomething()`方法，您可以加入參考`Person`中的物件識別碼**監看式**視窗。

1. 後面的程式碼中設定中斷點`Person`已建立物件。
   
1. 開始偵錯。
   
1. 當在中斷點暫停執行時開啟**區域變數**視窗中的選擇**偵錯** > **Windows** > **[區域變數]**.
   
1. 在 [**區域變數**] 視窗中，以滑鼠右鍵按一下`Person`變數，然後選取**設定物件 ID**。
   
   您應該會看到以貨幣符號 (**$**) 再加上數字**區域變數**視窗中，也就是物件識別碼。
   
1. 新增至的物件識別碼**監看式**視窗中的以滑鼠右鍵按一下 物件識別碼，然後選取**加入監看式**。
   
1. 在設定其他中斷點`DoSomething()`方法。
   
1. 繼續偵錯。 當執行暫停於要`DoSomething()`方法中，**監看式** 視窗會顯示`Person`物件。
   
   > [!NOTE]
   > 如果您想要查看物件的屬性，例如`Person.Name`，您必須啟用屬性評估選取**工具** > **選項** >  **偵錯** > **一般** > **啟用屬性評估及其他隱含函式呼叫**。

## <a name="dynamic-view-and-the-watch-window"></a>動態檢視和監看式視窗

某些指令碼語言 （例如 JavaScript 或 Python） 使用動態或[鴨子](https://en.wikipedia.org/wiki/Duck_typing)型別和.NET 4.0 或更新版本支援難以在一般的偵錯視窗觀察的物件。

**監看式** 視窗會顯示這些物件做為動態物件，從實作的型別建立<xref:System.Dynamic.IDynamicMetaObjectProvider>介面。 動態物件節點會顯示動態物件的動態成員，但不允許編輯成員值。 

若要重新整理**動態檢視**值，選取[重新整理圖示](#bkmk_refreshWatch)動態物件節點旁。 

若只要顯示**動態檢視**物件，請新增**動態**格式規範中的動態物件名稱之後**監看式**視窗：

- 若為 C#：`ObjectName, dynamic`
- 若為 Visual basic：`$dynamic, ObjectName`

>[!NOTE]
>- C#偵錯工具不會自動重新評估中的值**動態檢視**當您逐步執行至下一行程式碼。 
>- Visual Basic 偵錯工具會自動重新整理透過 新增運算式**動態檢視**。
>- 評估**動態檢視**的成員可能會有[副作用](https://en.wikipedia.org/wiki/Side_effect_\(computer_science\))。 

**若要插入新的監看式變數，會轉換成動態物件的物件：**
  
1. 以滑鼠右鍵按一下任何子系**動態檢視**。
1. 選擇**新增監看式**。 `object.name`會變成`((dynamic) object).name`而且會出現在新**監看式**視窗。

偵錯工具也會新增**動態檢視**之物件的子節點**自動變數**視窗。 若要開啟 **自動變數**視窗中的，偵錯期間，選取**偵錯** > **Windows** > **自動變數**。 

**動態檢視**也強化了 COM 物件的偵錯。 當偵錯工具取得 COM 物件包裝在**System.__ComObject**，它會新增**動態檢視**物件節點。

## <a name="observe-a-single-variable-or-expression-with-quickwatch"></a>觀察單一變數或快速監看式運算式

您可以使用**快速監看式**觀察單一變數。 

例如，如下列程式碼：

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

若要觀察`a`變數， 
   
1. 在 `a = a + b;` 行上設定中斷點。
   
1. 開始偵錯。 執行的中斷點處暫停。
   
1. 選取的變數`a`程式碼中。
   
1. 選取 **偵錯** > **快速監看式**，按下**Shift**+**F9**，或以滑鼠右鍵按一下，然後選取**快速監看式**。 
   
   **快速監看式**對話方塊隨即出現。 `a`變數是在**運算式**方塊**值**的**1**。
   
   ![快速監看式變數](../debugger/media/quickwatchvariable.png "快速監看式變數")
   
1. 若要評估的運算式中使用該變數，請輸入運算式這類`a + b`中**運算式**方塊中，然後選取**重新評估**。
   
   ![快速監看式運算式](../debugger/media/quickwatchexpression.png "快速監看式運算式")
   
1. 若要加入的變數或運算式，從**快速監看式**要**監看式**視窗中，選取**加入監看式**。
   
1. 選取 **關閉** 以關閉**快速監看式**視窗。 (**快速監看式**是強制回應對話方塊中，因此您無法繼續偵錯，只要已開啟。)
   
1. 繼續偵錯。 您可以觀察在變數**監看式**視窗。

## <a name="see-also"></a>另請參閱
 [什麼是偵錯？](../debugger/what-is-debugging.md)  
 [透過撰寫更好的 C# 程式碼來修正 Bug](../debugger/write-better-code-with-visual-studio.md)  
 [第一次查看偵錯](../debugger/debugger-feature-tour.md)[偵錯工具視窗](../debugger/debugger-windows.md)
