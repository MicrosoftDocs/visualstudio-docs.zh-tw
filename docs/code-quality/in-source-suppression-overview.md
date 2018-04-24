---
title: 隱藏在 Visual Studio 中的程式碼分析警告
ms.date: 01/29/2018
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
ms.openlocfilehash: 1b057b13697fe1ec41fdca1bef27ccb03637f696
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/19/2018
---
# <a name="suppress-code-analysis-warnings"></a>隱藏程式碼分析警告

通常會很有用，表示警告不適用。 這表示此程式碼的檢閱，而且可以隱藏警告的小組成員。 來源隱藏項目 (ISS) 使用<xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute>屬性來隱藏的警告。 屬性可以放接近產生警告的程式碼片段。 您可以加入<xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute>屬性設定為原始程式檔中，輸入您可以使用捷徑功能表中的警告或**錯誤清單**自動將它加入。

<xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute>屬性才隨附於您的 managed 程式碼組件的 IL 中繼資料的 conditional 屬性在編譯時期定義 CODE_ANALYSIS 編譯符號。

在 C + + CLI 使用巨集 CA\_抑制\_訊息或 CA\_GLOBAL\_SUPPRESS_MESSAGE 標頭檔中的將屬性。

> [!NOTE]
> 您不應該使用原始檔中隱藏項目上的發行組建，以避免不小心傳送的原始檔中隱藏項目中繼資料。 此外，因為在來源隱藏的處理成本，而可能降低應用程式的效能。

> [!NOTE]
> 如果您將專案移轉至 Visual Studio 2017 時，可能會突然面臨著產生大量的程式碼分析警告。 如果您不可以修正警告，並想要暫時關閉程式碼分析，請開啟專案屬性頁 (**專案** > ***專案*屬性...**)，並移至**程式碼分析** 索引標籤。取消選取**建置時啟用程式碼分析**，然後重建您的專案。 或者，您可以選取不同的小型規則集執行程式碼。 請記得在當您準備好修正警告的程式碼分析。

## <a name="suppressmessage-attribute"></a>SuppressMessage 屬性

當您選擇**抑制**從程式碼分析警告中的內容或以滑鼠右鍵按一下功能表**錯誤清單**、<xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute>屬性加入您的程式碼中，或專案的全域隱藏項目檔案。

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

- **規則類別**-定義此規則的類別目錄。 如需程式碼分析規則類別的詳細資訊，請參閱[Managed 程式碼警告](../code-quality/code-analysis-for-managed-code-warnings.md)。

- **Rule Id** -規則的識別碼。 支援包括同時短期或長期的規則識別項名稱。 簡短名稱是 CAXXXX;完整名稱是 CAXXXX:FriendlyTypeName。

- **對齊**-用來記錄原因隱藏訊息的文字。

- **訊息識別碼**-針對每則訊息有問題的唯一識別碼。

- **範圍**位在其要隱藏警告的目標。 如果未指定目標，則會將它設定為屬性的目標。 支援的範圍包括下列各項：

    - Module

    - 命名空間

    - 資源

    - 類型

    - 成員

- **目標**-識別項，用來指定在其要隱藏警告的目標。 它必須包含完整項目名稱。

## <a name="suppressmessage-usage"></a>SuppressMessage 使用量

程式碼分析警告會隱藏層級的<xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute>屬性會套用。 例如，屬性可以套用在組件、 模組、 類型、 成員或參數的層級。 目的是緊密結合的程式碼的隱藏項目資訊發生違規。

一般格式的隱藏項目包括規則分類和規則的識別碼，其中包含規則名稱的選擇性人們可讀取表示。 例如: 

`[SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]`

如果有嚴格的效能考量，在原始程式檔隱藏項目中繼資料將降到最低，可以省略 「 規則名稱。 規則類別和其規則識別碼一起構成充分唯一的規則識別項。 例如: 

`[SuppressMessage("Microsoft.Design", "CA1039")]`

為了可維護性，不建議省略規則名稱。

## <a name="suppress-selective-violations-within-a-method-body"></a>隱藏方法主體中的選擇性違規

隱藏項目屬性可以套用至方法，但不可以內嵌在方法主體。 這表示會抑制所有特定規則的違規，如果您將加入<xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute>屬性加入方法。

在某些情況下，您可能想要隱藏的違規情形，例如特定執行個體，以便未來的程式碼不會自動受程式碼分析規則。 某些程式碼分析規則可讓您利用`MessageId`屬性<xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute>屬性。 一般情況下，傳統規則違規 （本機變數或參數） 的特定符號尊重`MessageId`屬性。 [CA1500:VariableNamesShouldNotMatchFieldNames](../code-quality/ca1500-variable-names-should-not-match-field-names.md)是這類規則的範例。 不過，傳統規則違規的可執行程式碼 （非符號） 不受影響`MessageId`屬性。 此外，.NET 編譯器平台 ("Roslyn") 分析器不受影響`MessageId`屬性。

若要隱藏特定符號規則的違規情形，指定的符號名稱`MessageId`屬性<xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute>屬性。 下列範例示範具有兩個違規的程式碼[CA1500:VariableNamesShouldNotMatchFieldNames](../code-quality/ca1500-variable-names-should-not-match-field-names.md)&mdash;另一個用於`name`變數，另一個用於`age`變數。 僅違反`age`符號會隱藏。

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

Managed 程式碼編譯器和某些協力廠商工具產生程式碼，以便快速的程式碼開發。 出現在原始程式檔的編譯器所產生程式碼通常會標示`GeneratedCodeAttribute`屬性。

您可以選擇是否要隱藏程式碼分析警告與錯誤產生的程式碼。 如需如何隱藏這類警告和錯誤的資訊，請參閱[如何： 隱藏產生的程式碼的警告](../code-quality/how-to-suppress-code-analysis-warnings-for-generated-code.md)。

> [!NOTE]
> 程式碼分析會略過`GeneratedCodeAttribute`套用至整個組件或單一參數時。

## <a name="global-level-suppressions"></a>全域層級隱藏項目

Managed 程式碼分析工具會檢查`SuppressMessage`會套用到組件、 模組、 類型、 成員或參數的層級的屬性。 它也會引發對資源和命名空間的違規。 這些違規必須在全域層級套用，並為範圍並為目標。 例如，下列訊息會隱藏命名空間違規：

`[module: SuppressMessage("Microsoft.Design", "CA1020:AvoidNamespacesWithFewTypes", Scope = "namespace", Target = "MyNamespace")]`

> [!NOTE]
> 當您隱藏警告，並且包含命名空間範圍內時，它會抑制警告針對命名空間本身。 它不會隱藏對型別在命名空間中的警告。

可以表示任何隱藏項目，藉由指定明確的範圍。 這些隱藏項目必須駐留在全域層級。 您無法指定成員層級隱藏項目，而將型別。

全域層級隱藏項目會隱藏編譯器產生的程式碼不會對應至提供明確的使用者來源是指的訊息的唯一方式。 例如，下列程式碼會隱藏編譯器發出的建構函式的違規：

`[module: SuppressMessage("Microsoft.Design", "CA1055:AbstractTypesDoNotHavePublicConstructors", Scope="member", Target="Microsoft.Tools.FxCop.Type..ctor()")]`

> [!NOTE]
> `Target` 一定會包含完整項目名稱。

## <a name="global-suppression-file"></a>全域隱藏項目檔

全域隱藏項目檔案維護的全域層級隱藏項目或未指定目標的隱藏項目的隱藏項目。 例如，組件層級違規的隱藏項目會儲存此檔案中。 此外，某些 ASP.NET 隱藏項目會儲存在這個檔案中，因為沒有可用的表單背後的程式碼專案層級設定。 建立全域隱藏項目檔並將其加入至專案，您選取第一次**專案隱藏項目檔中**選項**抑制**命令**錯誤清單**視窗。

## <a name="see-also"></a>另請參閱

- <xref:System.Diagnostics.CodeAnalysis>
- [使用 Roslyn 分析器](../code-quality/use-roslyn-analyzers.md)