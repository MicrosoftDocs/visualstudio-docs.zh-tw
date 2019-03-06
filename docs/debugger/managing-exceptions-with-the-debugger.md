---
title: 使用偵錯工具管理例外狀況 |Microsoft Docs
ms.custom: seodec18
ms.date: 10/09/2018
ms.topic: conceptual
f1_keywords:
- vs.debug.exceptions
- vs.debug.exceptions.find
dev_langs:
- CSharp
- VB
- FSharp
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b83cb026bec6d33490517e5703a042b4a8e2434c
ms.sourcegitcommit: cdcbf254db737d42275e95de4ffc4f8c14e87e00
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57428696"
---
# <a name="manage-exceptions-with-the-debugger-in-visual-studio"></a>使用 Visual Studio 中偵錯工具管理例外狀況

例外狀況是程式執行時發生之錯誤狀態的指示。 哪些例外狀況或中斷，例外狀況的集合，您可以告知偵錯工具和您想在此時偵錯工具中斷 （亦即，在偵錯工具中暫停）。 當偵錯工具中斷時，它會顯示您已在擲回例外狀況。 您也可以新增或刪除的例外狀況。 使用 Visual Studio 中開啟的方案，使用**偵錯 > Windows > 例外狀況設定**來開啟**例外狀況設定**視窗。

提供回應最重要的例外狀況的處理常式。 如果您需要了解如何新增例外狀況處理常式，請參閱[修正 bug，藉由撰寫更好C#程式碼](../debugger/write-better-code-with-visual-studio.md)。 此外，了解如何設定偵錯工具一定中斷執行，某些例外狀況。

發生例外狀況時，偵錯工具都會將例外狀況訊息寫入至 [輸出] 視窗。 它可能會中斷執行，在下列情況下，當：

- 例外狀況會擲回未處理。
- 偵錯工具會設定為在叫用任何處理常式之前中斷執行。
- 您已設定[Just My Code](../debugger/just-my-code.md)，而且偵錯工具已設定為任何使用者程式碼中未處理的例外狀況中斷。

> [!NOTE]
> ASP.NET 具有最上層例外狀況處理常式，這會在瀏覽器中顯示錯誤頁面。 它不會中斷執行，除非**Just My Code**已開啟。 如需範例，請參閱[告知偵錯工具在使用者未處理的例外狀況繼續](#BKMK_UserUnhandled)如下。

<!-- Two consecutive notes are intentional here...-->

> [!NOTE]
> 在 Visual Basic 應用程式中，即使使用 On Error 樣式的錯誤處理常式，偵錯工具還是會將所有錯誤都當成例外狀況管理。

## <a name="tell-the-debugger-to-break-when-an-exception-is-thrown"></a>告知偵錯工具中斷擲回例外狀況時

偵錯工具可以在例外狀況擲回位置，中斷執行，因此您可能會在叫用處理常式之前，檢查例外狀況。

在 **例外狀況設定**視窗 (**偵錯 > Windows > 例外狀況設定**)，展開節點類別的例外狀況，例如**Common Language Runtime 例外狀況**. 然後選取核取方塊，該類別中，內的特定例外狀況，例如**System.AccessViolationException**。 您也可以選取例外狀況的整個類別。

![核取了 AccessViolationException](../debugger/media/exceptionsettingscheckaccess.png "ExceptionSettingsCheckAccess")

> [!TIP]
> 您可以使用，以尋找特定的例外狀況**搜尋**中的視窗**例外狀況設定**工具列上或使用搜尋來篩選特定命名空間 (例如**System.IO**)。

如果您選取中的例外狀況**例外狀況設定** 視窗中，偵錯工具會中斷執行每當擲回例外狀況是，不論是否處理它。 現在該例外狀況稱為第一次出現的例外狀況。 例如，以下是幾個情節：

- 在下列 C# 主控台應用程式中，Main 方法會在 **try/catch** 區塊內部擲回 `try/catch`。

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

  如果您有**AccessViolationException**簽入**例外狀況設定**，執行會在中斷`throw`當您在偵錯工具中執行此程式碼行。 然後，您可以繼續執行。 主控台應該會顯示這兩行：

  ```cmd
  caught exception
  goodbye
  ```

  但不會顯示`here`列。

- C#主控台應用程式所參考的類別，有兩種方法的類別程式庫。 其中一種方法會擲回例外狀況，並處理它，而第二個方法會擲回相同的例外狀況，但不會加以處理。

  ```csharp
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

  如果您有**AccessViolationException**簽入**例外狀況設定**，執行會在中斷`throw`兩者中**throwunhandledexception （)** 和**Throwunhandledexception**當您在偵錯工具中，會在執行此程式碼時。

若要將例外狀況設定還原為預設值，請選擇**將清單還原為預設設定**按鈕：

![還原在例外狀況設定的預設值](../debugger/media/restoredefaultexceptions.png "RestoreDefaultExceptions")

## <a name="BKMK_UserUnhandled"></a>告訴使用者未處理的例外狀況繼續偵錯工具

如果您正在偵錯使用.NET 或 JavaScript 程式碼[Just My Code](../debugger/just-my-code.md)，您可以告知偵錯工具，以避免中斷使用者程式碼中未處理，但其他地方處理的例外狀況。

1. 在 [**例外狀況設定**] 視窗中，以滑鼠右鍵按一下資料行標籤，開啟捷徑功能表，然後按**顯示的資料行 > 其他動作**。 (如果您已關閉**Just My Code**，您不會看到此命令。)第三個資料行名為**其他動作**隨即出現。

   ![其他動作 資料行](../debugger/media/additionalactionscolumn.png "AdditionalActionsColumn")

   顯示的例外狀況**當使用者程式碼中未處理時繼續**本專欄中，在偵錯工具會繼續如果使用者程式碼中未處理例外狀況，但會在外部處理。

2. 若要變更此設定特定的例外狀況，請選取例外狀況，以顯示捷徑功能表，以滑鼠右鍵按一下並選取**未處理時繼續使用者程式碼中**。 您可能也變更整個例外狀況，例如整個 Common Language Runtime 例外狀況分類的設定）。

   ![* * 時，繼續在使用者程式碼 * * 設定中未處理](../debugger/media/continuewhenunhandledinusercodesetting.png "ContinueWhenUnhandledInUserCodeSetting")

例如，ASP.NET web 應用程式處理的例外狀況將它們轉換成 HTTP 500 狀態碼 ([ASP.NET Web API 中處理的例外狀況](http://www.asp.net/web-api/overview/error-handling/exception-handling))，這可能無法幫助您判斷例外狀況的來源。 在下列範例中，使用者程式碼會呼叫擲回 `String.Format()` 的 <xref:System.FormatException>。 執行中斷，如下所示：

![使用者將會中斷&#45;未處理例外狀況](../debugger/media/exceptionunhandledbyuser.png "ExceptionUnhandledByUser")

## <a name="add-and-delete-exceptions"></a>新增及刪除例外狀況

您可以新增及刪除例外狀況。 若要刪除的例外狀況類型類別目錄，選取 例外狀況，然後選擇**從清單中刪除選取的例外狀況**上的按鈕 （減號）**例外狀況設定**工具列。 或者您可以以滑鼠右鍵按一下 例外狀況，然後選取**刪除**從捷徑功能表。 刪除例外狀況有相同的效果為未核取，也就是它擲回時，不會中斷偵錯工具。

若要新增例外狀況：

1. 在 [**例外狀況設定**] 視窗中，選取其中一個例外狀況類別 (例如**Common Language Runtime**)。

2. 選擇**例外狀況新增至選取的分類**（加號） 按鈕。

   ![* * 選取的類別目錄 按鈕以新增例外狀況](../debugger/media/addanexceptiontotheselectedcategorybutton.png "AddAnExceptionToTheSelectedCategoryButton")

3. 輸入例外狀況的名稱 (例如**System.UriTemplateMatchException**)。

   ![輸入例外狀況名稱](../debugger/media/typetheexceptionname.png "TypeTheExceptionName")

   例外狀況會新增至清單 （依字母順序），並會自動核取。

若要加入的 GPU 記憶體存取例外狀況、 JavaScript 執行階段例外狀況或 Win32 例外狀況類別的例外狀況，包括錯誤碼和描述。

> [!TIP]
> 請檢查您的拼字！ [例外狀況設定] 視窗並不會檢查新增的例外狀況是否存在。 因此如果您鍵入 **Sytem.UriTemplateMatchException**，您會得到針對該例外狀況 (而非針對 **System.UriTemplateMatchException**) 的項目。

例外狀況設定會保存在此方案的 .suo 檔案中，因此可套用至特定的方案中。 您無法在不同方案間重複使用特定的例外狀況設定。 現在會保存已加入的例外狀況;不是 已刪除的例外狀況。 您可能會加入例外狀況，關閉並重新開啟方案，以及例外狀況仍會發生。 但是，如果您刪除例外狀況，然後關閉/重新開啟此方案，則該例外狀況會重新出現。

[例外狀況設定]  視窗在 C# 中支援泛型例外狀況類型，但在 Visual Basic 中不支援。 若要中斷類似 `MyNamespace.GenericException<T>`的例外狀況，您必須新增例外狀況為 [MyNamespace.GenericException'1] 。 也就是說，如果您已建立此程式碼類似的例外狀況：

```csharp
public class GenericException<T> : Exception
{
    public GenericException() : base("This is a generic exception.")
    {
    }
}
```

您可以加入的例外狀況**例外狀況設定**使用上一個程序：

![加入泛型例外狀況](../debugger/media/addgenericexception.png "AddGenericException")

## <a name="add-conditions-to-an-exception"></a>將條件加入至例外狀況

使用**例外狀況設定**視窗來設定條件的例外狀況。 目前支援的條件包括要包含或排除例外狀況的模組名稱。 藉由設定模組名稱做為條件，您可以選擇只在特定的程式碼模組上例外狀況中斷。 您也可以選擇以避免在特定的模組。

> [!NOTE]
> 將條件加入至例外狀況從開始支援[!include[vs_dev15](../misc/includes/vs_dev15_md.md)]。

若要新增條件式的例外狀況：

1. 選擇**編輯條件**按鈕在例外狀況設定] 視窗中，或以滑鼠右鍵按一下 [例外狀況，然後選擇**編輯條件**。

   ![例外狀況的條件](../debugger/media/dbg-conditional-exception.png "DbgConditionalException")

2. 若要加入例外狀況需要額外的條件，請選取**加入條件**對每個新的條件。 會顯示其他條件線。

   ![例外狀況的額外條件](../debugger/media/extraconditionsforanexception.png "ExtraConditionsForAnException")

3. 每個條件列，請輸入名稱的模組，並變更比較運算子清單，來**Equals**或是**Not Equals**。 您可以指定萬用字元 (**\\\***) 指定多個模組的名稱。

4. 如果您要刪除條件，請選擇**X**條件列的結尾。

## <a name="see-also"></a>另請參閱

- [於例外狀況之後繼續執行](../debugger/continuing-execution-after-an-exception.md)<br/>
- [如何：在發生例外狀況後檢查系統程式碼](../debugger/how-to-examine-system-code-after-an-exception.md)<br/>
- [如何：使用原生執行階段檢查](../debugger/how-to-use-native-run-time-checks.md)<br/>
- [不使用 C 執行階段程式庫進行執行階段檢查](../debugger/using-run-time-checks-without-the-c-run-time-library.md)<br/>
- [偵錯工具簡介](../debugger/debugger-feature-tour.md)
