---
title: 隱藏程式碼分析警告
ms.date: 12/01/2018
ms.topic: conceptual
helpviewer_keywords:
- source suppression, code analysis
- code analysis, source suppression
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.openlocfilehash: 71d2fe83690e55d49bb23bffb09de91c8f7534b6
ms.sourcegitcommit: 1efb6b219ade7c35068b79fbdc573a8771ac608d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2020
ms.locfileid: "78167620"
---
# <a name="suppress-code-analysis-warnings"></a>隱藏程式碼分析警告

指出警告不適用時，通常會很有用。 這會向小組成員表示已審查程式碼，而且可以隱藏警告。 原始碼隱藏專案（ISS）會使用 <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> 屬性來隱藏警告。 屬性可以放在靠近產生警告之程式碼區段的位置。 您可以在原始程式檔中輸入來加入 <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> 屬性，或者您可以在**錯誤清單**的警告上使用快捷方式功能表，自動將它加入。

<xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> 屬性是條件式屬性，只有在編譯時期定義了 CODE_ANALYSIS 編譯符號時，才會包含在 managed 程式碼元件的 IL 中繼資料中。

在C++/cli 中，使用宏 CA\_隱藏標頭檔中\_訊息或 CA\_全域\_SUPPRESS_MESSAGE 來新增屬性。

> [!NOTE]
> 您不應該在發行組建上使用「原始碼隱藏式」，以避免意外傳送原始碼抑制中繼資料。 此外，由於原始碼隱藏的處理成本，應用程式的效能可能會降低。

::: moniker range="vs-2017"

> [!NOTE]
> 如果您將專案遷移至 Visual Studio 2017，可能會突然遇到大量的程式碼分析警告。 如果您還沒準備好修正警告，可以選擇 [**分析**] > **執行程式碼分析，並隱藏**作用中的問題，藉以隱藏所有警示。
>
> ![執行程式碼分析並隱藏 Visual Studio 中的問題](media/suppress-active-issues.png)

::: moniker-end

::: moniker range=">=vs-2019"

> [!NOTE]
> 如果您將專案遷移至 Visual Studio 2019，可能會突然遇到大量的程式碼分析警告。 如果您還沒準備好修正警告，可以選擇 [**分析**] > [**建立] 和 [隱藏**作用中的問題] 來隱藏所有警示。

::: moniker-end

## <a name="suppressmessage-attribute"></a>SuppressMessage 屬性

當您從 **錯誤清單**中的程式碼分析警告的內容或右鍵功能表中選擇 **隱藏** 時，會在您的程式碼或專案的全域隱藏專案檔案中加入 <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> 屬性。

<xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> 屬性具有下列格式：

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

- **Category** -用來定義規則的類別目錄。 如需程式碼分析規則類別目錄的詳細資訊，請參閱[Managed 程式碼警告](../code-quality/code-analysis-for-managed-code-warnings.md)。

- **CheckId** -規則的識別碼。 支援包括規則識別碼的簡短和完整名稱。 簡短名稱為 CAXXXX;完整名稱是 CAXXXX： FriendlyTypeName。

- **對齊**-用來記錄隱藏訊息原因的文字。

- **MessageId** -每個訊息之問題的唯一識別碼。

- **範圍**-隱藏警告的目標。 如果未指定目標，則會將它設定為屬性的目標。 支援的[範圍](xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute.Scope)包括下列各項：

  - [`module`](#module-suppression-scope) -此範圍會隱藏對元件的警告。 它是套用至整個專案的全域隱藏專案。

  - `resource`-（僅限[舊版 FxCop](../code-quality/static-code-analysis-for-managed-code-overview.md) ）此範圍會抑制診斷資訊中寫入模組（元件）一部分之資源檔的警告。 Roslyn 分析器診斷的C#/VB 編譯器不會讀取/遵守此範圍，只會分析原始程式檔。

  - `type`-此範圍會隱藏對類型的警告。

  - `member`-此範圍會隱藏對成員的警告。

  - `namespace`-此範圍會針對命名空間本身隱藏警告。 它不會針對命名空間中的類型隱藏警告。

  - `namespaceanddescendants`-（需要編譯器 3.x. x 版或更高版本，以及 Visual Studio 2019）此範圍會隱藏命名空間及其所有子系符號中的警告。 舊版分析會忽略 `namespaceanddescendants` 值。

- **Target** -用來指定隱藏警告之目標的識別碼。 它必須包含完整的專案名稱。

## <a name="suppressmessage-usage"></a>SuppressMessage 使用方式

程式碼分析警告會在套用 <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> 屬性的層級上隱藏。 例如，您可以在元件、模組、型別、成員或參數層級套用屬性。 這樣做的目的是要將隱藏專案資訊緊密地放在違規發生的程式碼中。

隱藏式的一般形式包括規則分類和規則識別碼，其中包含規則名稱的選擇性人可讀取標記法。 例如，

`[SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]`

如果將原始碼隱藏式中繼資料降到最低，有很嚴格的效能考慮，則可以省略規則名稱。 規則類別和其規則識別碼會形成一個足夠的唯一規則識別碼。 例如，

`[SuppressMessage("Microsoft.Design", "CA1039")]`

基於可維護性的考慮，不建議省略規則名稱。

## <a name="suppress-selective-violations-within-a-method-body"></a>隱藏方法主體內的選擇性違規

隱藏專案屬性可以套用至方法，但不能內嵌在方法主體內。 這表示如果您將 <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> 屬性加入至方法，則會隱藏特定規則的所有違規。

在某些情況下，您可能會想要隱藏特定的違規實例，例如，未來的程式碼不會自動從程式碼分析規則中排除。 某些程式碼分析規則可讓您使用 <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> 屬性的 `MessageId` 屬性來執行這項操作。 一般來說，特定符號（本機變數或參數）上違規的舊版規則會遵守 `MessageId` 屬性。 [CA1500： VariableNamesShouldNotMatchFieldNames](../code-quality/ca1500.md)是這類規則的範例。 不過，在可執行程式碼（非符號）上違規的舊版規則並不會遵守 `MessageId` 屬性。 此外，.NET Compiler Platform （"Roslyn"）分析器不會遵守 `MessageId` 屬性。

若要隱藏規則的特定符號違規，請指定 <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> 屬性之 `MessageId` 屬性的符號名稱。 下列範例顯示具有兩個 CA1500 的程式碼[： VariableNamesShouldNotMatchFieldNames](../code-quality/ca1500.md)&mdash;一個用於 `name` 變數，另一個用於 `age` 變數。 只會隱藏 `age` 符號的違規。

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

Managed 程式碼編譯器和一些協力廠商工具會產生程式碼，以加速程式碼開發。 出現在原始程式檔中的編譯器產生的程式碼，通常會以 `GeneratedCodeAttribute` 屬性來標示。

您可以選擇是否要針對產生的程式碼隱藏程式碼分析警告和錯誤。 如需有關如何隱藏這類警告和錯誤的詳細資訊，請參閱[如何：隱藏所產生程式碼的警告](../code-quality/how-to-suppress-code-analysis-warnings-for-generated-code.md)。

> [!NOTE]
> 程式碼分析會在套用至整個元件或單一參數時，忽略 `GeneratedCodeAttribute`。

## <a name="global-level-suppressions"></a>全域層級隱藏式

Managed 程式碼分析工具會檢查元件、模組、類型、成員或參數層級所套用的 `SuppressMessage` 屬性。 它也會對資源和命名空間引發違規。 這些違規必須套用於全域層級，且範圍設定為目標。 例如，下列訊息會抑制命名空間違規：

`[module: SuppressMessage("Microsoft.Design", "CA1020:AvoidNamespacesWithFewTypes", Scope = "namespace", Target = "MyNamespace")]`

> [!NOTE]
> 當您隱藏具有 `namespace` 範圍的警告時，它會針對命名空間本身抑制警告。 它不會針對命名空間內的類型隱藏警告。

您可以藉由指定明確範圍來表示任何隱藏專案。 這些隱藏項必須存留在全域層級。 您無法藉由裝飾類型來指定成員層級的隱藏專案。

全域層級的隱藏式是隱藏參考編譯器所產生之程式碼的訊息的唯一方式，而不會對應到明確提供的使用者來源。 例如，下列程式碼會抑制對編譯器發出的函式的違規：

`[module: SuppressMessage("Microsoft.Design", "CA1055:AbstractTypesDoNotHavePublicConstructors", Scope="member", Target="Microsoft.Tools.FxCop.Type..ctor()")]`

> [!NOTE]
> `Target` 一律包含完整的專案名稱。

### <a name="global-suppression-file"></a>全域隱藏專案檔案

全域隱藏專案檔案會維護不會指定目標的全域層級隱藏專案或隱藏專案。 例如，元件層級違規的隱藏式會儲存在這個檔案中。 此外，某些 ASP.NET 隱藏專案會儲存在此檔案中，因為在表單後方的程式碼中，不提供專案層級設定。 當您第一次在 [**錯誤清單**] 視窗中，選取 [**隱藏**] 命令的 [**在專案隱藏檔中**] 選項時，就會建立全域隱藏專案檔案，並將其新增至您的專案。

### <a name="module-suppression-scope"></a>模組隱藏範圍

您可以使用**模組**範圍，隱藏整個元件的程式碼品質違規。

例如， _GlobalSuppressions_專案檔中的下列屬性會隱藏 ASP.NET Core 專案的 ConfigureAwait 違規：

`[assembly: System.Diagnostics.CodeAnalysis.SuppressMessage("Reliability", "CA2007:Consider calling ConfigureAwait on the awaited task", Justification = "ASP.NET Core doesn't use thread context to store request context.", Scope = "module")]`

## <a name="see-also"></a>另請參閱

- <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute.Scope>
- <xref:System.Diagnostics.CodeAnalysis>
- [使用程式碼分析器](../code-quality/use-roslyn-analyzers.md)
