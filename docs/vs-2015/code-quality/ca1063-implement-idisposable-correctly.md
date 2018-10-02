---
title: Ca1063： 必須實作 IDisposable 正確 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- ImplementIDisposableCorrectly
- CA1063
helpviewer_keywords:
- CA1063
- ImplementIDisposableCorrectly
ms.assetid: 12afb1ea-3a17-4a3f-a1f0-fcdb853e2359
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: ed6b7832f17a39c145452d0bbfecfbda9be98547
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2018
ms.locfileid: "47588057"
---
# <a name="ca1063-implement-idisposable-correctly"></a>CA1063：必須正確實作 IDisposable
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[ca1063 必須： 實作 IDisposable 正確](https://docs.microsoft.com/visualstudio/code-quality/ca1063-implement-idisposable-correctly)。

|||
|-|-|
|TypeName|ImplementIDisposableCorrectly|
|CheckId|CA1063|
|分類|Microsoft.Design|
|中斷變更|非重大|

## <a name="cause"></a>原因
 `IDisposable` 未正確實作。 此問題的部分原因如下：

-   IDisposable 是在類別中重新實作。

-   完成重新覆寫。

-   Dispose 會覆寫。

-   Dispose （） 不是公用，密封，或名為 Dispose。

-   Dispose （bool） 不受保護、 虛擬或未密封。

-   非密封類型，在 dispose （） 必須呼叫 dispose （true）。

-   對於非密封類型，完成實作不會呼叫其中一個或兩個 dispose （bool） 或案例的類別完成項。

 這些模式的其中任何一個的違規會觸發這個警告。

 每個未密封的根 IDisposable 類型都必須提供它自己受保護虛擬 void dispose （bool） 方法。 Dispose （） 應該呼叫 Dipose(true) 和 Finalize 應該呼叫 dispose （false）。 如果您要建立未密封的根 IDisposable 類型，您必須定義 dispose （bool），並呼叫它。 如需詳細資訊，請參閱 <<c0> [ 清除 Unmanaged 資源向上](http://msdn.microsoft.com/library/a17b0066-71c2-4ba4-9822-8e19332fc213)中[Framework 設計方針](http://msdn.microsoft.com/library/5fbcaf4f-ea2a-4d20-b0d6-e61dee202b4b).NET Framework 文件的章節。

## <a name="rule-description"></a>規則描述
 所有的 IDisposable 類型都需正確地實作 Dispose 模式。

## <a name="how-to-fix-violations"></a>如何修正違規
 檢查您的程式碼，並判斷哪些解決方案可以修正此違規。

-   從所實作的介面清單中移除 IDisposable{0}並改為覆寫基底類別 Dispose 實作。

-   移除型別中的完成項{0}、 覆寫 Dispose (bool disposing)，並放在程式碼路徑的最終處理邏輯，其中 'disposing' 為 false。

-   移除{0}、 覆寫 Dispose (bool disposing)，並將處置邏輯放在程式碼路徑中 'disposing' 為 true。

-   請確認{0}是宣告為公用和密封。

-   重新命名{0}為 'Dispose'，並確定它已宣告為 public 和 sealed。

-   請確定{0}是宣告為 protected、 virtual 和未密封的。

-   修改{0}，因此它會呼叫 dispose （true），然後呼叫 GC。目前的物件執行個體上的 SuppressFinalize ('this' Me' 在[!INCLUDE[vbprvb](../includes/vbprvb-md.md)])，然後傳回。

-   修改{0}，讓它呼叫 dispose （false），然後傳回。

-   如果您正在撰寫的未密封的根 IDisposable 的類別，請確定 IDisposable 實作會遵循本節稍早說明的模式。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。

## <a name="pseudo-code-example"></a>虛擬程式碼範例
 下列虛擬程式碼提供如何應該實作 dispose （bool） 中使用受管理的類別和原生資源的一般範例。

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



