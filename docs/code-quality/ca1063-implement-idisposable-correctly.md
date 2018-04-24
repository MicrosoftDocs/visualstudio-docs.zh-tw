---
title: CA1063：必須正確實作 IDisposable
ms.date: 02/12/2018
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9205c20730681969550c3a2368e6ec889056648b
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/19/2018
---
# <a name="ca1063-implement-idisposable-correctly"></a>CA1063：必須正確實作 IDisposable

|||
|-|-|
|TypeName|ImplementIDisposableCorrectly|
|CheckId|CA1063|
|分類|Microsoft.Design|
|中斷變更|非中斷|

## <a name="cause"></a>原因

`IDisposable` 未正確實作。 這個問題的一些原因如下：

- IDisposable 是重新實作在類別中。

- 完成重新覆寫。

- 會覆寫 dispose。

- Dispose （） 不是公用，密封，或已命名的處置。

- Dispose （bool） 不受保護、 虛擬或未密封。

- 未密封的型別，在 dispose （） 必須呼叫 dispose （true）。

- 對於未密封的型別，Finalize 實作不會呼叫其中一個或兩個 dispose （bool） 或案例類別完成項。

這些模式的其中任何一個違規將會觸發這個警告。

每個未密封的型別宣告並實作 IDisposable 介面必須提供自己受保護虛擬 void dispose （bool） 的方法。 Dispose （） 應該呼叫 Dipose(true) 和 Finalize 應該呼叫 dispose （false）。 如果您要建立未密封的型別宣告並實作 IDisposable 介面，您必須定義 dispose （bool），並呼叫它。 如需詳細資訊，請參閱[清除 unmanaged 資源](/dotnet/standard/garbage-collection/unmanaged)中[.NET Framework 設計方針](/dotnet/standard/design-guidelines/index)。

## <a name="rule-description"></a>規則描述

所有的 IDisposable 類型都需正確地實作 Dispose 模式。

## <a name="how-to-fix-violations"></a>如何修正違規

檢查您的程式碼，並判斷哪些解決方案可以修正此違規。

- 從由 {0} 實作且改為覆寫基底類別 Dispose 實作的介面清單中移除 IDisposable。

- 移除型別 {0} 中的完成項、 覆寫 Dispose (bool disposing)，以及最終處理邏輯中的程式碼路徑其中 'disposing' 為 false。

- 移除 {0}，覆寫 Dispose (bool disposing)，而且將處置邏輯放在程式碼路徑中 'disposing' 為 true。

- 確定 {0} 已宣告為 public 和 sealed。

- 重新命名為 'Dispose' {0}，並請確定它宣告為 public 和 sealed。

- 請確定該 {0} 宣告為 protected、 virtual 和未密封。

- 修改 {0}，讓它會呼叫 dispose （true），然後呼叫 GC。目前的物件執行個體上的 SuppressFinalize ('this' Me' 中[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)])，然後傳回。

- 修改 {0}，讓它會呼叫 dispose （false），然後傳回。

- 如果您要建立未密封的型別宣告並實作 IDisposable 介面，請確定實作 IDisposable 的遵循本節稍早描述的模式。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

請勿隱藏此規則的警告。

## <a name="pseudo-code-example"></a>虛擬程式碼範例

下列虛擬程式碼提供 dispose （bool） 應如何實作中使用受管理的類別和原生資源的一般的範例。

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
    // own unmanaged resources itself, but leave the other methods
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