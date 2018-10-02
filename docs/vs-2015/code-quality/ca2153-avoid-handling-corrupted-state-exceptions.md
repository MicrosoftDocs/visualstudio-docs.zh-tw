---
title: CA2153： 避免處理損毀狀態例外狀況 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 418cc9cb-68ad-47e9-a6c8-a48b9c35db45
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: ff16046a115a7a21939ef33fa06f6a81ec56921c
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2018
ms.locfileid: "47588400"
---
# <a name="ca2153-avoid-handling-corrupted-state-exceptions"></a>CA2153：避免處理損毀狀態例外狀況
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[CA2153： 避免處理損毀狀態例外狀況](https://docs.microsoft.com/visualstudio/code-quality/ca2153-avoid-handling-corrupted-state-exceptions)。

|||
|-|-|
|TypeName|AvoidHandlingCorruptedStateExceptions|
|CheckId|CA2153|
|分類|Microsoft.Security|
|中斷變更|非中斷|

## <a name="cause"></a>原因
 [損毀狀態例外狀況 (CSE)](https://msdn.microsoft.com/magazine/dd419661.aspx)指出記憶體損毀存在於您的程序。 如果攻擊者將攻擊放入損毀的記憶體區域，則攔截這些處理序而非讓它們損毀，會導致安全性弱點。

## <a name="rule-description"></a>規則描述
 CSE 指出處理序的狀態已損毀且系統不予攔截。 在損毀狀態的案例中，如果以適當的 `HandleProcessCorruptedStateExceptions` 屬性標示方法，一般的處理常式只會攔截例外狀況。 根據預設， [Common Language Runtime (CLR)](https://msdn.microsoft.com/library/8bs2ecf4.aspx)將 Cse 不叫用 catch 處理常式。

 允許處理序損毀卻不攔截這類例外狀況，是最安全的選項，因為就算是記錄程式碼都會允許攻擊者攻擊記憶體損毀錯誤。

 這個警告會在以攔截所有例外狀況之一般處理常式攔截 CSE 時觸發，例如 catch(exception) 或 catch(no exception specification)。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要處理這種警告，您應該執行下列其中一項：

 1. 移除`HandleProcessCorruptedStateExceptions`屬性。 這會還原到預設的執行階段行為，不將 CSE 傳遞至 catch 處理常式。

 2. 移除一般 catch 處理常式，而非移除攔截特定例外狀況類型的處理常式。  這可能包括假設處理常式程式碼可以安全處理它們的 CSE (非常罕見)。

 3. 在確保例外狀況會傳遞至呼叫端並結束執行中處理序的 catch 處理常式中，重新擲回 CSE。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。

## <a name="pseudo-code-example"></a>虛擬程式碼範例

### <a name="violation"></a>違規
 下列虛擬程式碼會說明這個規則偵測到的模式。

```
[HandleProcessCorruptedStateExceptions]
//method to handle and log CSE exceptions
void TestMethod1()
{
    try
    {
        FileStream fileStream = new FileStream("name", FileMode.Create);
    }
    catch (Exception e)
    {
        // Handle error
    }
}
```

### <a name="solution-1"></a>解決方案 1
 移除 HandleProcessCorruptedExceptions 屬性以確保不處理例外狀況。

```
void TestMethod1()
{
    try
    {
        FileStream fileStream = new FileStream("name", FileMode.Create);
    }
    catch (IOException e)
    {
        // Handle error
    }
    catch (UnauthorizedAccessException e)
    {
        // Handle error
    }
}
```

### <a name="solution-2"></a>解決方案 2
 移除一般 catch 處理常式，只攔截特定的例外狀況類型。

```
void TestMethod1()
{
    try
    {
        FileStream fileStream = new FileStream("name", FileMode.Create);
    }
    catch (IOException e)
    {
        // Handle error
    }
    catch (UnauthorizedAccessException e)
    {
        // Handle error
    }
}
```

### <a name="solution-3"></a>解決方案 3
 重新擲回例外狀況。

```
void TestMethod1()
{
    try
    {
        FileStream fileStream = new FileStream("name", FileMode.Create);
    }
    catch (Exception e)
    {
        // Handle error
        throw;
    }
}
```



