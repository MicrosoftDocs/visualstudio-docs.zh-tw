---
title: 損毀狀態例外狀況的程式碼分析規則 CA2153
ms.date: 02/19/2019
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4b75e45b8a199265eaefe3a2b3c37ed62039e0eb
ms.sourcegitcommit: 845442e2b515c3ca1e4e47b46cc1cef4df4f08d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/20/2019
ms.locfileid: "56450265"
---
# <a name="ca2153-avoid-handling-corrupted-state-exceptions"></a>CA2153:避免處理損毀狀態例外狀況

|||
|-|-|
|TypeName|AvoidHandlingCorruptedStateExceptions|
|CheckId|CA2153|
|分類|Microsoft.Security|
|中斷變更|非中斷|

## <a name="cause"></a>原因

[損毀狀態例外狀況 (Cse)](https://msdn.microsoft.com/magazine/dd419661.aspx)指出記憶體損毀存在於您的程序。 如果攻擊者將攻擊放入損毀的記憶體區域，則攔截這些處理序而非讓它們損毀，會導致安全性弱點。

## <a name="rule-description"></a>規則描述

CSE 指出處理序的狀態已損毀且系統不予攔截。 在損毀的狀態的案例中，一般的處理常式只攔截到例外狀況如果您標示您的方法與<xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute?displayProperty=fullName>屬性。 根據預設， [Common Language Runtime (CLR)](/dotnet/standard/clr)不 Cse 不叫用 catch 處理常式。

最安全的選項可讓損毀的程序不需攔截這類例外狀況。 就算記錄程式碼，可以允許攻擊者攻擊記憶體損毀錯誤。

這個警告會攔截所有例外狀況，例如，一般處理常式攔截 Cse 時觸發程序`catch (System.Exception e)`或`catch`不含例外狀況參數。

## <a name="how-to-fix-violations"></a>如何修正違規

若要解決這個警告，請執行下列其中一項：

- 移除 <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> 屬性。 這會還原到預設的執行階段行為，不將 CSE 傳遞至 catch 處理常式。

- 移除一般 catch 處理常式，而非移除攔截特定例外狀況類型的處理常式。 這可能包括假設處理常式程式碼能夠安全地處理它們 （罕見） 的 Cse。

- 在 catch 處理常式，傳遞給呼叫端的例外狀況，應該會導致結束執行的處理程序會重新擲回 CSE。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

請勿隱藏此規則的警告。

## <a name="pseudo-code-example"></a>虛擬程式碼範例

### <a name="violation"></a>違規

下列虛擬程式碼會說明這個規則偵測到的模式。

```csharp
[HandleProcessCorruptedStateExceptions]
// Method that handles CSE exceptions.
void TestMethod1()
{
    try
    {
        FileStream fileStream = new FileStream("name", FileMode.Create);
    }
    catch (Exception e)
    {
        // Handle exception.
    }
}
```

### <a name="solution-1---remove-the-attribute"></a>解決方案 1： 移除屬性

移除<xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute>屬性可確保不由您的方法處理損毀狀態例外狀況。

```csharp
void TestMethod1()
{
    try
    {
        FileStream fileStream = new FileStream("name", FileMode.Create);
    }
    catch (Exception e)
    {
        // Handle exception.
    }
}
```

### <a name="solution-2---catch-specific-exceptions"></a>解決方案 2： 擷取特定的例外狀況

移除一般 catch 處理常式，只攔截特定的例外狀況類型。

```csharp
void TestMethod1()
{
    try
    {
        FileStream fileStream = new FileStream("name", FileMode.Create);
    }
    catch (IOException e)
    {
        // Handle IOException.
    }
    catch (UnauthorizedAccessException e)
    {
        // Handle UnauthorizedAccessException.
    }
}
```

### <a name="solution-3---rethrow"></a>解決方案 3： 重新擲回

重新擲回例外狀況。

```csharp
[HandleProcessCorruptedStateExceptions]
void TestMethod1()
{
    try
    {
        FileStream fileStream = new FileStream("name", FileMode.Create);
    }
    catch (Exception e)
    {
        // Rethrow the exception.
        throw;
    }
}
```