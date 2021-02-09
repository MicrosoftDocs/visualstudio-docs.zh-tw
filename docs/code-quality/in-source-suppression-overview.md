---
title: 隱藏程式碼分析違規項目
ms.date: 08/27/2020
description: 瞭解如何在 Visual Studio 中隱藏程式碼分析違規。 瞭解如何將 SuppressMessageAttribute 屬性用於來源隱藏專案。
ms.custom: SEO-VS-2020
ms.topic: conceptual
helpviewer_keywords:
- source suppression, code analysis
- code analysis, source suppression
author: mikadumont
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.openlocfilehash: c61803c21832367ede01817029b8d0318ac741a4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99859901"
---
# <a name="suppress-code-analysis-violations"></a>隱藏程式碼分析違規項目

指出警告不適用時，通常會很有用。 這表示小組成員已審核程式碼，而且可以隱藏警告。  (ISS 的原始檔隱藏) 使用 <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> 屬性來抑制警告。 屬性可放置於接近產生警告的程式碼區段。 您可以 <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> 在原始程式檔中輸入屬性，將其加入至原始程式檔，也可以使用 [ **錯誤清單** ] 中警告的快捷方式功能表自動新增。

<xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute>屬性是條件式屬性，只有在編譯時期定義 CODE_ANALYSIS 編譯符號時，才會包含在 managed 程式碼元件的 IL 中繼資料中。

在 c + +/CLI 中，使用 \_ 標頭檔中的 [宏] \_ 或 [ca \_ 全域 SUPPRESS_MESSAGE] \_ 來新增屬性。

> [!NOTE]
> 您不應該在發行組建上使用原始檔中的隱藏專案，以防止意外傳送來源隱藏中繼資料。 此外，由於來源抑制的處理成本，應用程式的效能可能會降低。

::: moniker range="vs-2017"

> [!NOTE]
> 如果您將專案遷移至 Visual Studio 2017，可能突然遇到大量的程式碼分析警告。 如果您還沒準備好修正這些警告，您可以選取 [**分析**  >  **執行程式碼分析] 並隱藏** 作用中的問題，來抑制所有警告。
>
> ![在 Visual Studio 中執行程式碼分析和隱藏問題](media/suppress-active-issues.png)

::: moniker-end

::: moniker range=">=vs-2019"

> [!NOTE]
> 如果您將專案遷移至 Visual Studio 2019，可能突然遇到大量的程式碼分析警告。 如果您還沒準備好修正這些警告，您可以選取 [**分析**  >  **組建] 並隱藏** 作用中的問題，來抑制這些警告。

::: moniker-end

## <a name="suppressmessage-attribute"></a>SuppressMessage 屬性

當您從 [**錯誤清單**] 中的程式碼分析警告的內容或右鍵功能表中選取 [**隱藏**] 時， <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> 會在您的程式碼或專案的全域隱藏專案檔中加入屬性。

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

- **Category** -規則定義所在的分類。 如需程式碼分析規則類別的詳細資訊，請參閱 [Managed 程式碼警告](/dotnet/fundamentals/code-analysis/quality-rules/index)。

- **CheckId** -規則的識別碼。 支援包含規則識別碼的簡短和完整名稱。 簡短名稱是 CAXXXX;完整名稱是 CAXXXX： FriendlyTypeName。

- **理由** -用來記錄隱藏訊息原因的文字。

- **MessageId** -每個訊息之問題的唯一識別碼。

- **範圍** -隱藏警告的目標。 如果未指定目標，則會將它設定為屬性的目標。 支援的 [範圍](xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute.Scope) 包括下列各項：

  - [`module`](#module-suppression-scope) -此範圍會隱藏對元件的警告。 它是套用至整個專案的全域隱藏專案。

  - `resource` -僅 ([舊版 FxCop](../code-quality/static-code-analysis-for-managed-code-overview.md)) 此範圍會隱藏診斷資訊中的警告，這些資訊會寫入屬於模組 (元件) 的資源檔。 在適用于 Roslyn 分析器診斷的 c #/VB 編譯器中，不會讀取/遵守此範圍，它只會分析原始程式檔。

  - `type` -此範圍會抑制針對類型的警告。

  - `member` -此範圍會抑制對成員的警告。

  - `namespace` -此範圍會隱藏對命名空間本身的警告。 它不會對命名空間中的類型隱藏警告。

  - `namespaceanddescendants` - (需要編譯器1.x 版或更高版本，且 Visual Studio 2019) 此範圍會隱藏命名空間及其所有子系符號中的警告。 `namespaceanddescendants`舊版分析會忽略此值。

- **目標** -用來指定要隱藏警告之目標的識別碼。 它必須包含完整的專案名稱。

當您在 Visual Studio 中看到警告時，您可以在 `SuppressMessage` 全域隱藏專案檔中 [加入隱藏](../code-quality/use-roslyn-analyzers.md#suppress-violations)專案，以查看的範例。 隱藏專案屬性及其必要屬性會出現在預覽視窗中。

## <a name="suppressmessage-usage"></a>SuppressMessage 使用方式

程式碼分析警告會隱藏于套用屬性的層級 <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> 。 例如，屬性可套用於元件、模組、類型、成員或參數層級。 這項功能的目的是要將隱藏的資訊緊密地結合到違規發生的程式碼。

隱藏專案的一般形式包括規則類別目錄和規則識別碼，其中包含規則名稱的選擇性人類可讀取標記法。 例如：

`[SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]`

如果最小化來源隱藏專案中繼資料的效能有嚴格的原因，可以省略規則名稱。 規則類別和其規則識別碼會形成足夠的唯一規則識別碼。 例如：

`[SuppressMessage("Microsoft.Design", "CA1039")]`

基於可維護性的理由，不建議省略規則名稱。

## <a name="suppress-selective-violations-within-a-method-body"></a>隱藏方法主體內的選擇性違規

隱藏專案屬性可以套用至方法，但無法內嵌于方法主體內。 這表示，如果您將屬性加入至方法，就會隱藏特定規則的所有違規 <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> 。

在某些情況下，您可能會想要隱藏違規的特定實例，例如，未來的程式碼不會自動豁免程式碼分析規則。 某些程式碼分析規則可讓您使用屬性 `MessageId` （attribute）的屬性（attribute）來完成這項作業 <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> 。 一般來說，在特定符號上違規的舊版規則 (區域變數或參數) 遵守 `MessageId` 屬性。 [CA1500： VariableNamesShouldNotMatchFieldNames](../code-quality/ca1500.md) 是這類規則的範例。 不過，在可執行程式碼上違規的舊版規則 (非符號) 不會遵守 `MessageId` 屬性。 此外，.NET Compiler Platform ( "Roslyn" ) 分析器不會遵守 `MessageId` 屬性。

若要隱藏規則的特定符號違規，請指定屬性的符號名稱 `MessageId` <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> 。 下列範例顯示具有兩個 CA1500 違規的程式碼[： VariableNamesShouldNotMatchFieldNames](../code-quality/ca1500.md) &mdash; 一個用於 `name` 變數，另一個用於 `age` 變數。 只 `age` 會隱藏符號的違規。

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

## <a name="global-level-suppressions"></a>全域層級隱藏

Managed 程式碼分析工具 `SuppressMessage` 會檢查元件、模組、類型、成員或參數層級所套用的屬性。 它也會對資源和命名空間引發違規。 這些違規必須套用到全域層級，並設定範圍並設為目標。 例如，下列訊息會抑制命名空間違規：

`[module: SuppressMessage("Microsoft.Design", "CA1020:AvoidNamespacesWithFewTypes", Scope = "namespace", Target = "MyNamespace")]`

> [!NOTE]
> 當您隱藏範圍的警告時 `namespace` ，它會抑制對命名空間本身的警告。 它不會對命名空間中的類型隱藏警告。

任何隱藏專案都可以藉由指定明確的範圍來表示。 這些隱藏項必須存留在全域層級。 您無法藉由裝飾類型來指定成員層級隱藏專案。

全域層級隱藏的唯一方法是隱藏參考編譯器產生之程式碼的訊息，而該程式碼不會對應至明確提供的使用者來源。 例如，下列程式碼會針對編譯器發出的函式抑制違規：

`[module: SuppressMessage("Microsoft.Design", "CA1055:AbstractTypesDoNotHavePublicConstructors", Scope="member", Target="Microsoft.Tools.FxCop.Type..ctor()")]`

> [!NOTE]
> `Target` 一律包含完整的專案名稱。

### <a name="global-suppression-file"></a>全域隱藏專案檔

全域隱藏專案檔會維護不指定目標的全域層級隱藏專案或隱藏專案。 例如，元件層級違規的隱藏項會儲存在此檔案中。 此外，某些 ASP.NET 隱藏專案會儲存在此檔案中，因為表單背後的程式碼無法使用專案層級設定。 當您第一次在 [**錯誤清單**] 視窗中，于 [**隱藏**] 命令的 [**專案隱藏** 檔] 選項中選取時，即會建立全域隱藏專案檔並將其新增至您的專案。

### <a name="module-suppression-scope"></a>模組隱藏範圍

您可以使用 **模組** 範圍來抑制整個元件的程式碼品質違規。

例如， _GlobalSuppressions_ 專案檔中的下列屬性將會抑制 ASP.NET Core 專案的 ConfigureAwait 違規：

`[assembly: System.Diagnostics.CodeAnalysis.SuppressMessage("Reliability", "CA2007:Consider calling ConfigureAwait on the awaited task", Justification = "ASP.NET Core doesn't use thread context to store request context.", Scope = "module")]`

## <a name="generated-code"></a>產生的程式碼

Managed 程式碼編譯器和一些協力廠商工具會產生程式碼，以加速程式碼開發。 在原始程式檔中出現的編譯器產生程式碼通常會以 `GeneratedCodeAttribute` 屬性標記。

針對原始程式碼分析，您可以在檔案中隱藏產生的程式碼中的訊息 `.editorconfig` 。 如需詳細資訊，請參閱 [排除產生](/dotnet/fundamentals/code-analysis/configuration-options#exclude-generated-code)的程式碼。

針對舊版程式碼分析，您可以選擇是否要隱藏所產生程式碼的程式碼分析警告和錯誤。 如需如何隱藏這類警告和錯誤的詳細資訊，請參閱 [如何：隱藏所產生程式碼的警告](../code-quality/how-to-suppress-code-analysis-warnings-for-generated-code.md)。

> [!NOTE]
> 當程式碼分析套用 `GeneratedCodeAttribute` 至整個元件或單一參數時，會忽略程式碼分析。

## <a name="see-also"></a>另請參閱

- <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute.Scope>
- <xref:System.Diagnostics.CodeAnalysis>
- [使用程式碼分析器](../code-quality/use-roslyn-analyzers.md)
