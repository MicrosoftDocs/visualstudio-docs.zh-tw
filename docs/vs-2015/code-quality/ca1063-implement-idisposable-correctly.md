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
ms.openlocfilehash: 04691d2344b232906676180122ad67fff5405891
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85539356"
---
# <a name="ca1063-implement-idisposable-correctly"></a>CA1063:必須正確實作 IDisposable
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|ImplementIDisposableCorrectly|
|CheckId|CA1063|
|類別|Microsoft. 設計|
|中斷變更|非中斷|

## <a name="cause"></a>原因
 `IDisposable` 未正確地執行。 此問題的一些原因如下所示：

- 在類別中重新執行 IDisposable。

- 已重新覆寫 Finalize。

- 已覆寫 Dispose。

- Dispose ( # A1 不是公用、密封或命名的 Dispose。

- Dispose (bool) 不受保護、虛擬或未密封。

- 在未密封的類型中，Dispose ( # A1 必須呼叫 Dispose (true) 。

- 若為非密封類型，Finalize 實並不會呼叫 Dispose (bool) 或 case 類別完成項。

  違規任何一個模式將會觸發此警告。

  每個未密封的根 IDisposable 類型都必須提供本身受保護的虛擬 void Dispose (bool) 方法。 Dispose ( # A1 應呼叫 Dispose (true) 且 Finalize 應該呼叫 Dispose (false) 。 如果您要建立未密封的根 IDisposable 型別，您必須定義 Dispose (bool) 並加以呼叫。 如需詳細資訊，請參閱 .NET Framework 檔的[架構設計指導方針](https://msdn.microsoft.com/library/5fbcaf4f-ea2a-4d20-b0d6-e61dee202b4b)一節中的[清除非受控資源](https://msdn.microsoft.com/library/a17b0066-71c2-4ba4-9822-8e19332fc213)。

## <a name="rule-description"></a>規則描述
 所有的 IDisposable 類型都需正確地實作 Dispose 模式。

## <a name="how-to-fix-violations"></a>如何修正違規
 檢查您的程式碼，並判斷下列哪一個解決方法會修正此違規。

- 請從所執行的介面清單中移除 IDisposable {0} ，並改為覆寫基類處置的實作為。

- 從型別移除完成項 {0} ，覆寫 Dispose (bool 處置) ，然後將完成邏輯放在程式碼路徑中，其中 ' dispose ' 為 false。

- 移除 {0} 、覆寫 dispose (bool 處置) ，然後在程式碼路徑中放置 dispose 邏輯，其中 ' 處置 ' 為 true。

- 確定 {0} 已宣告為公用並密封。

- 重新命名 {0} 為 ' Dispose '，並確定其已宣告為公用並密封。

- 請確定 {0} 已宣告為受保護、虛擬和未密封。

- 進行修改， {0} 使其呼叫 Dispose (true) ，然後呼叫 GC。SuppressFinalize 目前物件實例 () 中的 ' this ' 或 ' Me ' [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] ，然後傳回。

- 修改， {0} 使其呼叫 Dispose (false) 然後傳回。

- 如果您要撰寫未密封的根 IDisposable 類別，請確定 IDisposable 的執行遵循本節稍早所述的模式。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。

## <a name="pseudo-code-example"></a>虛擬程式碼範例
 下列虛擬程式碼提供如何在使用 managed 和原生資源的類別中，執行 Dispose (bool) 的一般範例。

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
