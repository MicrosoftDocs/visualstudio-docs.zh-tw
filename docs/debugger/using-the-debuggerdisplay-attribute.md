---
title: 使用 DebuggerDisplay 顯示自訂資訊 |Microsoft Docs
description: 使用 DebuggerDisplayAttribute 的實例來控制物件、屬性或欄位在偵錯工具變數視窗中顯示的方式。
ms.custom: SEO-VS-2020
ms.date: 01/09/2019
ms.topic: how-to
helpviewer_keywords:
- attributes, debugger
- DebuggerDisplay attribute
- DebuggerDisplayAttribute class
ms.assetid: f4eb7c76-af4e-493b-9ab6-9cb05949d9b3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1d846fd5e423ed17f7754260f169e32dbef5486b
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/13/2021
ms.locfileid: "98150752"
---
# <a name="tell-the-debugger-what-to-show-using-the-debuggerdisplay-attribute-c-visual-basic-f-ccli"></a>使用 DebuggerDisplay 屬性告訴偵錯工具要顯示的內容 (c #、Visual Basic、F #、c + +/CLI) 

<xref:System.Diagnostics.DebuggerDisplayAttribute> 控制物件、屬性或欄位在偵錯工具變數視窗中顯示的方式。 這個屬性可以適用於類型、委派、屬性、欄位和組件。 如果套用至基底類型，屬性也會套用至子類別。

`DebuggerDisplay` 屬性有單一引數，這是要在類型執行個體的 [值] 一欄中顯示的字串。 這個字串可以包含括號 (`{` 和 `}`)。 一對括號內的文字會評估為欄位、屬性或方法。

如果類別具有覆寫的 `ToString()` 方法，偵錯工具會使用覆寫的方法，而非預設的 `{<typeName>}`。 因此，如果您已覆寫 `ToString()` 方法，偵錯工具就會使用覆寫的方法，而非預設的`{<typeName>}`，而且您不需要使用 `DebuggerDisplay`。 若兩者都使用，`DebuggerDisplay` 屬性會優先於覆寫的 `ToString()` 方法。 `DebuggerDisplay`屬性也優先于 `ToString()` 子類別中的覆寫方法。

偵錯工具是否評估這個隱含 `ToString()` 呼叫取決於 [工具]/[ **選項]/[調試** 程式] 對話方塊中的使用者設定。

> [!IMPORTANT]
> 如果已在 [**工具]/[選項]/[調試** 程式] 對話方塊中選取 [**在變數視窗中顯示物件的原始結構**] 核取方塊，則會 `DebuggerDisplay` 忽略屬性。

> [!NOTE]
> 若為機器碼，只有在 c + +/CLI 程式碼中才支援此屬性。

下表說明 `DebuggerDisplay` 屬性的一些可能用法和範例輸出。

|屬性|出現在值資料行中的輸出|
|---------------| - |
|`[DebuggerDisplay("x = {x} y = {y}")]`<br /><br /> 用於具有 `x` 和 `y`欄位的類型。|`x = 5 y = 18`|
|`[DebuggerDisplay("String value is {getString()}")]`參數語法會因語言而有所不同。 因此，請小心使用。|`String value is [5, 6, 6]`|

`DebuggerDisplay` 也可以接受具名參數。

|參數|目的|
|----------------|-------------|
|`Name`, `Type`|這些參數會影響變數視窗的 [ **名稱** ] 和 [ **類型** ] 欄 (它們可以設定為與建構函式使用相同語法的字串)。過度使用或不當使用這些參數，會造成輸出混淆。|
|`Target`, `TargetTypeName`|指定屬性在組件層級使用時的目標類型。|

Autoexp.cs 檔案會在組件層級使用 DebuggerDisplay 屬性。 Autoexp.cs 檔案會決定 Visual Studio 用於 .NET 物件使用的預設展開 (Expansion)。 您可以檢查 autoexp.cs 檔案以取得如何使用 DebuggerDisplay 屬性的範例，或修改和編譯 autoexp.cs 檔案以變更預設展開 (Expansion)。 請務必先備份 autoexp.cs 檔案，再進行修改。

若要建置 autoexp.cs，請開啟 VS2015 的開發人員命令提示字元，然後執行下列命令

```cmd
cd <directory containing autoexp.cs>
csc /t:library autoexp.cs
```

對 autoexp.dll 所做的變更將會在下一個偵錯工作階段中選出。

## <a name="using-expressions-in-debuggerdisplay"></a>在 DebuggerDisplay 中使用運算式
雖然您可以在 DebuggerDisplay 屬性中使用大括號括住的一般運算式，但不建議採取這種做法。

DebuggerDisplay 中的一般運算式只能隱含存取目標類型之目前執行個體的 `this` 指標。 運算式無法存取別名、區域變數或指標。 如果運算式參考屬性 (Property)，則不會處理這些屬性 (Property) 中的屬性 (Attribute)。 例如，如果欄位 `count` 為 8，則 C# 程式碼 `[DebuggerDisplay("Object {count - 2}")]` 會顯示 `Object 6`。

在 DebuggerDisplay 中使用運算式可能導致下列問題：

- 評估運算式是偵錯工具中最昂貴的作業，而且每次顯示運算式時都會進行評估。 這可能會在逐步執行程式碼時導致效能問題。 例如，若集合或清單中的元素數目很大，則用於顯示其中值的複雜運算式執行速度可能會非常慢。

- 運算式是由使用目前堆疊框架語言的運算式評估工具進行評估，而不是由撰寫運算式之語言的評估工具進行評估。 這種情況可能會在語言不同時導致無法預測的結果。

- 評估運算式可能會變更應用程式的狀態。 例如，設定屬性值的運算式會改變執行程式碼中的屬性值。

  減少運算式評估可能出現之問題的其中一種方法，是建立私用屬性來執行作業並傳回字串。 這樣 DebuggerDisplay 屬性就可以顯示該私用屬性的值。 下列範例將實作這個模式：

```csharp
[DebuggerDisplay("{DebuggerDisplay,nq}")]
public sealed class MyClass
{
    public int count { get; set; }
    public bool flag { get; set; }
    private string DebuggerDisplay
    {
        get
        {
            return string.Format("Object {0}", count - 2);
        }
    }
}
```

"，Nq" 後置詞會指示運算式評估工具在顯示最終值時移除引號 (nq = no 引號) 。

## <a name="example"></a>範例
下列程式碼範例將示範如何使用 `DebuggerDisplay`搭配 `DebuggerBrowseable` 和 `DebuggerTypeProxy`。 在偵錯工具變數視窗中檢視時 (例如 [ **監看式** ] 視窗)，它會產生類似下面所示的展開：

|**名稱**|**ReplTest1**|**型別**|
|--------------|---------------|--------------|
|答案|"three"|object {string}|
|值|3|object {int}|

```csharp
[DebuggerDisplay("{value}", Name = "{key}")]
internal class KeyValuePairs
{
    private IDictionary dictionary;
    private object key;
    private object value;
    public KeyValuePairs(IDictionary dictionary, object key, object value)
    {
        this.value = value;
        this.key = key;
        this.dictionary = dictionary;
    }

    public object Key
    {
        get { return key; }
        set
        {
            object tempValue = dictionary[key];
            dictionary.Remove(key);
            key = value;
            dictionary.Add(key, tempValue);
        }
    }

    public object Value
    {
        get { return this.value; }
        set
        {
            this.value = value;
            dictionary[key] = this.value;
        }
    }
}

[DebuggerDisplay("{DebuggerDisplay,nq}")]
[DebuggerTypeProxy(typeof(HashtableDebugView))]
class MyHashtable
{
    public Hashtable hashtable;

    public MyHashtable()
    {
        hashtable = new Hashtable();
    }

    private string DebuggerDisplay { get { return "Count = " + hashtable.Count; } }

    private class HashtableDebugView
    {
        private MyHashtable myhashtable;
        public HashtableDebugView(MyHashtable myhashtable)
        {
            this.myhashtable = myhashtable;
        }

        [DebuggerBrowsable(DebuggerBrowsableState.RootHidden)]
        public KeyValuePairs[] Keys
        {
            get
            {
                KeyValuePairs[] keys = new KeyValuePairs[myhashtable.hashtable.Count];

                int i = 0;
                foreach (object key in myhashtable.hashtable.Keys)
                {
                    keys[i] = new KeyValuePairs(myhashtable.hashtable, key, myhashtable.hashtable[key]);
                    i++;
                }
                return keys;
            }
        }
    }
}
```

## <a name="see-also"></a>另請參閱

- [使用 DebuggerTypeProxy 屬性](../debugger/using-debuggertypeproxy-attribute.md)
- [建立受控物件的自訂檢視](../debugger/create-custom-views-of-managed-objects.md)
- [C# 中的格式規範](../debugger/format-specifiers-in-csharp.md)
- [使用偵錯工具顯示屬性增強偵錯功能](/dotnet/framework/debug-trace-profile/enhancing-debugging-with-the-debugger-display-attributes)
