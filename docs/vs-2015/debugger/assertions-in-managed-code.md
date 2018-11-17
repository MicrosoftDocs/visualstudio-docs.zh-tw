---
title: Managed 程式碼中的判斷提示 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], assertions in managed code
- Trace.Assert method
- debugging managed code, assertions
- Debug.Assert method
- Debug.Listeners property
- assertions, side effects
- Trace.Listeners property
- assertions, managed code
ms.assetid: 70ab2522-6486-4076-a1a9-e0f11cd0f3a1
caps.latest.revision: 32
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c47b2b05ab358826d594d0c6ef29c1b50e0a529f
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51806538"
---
# <a name="assertions-in-managed-code"></a>Managed 程式碼中的判斷提示
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

判斷提示 (或 `Assert` 陳述式) 可以測試條件，您可以將此條件指定為 `Assert` 陳述式的引數。 如果條件判斷值為 true，則不會執行任何動作。 如果條件判斷值為 false，則判斷提示會失敗。 如果您是以偵錯組建執行，則您的程式將進入中斷模式。  
  
##  <a name="BKMK_In_this_topic"></a>本主題內容  
 [System.Diagnostics 命名空間中的判斷提示](#BKMK_Asserts_in_the_System_Diagnostics_Namespace)  
  
 [Debug.Assert 方法](#BKMK_The_Debug_Assert_method)  
  
 [Debug.Assert 的副作用](#BKMK_Side_effects_of_Debug_Assert)  
  
 [追蹤和偵錯需求](#BKMK_Trace_and_Debug_Requirements)  
  
 [Assert 引數](#BKMK_Assert_arguments)  
  
 [自訂 Assert 的行為](#BKMK_Customizing_Assert_behavior)  
  
 [在組態檔中設定判斷提示](#BKMK_Setting_assertions_in_configuration_files)  
  
##  <a name="BKMK_Asserts_in_the_System_Diagnostics_Namespace"></a> System.Diagnostics 命名空間中的判斷提示  
 在 Visual Basic 和 Visual C# 中，您可以從位於 `Assert` 命名空間中的 <xref:System.Diagnostics.Debug> 或 <xref:System.Diagnostics.Trace> 使用 <xref:System.Diagnostics> 方法。 <xref:System.Diagnostics.Debug> 類別方法未包含在程式的發行版本中，因此不會增加發行程式碼的大小或減緩其速度。  
  
 C++ 不支援 <xref:System.Diagnostics.Debug> 類別方法。 您可以使用來達到相同的效果<xref:System.Diagnostics.Trace>類別搭配條件式編譯，例如`#ifdef DEBUG`...`#endif`.  
  
 [本主題內容](#BKMK_In_this_topic)  
  
##  <a name="BKMK_The_Debug_Assert_method"></a> Debug.Assert 方法  
 您可以隨意使用 <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> 方法測試程式碼正確時應為 true 的條件。 例如，假設您撰寫了整數除法函式。 依據數學規則，除數不可為零。 您可以使用判斷提示測試這項條件：  
  
```vb  
Function IntegerDivide(ByVal dividend As Integer, ByVal divisor As Integer) As Integer  
    Debug.Assert(divisor <> 0)  
    Return CInt(dividend / divisor)  
End Function  
```  
  
```csharp  
int IntegerDivide ( int dividend , int divisor )  
    { Debug.Assert ( divisor != 0 );  
        return ( dividend / divisor ); }  
```  
  
 您在偵錯工具下執行此程式碼時，將會評估判斷提示陳述式，但是在發行版本中則不會進行比較，因此不會有額外的負荷。  
  
 以下是另一個範例。 您擁有實作檢查帳戶的類別，如下所示：  
  
```vb  
Dim amount, balance As Double  
balance = savingsAccount.balance  
Debug.Assert(amount <= balance)  
SavingsAccount.Withdraw(amount)  
```  
  
```csharp  
float balance = savingsAccount.Balance;  
Debug.Assert ( amount <= balance );  
savingsAccount.Withdraw ( amount );  
```  
  
 在您從帳戶中提領現金之前，想要先確認帳戶餘額足夠供應您預備提領的金額。 您可以撰寫判斷提示檢查餘額：  
  
```vb  
Dim amount, balance As Double  
balance = savingsAccount.balance  
Trace.Assert(amount <= balance)  
SavingsAccount.Withdraw(amount)  
```  
  
```csharp  
float balance = savingsAccount.Balance;  
Trace.Assert ( amount <= balance );  
savingsAccount.Withdraw ( amount );  
```  
  
 請注意，當您建立程式碼的發行版本時，對 <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> 方法的呼叫就會消失。 這表示，在發行版本內，檢查餘額的呼叫將會消失。 若要解決這個問題，您應該將 <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> 取代為 <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName>，後者不會在發行版本中消失：  
  
 呼叫 <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName> 與呼叫 <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> 不同，前者會增加發行版本的額外負荷。  
  
 [本主題內容](#BKMK_In_this_topic)  
  
##  <a name="BKMK_Side_effects_of_Debug_Assert"></a> Debug.Assert 的副作用  
 當您使用 <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> 時，請確認 `Assert` 內的任何程式碼都不會在 `Assert` 移除後變更程式的結果。 否則，您可能意外引入只會出現在程式發行版本中的 Bug。 處理包含函式或程序呼叫的判斷提示時要特別小心，例如下面的範例：  
  
```vb  
' unsafe code  
Debug.Assert (meas(i) <> 0 )  
```  
  
```csharp  
// unsafe code  
Debug.Assert (meas(i) != 0 );  
```  
  
 這個 <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> 用法乍看之下好像很安全，但假設每次呼叫 meas 函式時都會更新計數器。 當您建置發行版本時，將會去除這個 meas 呼叫，如此計數器就不會更新。 這是具有副作用的函式範例。 去除具有副作用的函式呼叫將導致只出現在發行版本中的 Bug。 若要避免這類問題，請不要在 <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> 陳述式中放置函式呼叫。 請改用暫存變數：  
  
```vb  
temp = meas( i )  
Debug.Assert (temp <> 0)  
```  
  
```csharp  
temp = meas( i );  
Debug.Assert ( temp != 0 );  
```  
  
 即使是使用 <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName> 時，您仍然會想要避免將函式呼叫放入 `Assert` 陳述式中。 這類呼叫應該是安全的，因為發行組建中不會去除 <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName> 陳述式。 但是，如果您養成不使用這類建構的習慣，使用 <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> 時就比較不會犯錯。  
  
 [本主題內容](#BKMK_In_this_topic)  
  
##  <a name="BKMK_Trace_and_Debug_Requirements"></a> 追蹤和偵錯需求  
 如果您使用 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 精靈建立專案，根據預設，TRACE 符號會同時在發行和偵錯組態中定義。 根據預設，DEBUG 符號只會在偵錯組建中定義。  
  
 否則為了要讓 <xref:System.Diagnostics.Trace> 方法運作，您程式的原始程式檔頂端就必須要有下列其中一個項目：  
  
- `#Const TRACE = True` (在 Visual Basic 中)  
  
- `#define TRACE` (在 Visual C# 和 C++ 中)  
  
  或者，您的程式必須是使用 TRACE 選項所建置：  
  
- `/d:TRACE=True` (在 Visual Basic 中)  
  
- `/d:TRACE` (在 Visual C# 和 C++ 中)  
  
  如果您需要在 C# 或 Visual Basic 的發行組建中使用 Debug 方法，則必須在發行組態中定義 DEBUG 符號。  
  
  C++ 不支援 <xref:System.Diagnostics.Debug> 類別方法。 您可以使用來達到相同的效果<xref:System.Diagnostics.Trace>類別搭配條件式編譯，例如`#ifdef DEBUG`...`#endif`. 您可以定義中的這些符號**\<專案 > 屬性頁** 對話方塊。 如需詳細資訊，請參閱 <<c0> [ 變更 Visual Basic 偵錯組態的專案設定](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)或是[變更 C 或 c + + 偵錯組態的專案設定](../debugger/project-settings-for-a-cpp-debug-configuration.md)。  
  
##  <a name="BKMK_Assert_arguments"></a> Assert 引數  
 <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName> 和 <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> 最多可接受三個引數。 第一個引數是強制性的，代表您要檢查的條件。 如果您呼叫<xref:System.Diagnostics.Trace.Assert%28System.Boolean%29?displayProperty=fullName>或<xref:System.Diagnostics.Debug.Assert%28System.Boolean%29?displayProperty=fullName>只有一個引數，與`Assert`方法會檢查條件，和如果結果為 false，則會輸出的呼叫堆疊，內容**輸出**視窗。 下列範例將示範 <xref:System.Diagnostics.Trace.Assert%28System.Boolean%29?displayProperty=fullName> 和 <xref:System.Diagnostics.Debug.Assert%28System.Boolean%29?displayProperty=fullName>：  
  
```vb  
Debug.Assert(stacksize > 0)  
Trace.Assert(stacksize > 0)  
```  
  
```csharp  
Debug.Assert ( stacksize > 0 );  
Trace.Assert ( stacksize > 0 );   
```  
  
 若出現第二個和第三個引數，這兩個引數必須為字串。 如果您使用兩個或三個引數呼叫 <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName> 或 <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName>，第一個引數就是條件。 方法會檢查條件，如果結果是 false，就會輸出第二個和第三個字串。 下列範例將示範搭配兩個引數使用的 <xref:System.Diagnostics.Debug.Assert%28System.Boolean%2CSystem.String%29?displayProperty=fullName> 和 <xref:System.Diagnostics.Trace.Assert%28System.Boolean%2CSystem.String%29?displayProperty=fullName>：  
  
```vb  
Debug.Assert(stacksize > 0, "Out of stack space")  
Trace.Assert(stacksize > 0, "Out of stack space")  
```  
  
```csharp  
Debug.Assert ( stacksize > 0, "Out of stack space" );  
Trace.Assert ( stacksize > 0, "Out of stack space" );  
```  
  
 下列範例將示範 <xref:System.Diagnostics.Debug.Assert%2A> 和 <xref:System.Diagnostics.Trace.Assert%2A>：  
  
```vb  
Debug.Assert(stacksize > 0, "Out of stack space. Bytes left:" , Format(size, "G"))  
Trace.Assert(stacksize > 0, "Out of stack space. Bytes left:" , Format(size, "G"))  
Trace.Assert(stacksize > 0, "Out of stack space. Bytes left:", "inctemp failed on third call" )  
```  
  
```csharp  
Debug.Assert ( stacksize > 100, "Out of stack space" , "Failed in inctemp" );  
Trace.Assert ( stacksize > 0, "Out of stack space", "Failed in inctemp" );   
```  
  
 [本主題內容](#BKMK_In_this_topic)  
  
##  <a name="BKMK_Customizing_Assert_behavior"></a> 自訂 Assert 的行為  
 如果您在使用者介面模式中，執行您的應用程式`Assert`方法會顯示**判斷提示失敗**對話方塊時的條件失敗。 判斷提示失敗時，發生的動作就會受<xref:System.Diagnostics.Debug.Listeners%2A>或<xref:System.Diagnostics.Trace.Listeners%2A>屬性。  
  
 自訂輸出行為的方法包括將 <xref:System.Diagnostics.TraceListener> 物件加入至 `Listeners` 集合內、從 <xref:System.Diagnostics.TraceListener> 集合內移除 `Listeners`，或覆寫現有 <xref:System.Diagnostics.TraceListener.Fail%2A?displayProperty=fullName> 的 `TraceListener` 方法，讓它擁有不同的行為。  
  
 例如，您可以覆寫<xref:System.Diagnostics.TraceListener.Fail%2A?displayProperty=fullName>方法來寫入事件記錄檔，而不是顯示**判斷提示失敗** 對話方塊。  
  
 若要以這種方式自訂輸出，您的程式必須包含接聽程式，而且必須繼承自 <xref:System.Diagnostics.TraceListener>，並覆寫其 <xref:System.Diagnostics.TraceListener.Fail%2A?displayProperty=fullName> 方法。  
  
 如需詳細資訊，請參閱 <<c0> [ 追蹤接聽項](http://msdn.microsoft.com/library/444b0d33-67ea-4c36-9e94-79c50f839025)。  
  
 [本主題內容](#BKMK_In_this_topic)  
  
##  <a name="BKMK_Setting_assertions_in_configuration_files"></a> 在組態檔中設定判斷提示  
 您可以在程式組態檔中設定判斷提示，就像在程式碼中一樣。 如需詳細資訊，請參閱 <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName>或 <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName>。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName>   
 <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName>   
 [偵錯工具安全性](../debugger/debugger-security.md)   
 [追蹤和檢測應用程式](http://msdn.microsoft.com/library/773b6fc4-9013-4322-b728-5dec7a72e743)   
 [如何：使用追蹤和偵錯進行條件式編譯](http://msdn.microsoft.com/library/56d051c3-012c-42c1-9a58-7270edc624aa)   
 [C#、F# 和 Visual Basic 專案類型](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [偵錯 Managed 程式碼](../debugger/debugging-managed-code.md)



