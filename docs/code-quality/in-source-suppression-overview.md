---
title: 隱藏程式碼分析警告
ms.date: 08/03/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- source suppression, code analysis
- code analysis, source suppression
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.openlocfilehash: 1e90de7acf13ca28a20a35aa3ad3e70f58780279
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/03/2018
ms.locfileid: "39513042"
---
# <a name="suppress-code-analysis-warnings"></a>隱藏程式碼分析警告

它通常是用於指出警告不適用。 這表示小組成員檢閱的程式碼，而且可以隱藏警告。 來源隱藏項目 (ISS) 使用<xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute>屬性隱藏警告。 屬性可以放接近產生警告的程式碼片段。 您可以加入<xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute>屬性至原始程式檔中輸入，或者您可以使用捷徑功能表上的警告中**錯誤清單**自動將它加入。

<xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute>屬性是在編譯時期定義 CODE_ANALYSIS 編譯的符號時，才會包含您的 managed 程式碼組件的 IL 中繼資料中的條件式屬性。

在 C + + /cli CLI，使用巨集 CA\_抑制\_訊息或 CA\_GLOBAL\_SUPPRESS_MESSAGE 標頭檔中的新增屬性。

> [!NOTE]
> 您不應該在發行組建中，使用在原始程式檔的隱藏項目，以避免不小心傳送來源在隱藏項目中繼資料。 此外，在原始程式檔隱藏項目處理成本，因為您的應用程式的效能可能會降低。

> [!NOTE]
> 如果您將專案移轉至 Visual Studio 2017 時，可能會突然面臨大量程式碼分析警告。 來自這些警告[Roslyn 分析器](roslyn-analyzers-overview.md)。 如果您尚未準備好，修正警告，您就可以隱藏所有人都選擇**分析** > **執行程式碼分析和隱藏作用中問題**。
>
> ![執行程式碼分析並隱藏在 Visual Studio 中的問題](media/suppress-active-issues.png)

## <a name="suppressmessage-attribute"></a>SuppressMessage 屬性

當您選擇**抑制**從操作功能表或以滑鼠右鍵按一下功能表中的程式碼分析警告**錯誤清單**、<xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute>屬性會加入程式碼中，或專案的全域隱藏項目檔案。

<xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute>屬性具有下列格式：

```vb
<Scope:SuppressMessage("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")>
```

```csharp
[Scope:SuppressMessage("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")]
```

```cpp
CA_SUPPRESS_MESSAGE("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")
```

屬性的屬性包括：

- **類別目錄**-規則定義所在的類別。 如需程式碼分析規則類別的詳細資訊，請參閱[Managed 程式碼警告](../code-quality/code-analysis-for-managed-code-warnings.md)。

- **CheckId** -規則的識別碼。 支援包括同時短期和長期的規則識別項的名稱。 簡短名稱是 CAXXXX;CAXXXX:FriendlyTypeName 長的名稱。

- **理由**-用來記錄原因隱藏訊息的文字。

- **MessageId** -每個訊息發生問題的唯一識別碼。

- **範圍**-在其要隱藏警告的目標。 如果未指定目標，則會將它設定為屬性的目標。 支援的範圍包括下列各項：

    - Module

    - 命名空間

    - 資源

    - 類型

    - 成員

- **目標**-識別項，用來指定在其要隱藏警告的目標。 它必須包含完整項目名稱。

## <a name="suppressmessage-usage"></a>SuppressMessage 使用量

程式碼分析警告會隱藏的層級<xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute>屬性會套用。 例如，屬性可以套用在組件、 模組、 類型、 成員或參數層級。 的目的是緊密結合的程式碼的隱藏項目資訊發生違規的位置。

一般格式的隱藏項目包含規則的類別和規則識別項，其中包含規則名稱的選擇性人們可讀取表示。 例如: 

`[SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]`

如果有最小化在原始程式檔隱藏項目中繼資料的嚴格的效能考量，就可以省略 「 規則名稱。 規則類別和其規則識別碼一起構成夠唯一的規則識別項。 例如: 

`[SuppressMessage("Microsoft.Design", "CA1039")]`

基於可維護性，不建議省略之規則的名稱。

## <a name="suppress-selective-violations-within-a-method-body"></a>隱藏在方法主體中的選擇性違規

隱藏項目屬性可以套用至方法，但不能在方法主體中內嵌。 這表示會隱藏所有違規的特定規則，如果您新增<xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute>屬性加入方法。

在某些情況下，您可能想要隱藏的違規情形，例如特定執行個體，以便未來的程式碼不會自動從程式碼分析規則中免除。 某些程式碼分析規則可讓您可以使用`MessageId`屬性<xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute>屬性。 一般情況下，傳統規則違規 （本機變數或參數） 的特定符號尊重`MessageId`屬性。 [CA1500:VariableNamesShouldNotMatchFieldNames](../code-quality/ca1500-variable-names-should-not-match-field-names.md)舉例說明這樣的規則。 不過，傳統的規則，可執行程式碼 （非符號） 的違規不遵守`MessageId`屬性。 此外，.NET 編譯器平台 ("Roslyn") 分析器不遵守`MessageId`屬性。

若要隱藏特定符號規則的違規情形，指定的符號名稱`MessageId`屬性<xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute>屬性。 下列範例示範具有兩個違規的程式碼[CA1500:VariableNamesShouldNotMatchFieldNames](../code-quality/ca1500-variable-names-should-not-match-field-names.md)&mdash;另一個用於`name`變數，另一個用於`age`變數。 只有違反`age`符號會隱藏。

```vb
Public Class Animal
    Dim age As Integer
    Dim name As String

    <CodeAnalysis.SuppressMessage("Microsoft.Maintainability", "CA1500:VariableNamesShouldNotMatchFieldNames", MessageId:="age")>
    Sub PrintInfo()
        Dim age As Integer = 5
        Dim name As String = "Charlie"

        Console.WriteLine("Age {0}, Name {1}", age, name)
    End Sub

End Class
```

```csharp
public class Animal
{
    int age;
    string name;

    [System.Diagnostics.CodeAnalysis.SuppressMessage("Microsoft.Maintainability", "CA1500:VariableNamesShouldNotMatchFieldNames", MessageId = "age")]
    private void PrintInfo()
    {
        int age = 5;
        string name = "Charlie";

        Console.WriteLine($"Age {age}, Name {name}");
    }
}
```

## <a name="generated-code"></a>產生的程式碼

Managed 程式碼編譯器和某些協力廠商工具產生程式碼，以便快速的程式碼開發。 編譯器所產生的程式碼會出現在原始程式檔，通常會標示`GeneratedCodeAttribute`屬性。

您可以選擇是否要隱藏程式碼分析警告與錯誤產生的程式碼。 如需如何隱藏這類警告和錯誤的資訊，請參閱[如何： 隱藏的警告，產生的程式碼](../code-quality/how-to-suppress-code-analysis-warnings-for-generated-code.md)。

> [!NOTE]
> 程式碼分析忽略`GeneratedCodeAttribute`套用至整個組件或單一參數時。

## <a name="global-level-suppressions"></a>全域層級隱藏項目

Managed 程式碼分析工具會檢查`SuppressMessage`會套用到組件、 模組、 類型、 成員或參數層級的屬性。 它也會引發對資源和命名空間的違規。 這些違規必須套用的全域層級是範圍和目標。 例如，下列訊息會隱藏命名空間違規：

`[module: SuppressMessage("Microsoft.Design", "CA1020:AvoidNamespacesWithFewTypes", Scope = "namespace", Target = "MyNamespace")]`

> [!NOTE]
> 當您隱藏警告，其中含有命名空間範圍時，它會隱藏對本身的命名空間的警告。 它不會抑制警告針對命名空間內的型別。

可以表示任何隱藏項目，藉由指定明確的範圍。 這些隱藏項目必須即時的全域層級。 您無法指定成員層級隱藏項目來裝飾型別。

全域層級隱藏項目會隱藏編譯器產生的程式碼未明確提供的使用者來源對應到參考的訊息的唯一方式。 例如，下列程式碼會封鎖對編譯器發出的建構函式的違規：

`[module: SuppressMessage("Microsoft.Design", "CA1055:AbstractTypesDoNotHavePublicConstructors", Scope="member", Target="Microsoft.Tools.FxCop.Type..ctor()")]`

> [!NOTE]
> `Target` 一定會包含完整項目名稱。

## <a name="global-suppression-file"></a>全域隱藏項目檔

全域隱藏項目檔案會維護的全域層級隱藏項目或未指定目標的隱藏項目會隱藏項目。 例如，組件層級違規的隱藏項目會儲存此檔案中。 此外，有些 ASP.NET 隱藏項目會儲存在這個檔案中，因為專案層級設定不適用於表單後面的程式碼。 建立全域隱藏項目檔並將其加入至專案，因此您選取第一次**專案隱藏項目檔中的流程範本**選項**隱藏**命令**錯誤清單**視窗。

## <a name="see-also"></a>另請參閱

- <xref:System.Diagnostics.CodeAnalysis>
- [使用 Roslyn 分析器](../code-quality/use-roslyn-analyzers.md)