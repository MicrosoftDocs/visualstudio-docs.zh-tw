---
title: 使用偵錯工具管理例外狀況 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.exceptions
- vs.debug.exceptions.find
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
helpviewer_keywords:
- run-time errors
- exception handling, during debugging
- errors [debugger]
- debugger, runtime errors
- On Error-style error handlers
- exceptions, Win32
- run-time errors, debugging
- Win32, exceptions
- run time, exceptions
- error handling
- debugging [Visual Studio], exception handling
- common language runtime, exceptions
- native run-time checks
- exceptions, debugging
ms.assetid: 43a77fa8-37d0-4c98-a334-0134dbca4ece
caps.latest.revision: 40
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 45b681b8d146fcc4ca8b056cd94bb0ef65cae826
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "75918950"
---
# <a name="managing-exceptions-with-the-debugger"></a>使用偵錯工具管理例外狀況
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

例外狀況是程式執行時發生之錯誤狀態的指示。 您可以也應該提供可對最重要例外狀況回應的處理常式，但請務必了解如何設定偵錯工具以針對您想要查看的例外狀況來中斷。  
  
 發生例外狀況時，偵錯工具都會將例外狀況訊息寫入至 [輸出] 視窗。 在下列情況下，它可能會中斷執行：  
  
- 當例外狀況已擲回且未處理。  
  
- 當偵錯工具設定為在叫用任何處理常式之前就已擲回例外狀況時，立即中斷執行。  
  
- 如果您曾設定 [Just My Code](../debugger/just-my-code.md)，且偵錯工具設定為在非由使用者程式碼所處理的任何例外狀況時中斷。  
  
> [!NOTE]
> ASP.NET 具有最上層例外狀況處理常式，這會在瀏覽器中顯示錯誤頁面。 它不會中斷執行，除非 [Just My Code] **** 已開啟。 如需範例，請參閱下列 [Setting the debugger to continue on user-unhandled exceptions](../debugger/managing-exceptions-with-the-debugger.md#BKMK_UserUnhandled) 。  
  
> [!NOTE]
> 在 Visual Basic 應用程式中，即使使用 On Error 樣式的錯誤處理常式，偵錯工具還是會將所有錯誤都當成例外狀況管理。  
  
## <a name="managing-exceptions-with-the-exception-settings-window"></a>藉由 [例外狀況設定] 視窗管理例外狀況  
 您可以使用 [例外狀況設定] **** 視窗來指定哪些例外狀況 (或例外狀況的集合) 會導致偵錯工具中斷，並指定在哪個點上您會想要中斷。 您可以新增或刪除例外狀況，或指定要中斷的例外狀況。 在經由 [偵錯] / [Windows] / [例外狀況設定] **** 開啟方案時，此視窗隨即開啟。  
  
 您可以使用 [例外狀況設定] **** 工具列中的 [搜尋] **** 視窗，尋找特定的例外狀況，或使用搜尋來篩選特定命名空間 (例如 [System.IO] ****)。  
  
### <a name="setting-the-debugger-to-break-when-an-exception-is-thrown"></a>設定偵錯工具在擲回例外狀況時中斷  
 偵錯工具可以在擲回例外狀況的位置中斷執行，讓您可以在叫用處理常式之前有機會檢查例外狀況。  
  
 在 [例外狀況設定] **** 視窗中，展開例外狀況分類的節點 (例如，[Common Language Runtime 例外狀況] **** 表示.NET 例外狀況)，並選取該類別目錄內的特定例外狀況核取方塊 (例如 [System.AccessViolationException] ****)。 您也可以選取例外狀況的整個類別。  
  
 ![已檢查的 AccessViolationException](../debugger/media/exceptionsettingscheckaccess.png "ExceptionSettingsCheckAccess")  
  
 如果您核取指定的例外狀況，則偵錯工具的執行會在任何擲回例外狀況的地方中斷，無論它是已處理或未處理的。 此時該例外狀況稱為第一個可能發生的例外狀況。 例如，以下是幾個情節：  
  
1. 在下列 C# 主控台應用程式中，Main 方法會在 **try/catch** 區塊內部擲回 `try/catch` ：  
  
   ```csharp  
   static void Main(string[] args)  
   {  
       try  
       {  
           throw new AccessViolationException();  
           Console.WriteLine("here");  
       }  
       catch (Exception e)  
       {  
           Console.WriteLine("caught exception");  
       }  
       Console.WriteLine("goodbye");  
   }  
   ```  
  
    當您在偵錯工具中執行此程式碼時，如果您在 [例外狀況設定] **try/catch** 中核取了 [AccessViolationException] ****，則執行會在 `throw` 行中斷。 然後，您可以繼續執行。 主控台應該會顯示這兩行：  
  
   ```  
   caught exception  
   goodbye  
   ```  
  
    但它不會顯示 `here` 行。  
  
2. C# 主控台應用程式參考類別庫的類別有兩種方法，其中的一種方法會擲回例外狀況並加以處理，而第二個方法會擲回相同的例外狀況，但不會加以處理：  
  
   ```vb  
   public class Class1  
   {  
       public void ThrowHandledException()  
       {  
           try  
           {  
               throw new AccessViolationException();  
           }  
           catch (AccessViolationException ave)  
           {  
               Console.WriteLine("caught exception" + ave.Message);  
           }  
       }  
  
       public void ThrowUnhandledException()  
       {  
           throw new AccessViolationException();  
       }  
   }  
   ```  
  
    以下是主控台應用程式的 Main () 方法：  
  
   ```csharp  
   static void Main(string[] args)  
   {  
       Class1 class1 = new Class1();  
       class1.ThrowHandledException();  
       class1.ThrowUnhandledException();  
   }  
   ```  
  
    如果您已 **了 [accessviolationexception** 簽入 **例外狀況設定**，當您在偵錯工具執行中執行此程式碼時，將會在 `throw` **ThrowHandledException ( # B1 ** 和 **ThrowUnhandledException ( # B3 **中的那一行中斷。  
  
   如果您想要將例外狀況設定還原為預設值，您可以按一下工具列上的 [還原] **** 按鈕：  
  
   ![將例外狀況設定還原成預設值](../debugger/media/restoredefaultexceptions.png "RestoreDefaultExceptions")  
  
### <a name="setting-the-debugger-to-continue-on-user-unhandled-exceptions"></a><a name="BKMK_UserUnhandled"></a> 將偵錯工具設定為在使用者未處理的例外狀況時繼續  
 如果您正在偵錯具有 [Just My Code](../debugger/just-my-code.md)的 .NET 或 JavaScript 程式碼，則可以告知偵錯工具不中斷使用者程式碼中未處理，但在其他地方處理的例外狀況。  
  
1. 在 [例外狀況設定] **** 視窗中，開啟內容功能表，方法是在視窗中按一下滑鼠右鍵，然後選取 [顯示行] ****。 (如果您關閉了 [Just My Code] ****，您就不會看到這個命令。)  
  
2. 您應該會看到名為 [其他動作] **** 的第二個資料行。 這個資料行會在特定的例外狀況顯示 [當使用者程式碼中未處理時繼續] **** ，這表示如果在使用者程式碼中未處理例外狀況，但會在外部程式碼中處理，則偵錯工具不會中斷。  
  
3. 您可以針對特定的例外狀況 (選取此例外狀況，以滑鼠右鍵按一下，並選取/取消選取 [當使用者程式碼中未處理時繼續] ****)，或整個例外狀況分類 (例如，所有 Common Language Runtime 例外狀況)，來變更此設定。  
  
   例如，ASP.NET Web 應用程式將例外狀況轉換成 HTTP 500 狀態碼 ([Exception Handling in ASP.NET API (在 ASP.NET 應用程式開發介面中的例外狀況處理)](/aspnet/web-api/overview/error-handling/exception-handling)) 加以處理，這可能無法幫助您判斷例外狀況的來源。 在下列範例中，使用者程式碼會呼叫擲回 `String.Format()` 的 <xref:System.FormatException>。 執行中斷，如下所示：  
  
   ![在使用者&#45;unhanlded 例外狀況時中斷](../debugger/media/exceptionunhandledbyuser.png "ExceptionUnhandledByUser")  
  
### <a name="adding-and-deleting-exceptions"></a>新增及刪除例外狀況  
 您可以新增及刪除例外狀況。 您可以從任何類別目錄刪除任何類型的例外狀況，方法是選取此例外狀況，並按下 [例外狀況設定] **** 工具列上的 [刪除] **** 按鈕 (減號)，或以滑鼠右鍵按一下此例外狀況，然後從內容功能表選取 [刪除] **** 。 刪除例外狀況和未核取例外狀況有相同的效果，也就是偵錯工具並不會在其擲回時中斷。  
  
 若要加入例外狀況：在 [例外狀況設定] **** 視窗中，選取其中一個例外狀況類別 (例如，[Common Language Runtime] ****)，然後按一下 [新增] **** 按鈕。 輸入例外狀況的名稱 (例如 []****)。 此例外狀況隨即加入清單 (依字母順序)，且會自動核取。  
  
 如果您想要將例外狀況加入 [GPU 記憶體存取例外狀況]、[JavaScript 執行階段例外狀況] 或 [Win32 例外狀況] 類別，您需要包含此錯誤碼和描述。  
  
> [!TIP]
> 請檢查您的拼字！ [例外狀況設定] **** 視窗並不會檢查加入的例外狀況是否存在。 因此如果您輸入 **Sytem.UriTemplateMatchException**，您會得到針對該例外狀況的項目 (而非針對 **System.UriTemplateMatchException**)。  
  
 例外狀況設定會保存在此方案的 .suo 檔案中，因此可套用至特定的方案中。 您無法在不同方案間重複使用特定的例外狀況設定。 此時，會保存已加入的例外狀況；但已刪除的例外狀況除外。 換句話說，您可以加入例外狀況，關閉並重新開啟方案，然後該例外狀況仍不會消失。 但是，如果您刪除例外狀況，然後關閉/重新開啟此方案，則該例外狀況會重新出現。  
  
 [例外狀況設定] **** 視窗在 C# 中支援泛型例外狀況類型，但在 Visual Basic 中不支援。 若要中斷類似 `MyNamespace.GenericException<T>`的例外狀況，您必須新增例外狀況為 [MyNamespace.GenericException'1] ****。 也就是說，如果您已經建立這類例外狀況：  
  
```csharp  
public class GenericException<T> : Exception  
{  
    public GenericException() : base("This is a generic exception.")  
    {  
    }  
}  
```  
  
 您可以將此例外狀況加入 [例外狀況設定] **** ，如下所示：  
  
 ![加入泛型例外狀況](../debugger/media/addgenericexception.png "AddGenericException")  
  
## <a name="see-also"></a>另請參閱  
 [例外狀況之後繼續執行](../debugger/continuing-execution-after-an-exception.md)   
 [如何：在例外狀況後檢查系統程式碼](../debugger/how-to-examine-system-code-after-an-exception.md)   
 [如何：使用原生執行時間檢查](../debugger/how-to-use-native-run-time-checks.md)   
 [不使用 C 執行時間程式庫的執行時間檢查](../debugger/using-run-time-checks-without-the-c-run-time-library.md)   
 [例外狀況助理](https://msdn.microsoft.com/library/992892ac-9d52-44cc-bf09-b44bfc5befeb)   
 [偵錯工具基礎](../debugger/debugger-basics.md)
