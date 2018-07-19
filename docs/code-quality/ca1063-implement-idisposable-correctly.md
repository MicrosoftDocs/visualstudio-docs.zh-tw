---
title: CA1063：必須正確實作 IDisposable
ms.date: 02/12/2018
ms.prod: visual-studio-dev15
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
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: e202c35ee6bd8353170e758629b1cc6e739b775d
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/17/2018
ms.locfileid: "39080967"
---
# <a name="ca1063-implement-idisposable-correctly"></a>CA1063：必須正確實作 IDisposable

|||
|-|-|
|TypeName|ImplementIDisposableCorrectly|
|CheckId|CA1063|
|分類|Microsoft.Design|
|中斷變更|非重大|

## <a name="cause"></a>原因

<xref:System.IDisposable?displayProperty=nameWithType>介面的實作不正確。 可能原因包括：

- <xref:System.IDisposable> 被根據類別中。

- 完成程序 reoverridden。

- Dispose （） 會覆寫。

- Dispose （） 方法不是公用的[密封](/dotnet/csharp/language-reference/keywords/sealed)，或具名**處置**。

- Dispose （bool） 不受保護、 虛擬或未密封。

- 非密封類型，在 dispose （） 必須呼叫 dispose （true）。

- 對於非密封類型，完成實作不會呼叫其中一個或兩個 dispose （bool） 或基底類別完成項。

這些模式的其中任何一個的違規會觸發警告 ca1063 必須。

每個未密封的型別會宣告並實作<xref:System.IDisposable>介面必須提供它自己受保護虛擬 void dispose （bool） 方法。 Dispose （） 應該呼叫 Dipose(true)，和完成項應該呼叫 dispose （false）。 如果您建立未密封的型別會宣告並實作<xref:System.IDisposable>介面，您必須定義 dispose （bool），並呼叫它。 如需詳細資訊，請參閱 <<c0> [ 清除 unmanaged 資源 （.NET 指南）](/dotnet/standard/garbage-collection/unmanaged)並[Dispose 模式](/dotnet/standard/design-guidelines/dispose-pattern)。

## <a name="rule-description"></a>規則描述

所有<xref:System.IDisposable>型別應該實作[Dispose 模式](/dotnet/standard/design-guidelines/dispose-pattern)正確。

## <a name="how-to-fix-violations"></a>如何修正違規

檢查您的程式碼，並判斷哪些解決方案可以修正此違規：

- 移除<xref:System.IDisposable>從清單中，會藉由將您的類型，並改為覆寫基底類別 Dispose 實作的介面。

- 移除您的型別中的完成項、 覆寫 Dispose (bool disposing)，並放在程式碼路徑的最終處理邏輯，其中 'disposing' 為 false。

- 覆寫 Dispose (bool disposing)，並將處置邏輯放在程式碼路徑中 'disposing' 為 true。

- 請確定 dispose （） 會宣告為公用並[密封](/dotnet/csharp/language-reference/keywords/sealed)。

- 重新命名您的 dispose 方法，來**處置**，並確定它已宣告為公用並[密封](/dotnet/csharp/language-reference/keywords/sealed)。

- 請確定 dispose （bool） 已宣告為 protected、 virtual 和 unsealed。

- 修改 dispose （），讓它會呼叫 dispose （true），然後呼叫<xref:System.GC.SuppressFinalize%2A>目前的物件執行個體上 (`this`，或`Me`Visual Basic 中)，然後傳回。

- 修改您的完成項，讓它呼叫 dispose （false），然後傳回。

- 如果您建立未密封的型別會宣告並實作<xref:System.IDisposable>介面，請確定實作<xref:System.IDisposable>遵循本節稍早說明的模式。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

請勿隱藏此規則的警告。

## <a name="pseudo-code-example"></a>虛擬程式碼範例

下列虛擬程式碼提供如何應該實作 dispose （bool） 中使用受管理的類別和原生資源的一般範例。

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

## <a name="see-also"></a>另請參閱

- [Dispose 模式 （framework 設計方針）](/dotnet/standard/design-guidelines/dispose-pattern)
- [清除 unmanaged 資源 （.NET 指南）](/dotnet/standard/garbage-collection/unmanaged)