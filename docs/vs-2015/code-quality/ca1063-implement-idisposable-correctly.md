---
title: CA1063 必須：正確地執行 IDisposable |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ImplementIDisposableCorrectly
- CA1063
helpviewer_keywords:
- CA1063
- ImplementIDisposableCorrectly
ms.assetid: 12afb1ea-3a17-4a3f-a1f0-fcdb853e2359
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 1fe2982ab9e1b3951583b268eadb44c97c8e4805
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663640"
---
# <a name="ca1063-implement-idisposable-correctly"></a>CA1063：必須正確實作 IDisposable
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ImplementIDisposableCorrectly|
|CheckId|CA1063|
|Category|Microsoft. Design|
|中斷變更|不中斷|

## <a name="cause"></a>原因
 未正確執行 `IDisposable`。 此問題的一些原因如下所列：

- IDisposable 會在類別中重新執行。

- Finalize 會重新覆寫。

- Dispose 會遭到覆寫。

- Dispose （）不是公用、密封或名為 Dispose。

- Dispose （bool）未受保護、虛擬或未密封。

- 在未密封的類型中，Dispose （）必須呼叫 Dispose （true）。

- 對於未密封的類型，Finalize 執行不會呼叫 Dispose （bool）或案例類別完成項。

  違反其中任何一種模式將會觸發此警告。

  每個未密封的根 IDisposable 類型都必須提供自己的受保護虛擬 void Dispose （bool）方法。 Dispose （）應呼叫 Dispose （true），而 Finalize 應呼叫 Dispose （false）。 如果您要建立未密封的根 IDisposable 類型，您必須定義 Dispose （bool）並呼叫它。 如需詳細資訊，請參閱 .NET Framework 檔的[架構設計方針](https://msdn.microsoft.com/library/5fbcaf4f-ea2a-4d20-b0d6-e61dee202b4b)一節中的[清除非受控資源](https://msdn.microsoft.com/library/a17b0066-71c2-4ba4-9822-8e19332fc213)。

## <a name="rule-description"></a>規則描述
 所有的 IDisposable 類型都需正確地實作 Dispose 模式。

## <a name="how-to-fix-violations"></a>如何修正違規
 檢查您的程式碼，並判斷下列哪一個解決方法會修正此違規。

- 從 {0} 所執行的介面清單中移除 IDisposable，並改為覆寫基類處置執行。

- 從類型 {0} 移除完成項，覆寫 Dispose （bool 處置），並將完成邏輯放在程式碼路徑中，其中 ' 處置 ' 為 false。

- 移除 {0}、覆寫 Dispose （bool 處置），然後將 dispose 邏輯放在程式碼路徑中，其中 ' 處置 ' 為 true。

- 請確定 {0} 宣告為 public 和 sealed。

- 將 {0} 重新命名為 ' Dispose '，並確定它已宣告為 public 和 sealed。

- 請確定 {0} 宣告為 protected、virtual 和未密封。

- 修改 {0}，使其呼叫 Dispose （true），然後呼叫 GC。Gc.suppressfinalize 在目前的物件實例上（在 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 中為 ' this ' 或 ' Me '），然後傳回。

- 修改 {0}，使其呼叫 Dispose （false），然後傳回。

- 如果您要撰寫未密封的根 IDisposable 類別，請確定 IDisposable 的執行遵循本節稍早所述的模式。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。

## <a name="pseudo-code-example"></a>虛擬程式碼範例
 下列虛擬程式碼提供如何在使用 managed 和原生資源的類別中實作為 Dispose （bool）的一般範例。

```
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
