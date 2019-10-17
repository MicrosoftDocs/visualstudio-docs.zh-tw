---
title: CA1063：必須正確實作 IDisposable
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- ImplementIDisposableCorrectly
- CA1063
helpviewer_keywords:
- CA1063
- ImplementIDisposableCorrectly
ms.assetid: 12afb1ea-3a17-4a3f-a1f0-fcdb853e2359
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: 0fd4ba8d5dd5568dc7fca50ed61739b490bdcba7
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72440610"
---
# <a name="ca1063-implement-idisposable-correctly"></a>CA1063：必須正確實作 IDisposable

|||
|-|-|
|TypeName|ImplementIDisposableCorrectly|
|CheckId|CA1063|
|分類|Microsoft. Design|
|重大變更|不中斷|

## <a name="cause"></a>原因

未正確執行 <xref:System.IDisposable?displayProperty=nameWithType> 介面。 可能的原因包括：

- <xref:System.IDisposable> 會在類別中根據重新實作。

- `Finalize` 會再次遭到覆寫。

- `Dispose()` 會遭到覆寫。

- @No__t-0 方法不是公用、[密封](/dotnet/csharp/language-reference/keywords/sealed)或名為**Dispose**。

- `Dispose(bool)` 未受保護、虛擬或未密封。

- 在未密封的類型中，`Dispose()` 必須呼叫 `Dispose(true)`。

- 若為未密封的類型，@no__t 0 的實作用不會呼叫或兩者都是 `Dispose(bool)` 或基類完成項。

違反任何一種模式會觸發警告 CA1063 必須。

宣告並實 @no__t 0 介面的每個未密封類型，都必須提供自己的 @no__t 1 方法。 `Dispose()` 應呼叫 `Dispose(true)`，而完成項應呼叫 `Dispose(false)`。 如果您建立宣告和執行 @no__t 0 介面的未密封型別，您必須定義 `Dispose(bool)`，並呼叫它。 如需詳細資訊，請參閱[清除非受控資源（.net 指南）](/dotnet/standard/garbage-collection/unmanaged)和[處置模式](/dotnet/standard/design-guidelines/dispose-pattern)。

根據預設，此規則只會查看外部可見的類型，但這是[可](#configurability)設定的。

## <a name="rule-description"></a>規則描述

所有 @no__t 0 類型都應該正確地實作為[處置模式](/dotnet/standard/design-guidelines/dispose-pattern)。

## <a name="how-to-fix-violations"></a>如何修正違規

檢查您的程式碼，並判斷下列哪一個解決方法會修正此違規：

- 從您的類型所實的介面清單中移除 <xref:System.IDisposable>，並改為覆寫基類處置執行。

- 從您的型別中移除完成項、覆寫 Dispose （bool 處置），然後將完成邏輯放在程式碼路徑中，其中 ' 處置 ' 為 false。

- 覆寫 Dispose （bool 處置），並將 Dispose 邏輯放在程式碼路徑中，其中 ' 處置 ' 為 true。

- 請確定 Dispose （）已宣告為 public 和[sealed](/dotnet/csharp/language-reference/keywords/sealed)。

- 將 dispose 方法重新命名為**dispose** ，並確定它已宣告為 public 和[sealed](/dotnet/csharp/language-reference/keywords/sealed)。

- 請確定 Dispose （bool）宣告為 protected、virtual 和未密封。

- 修改 Dispose （），使其呼叫 Dispose （true），然後在目前的物件實例上呼叫 <xref:System.GC.SuppressFinalize%2A> （`this`，或在 Visual Basic 中為 `Me`），然後傳回。

- 修改您的完成項，使其呼叫 Dispose （false），然後傳回。

- 如果您建立宣告並執行 <xref:System.IDisposable> 介面的未密封類型，請確定 <xref:System.IDisposable> 的實行遵循本節前面所述的模式。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

請勿隱藏此規則的警告。

## <a name="configurability"></a>可設定性

如果您是從[FxCop 分析器](install-fxcop-analyzers.md)執行此規則（而不是使用舊版分析），您可以根據其存取範圍，設定程式碼基底中的哪些部分來執行此規則。 例如，若要指定規則只針對非公用 API 介面執行，請將下列機碼值組新增至專案中的 editorconfig 檔案：

```ini
dotnet_code_quality.ca1063.api_surface = private, internal
```

您可以只針對此規則、所有規則或此類別中的所有規則（設計）設定此選項。 如需詳細資訊，請參閱[設定 FxCop 分析器](configure-fxcop-analyzers.md)。

## <a name="pseudo-code-example"></a>虛擬程式碼範例

下列虛擬程式碼提供如何在使用 managed 和原生資源的類別中實作為 Dispose （bool）的一般範例。

```csharp
public class Resource : IDisposable
{
    private IntPtr nativeResource = Marshal.AllocHGlobal(100);
    private AnotherResource managedResource = new AnotherResource();

    // Dispose() calls Dispose(true)
    public void Dispose()
    {
        Dispose(true);
        GC.SuppressFinalize(this);
    }

    // NOTE: Leave out the finalizer altogether if this class doesn't
    // own unmanaged resources, but leave the other methods
    // exactly as they are.
    ~Resource()
    {
        // Finalizer calls Dispose(false)
        Dispose(false);
    }

    // The bulk of the clean-up code is implemented in Dispose(bool)
    protected virtual void Dispose(bool disposing)
    {
        if (disposing)
        {
            // free managed resources
            if (managedResource != null)
            {
                managedResource.Dispose();
                managedResource = null;
            }
        }
        // free native resources if there are any.
        if (nativeResource != IntPtr.Zero)
        {
            Marshal.FreeHGlobal(nativeResource);
            nativeResource = IntPtr.Zero;
        }
    }
}
```

## <a name="see-also"></a>請參閱

- [Dispose 模式（架構設計方針）](/dotnet/standard/design-guidelines/dispose-pattern)
- [清除非受控資源（.NET 指南）](/dotnet/standard/garbage-collection/unmanaged)
