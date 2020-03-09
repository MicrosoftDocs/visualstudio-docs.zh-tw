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
ms.openlocfilehash: 00ad5b41dd0a11661d281f24474b7673ea0a342c
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2020
ms.locfileid: "78409241"
---
# <a name="manage-exceptions-with-the-debugger-in-visual-studio"></a>在 Visual Studio 中使用偵錯工具管理例外狀況

例外狀況是程式執行時發生之錯誤狀態的指示。 您可以告訴偵錯工具要中斷的例外狀況或例外狀況集，以及您想要偵錯工具中斷的時間點（也就是在偵錯工具中暫停）。 當偵錯工具中斷時，它會顯示擲回例外狀況的位置。 您也可以新增或刪除例外狀況。 在 Visual Studio 中開啟方案時，請使用**Debug > Windows > 例外狀況設定**來開啟 [**例外狀況設定**] 視窗。

提供回應最重要例外狀況的處理常式。 如果您需要知道如何新增例外狀況的處理常式，請參閱透過[撰寫更好C#的程式碼來修正 bug](../debugger/write-better-code-with-visual-studio.md)。 此外，您也可以瞭解如何設定偵錯工具，一律中斷執行某些例外狀況。

發生例外狀況時，偵錯工具都會將例外狀況訊息寫入至 [輸出] 視窗。 當下列情況發生時，可能會中斷執行：

- 擲回未處理的例外狀況。
- 偵錯工具設定為在叫用任何處理程式之前中斷執行。
- 您已設定[Just My Code](../debugger/just-my-code.md)，並將偵錯工具設定為在使用者程式碼中未處理的任何例外狀況時中斷。

> [!NOTE]
> ASP.NET 具有最上層例外狀況處理常式，這會在瀏覽器中顯示錯誤頁面。 除非開啟**Just My Code** ，否則不會中斷執行。 如需範例，請參閱下方[的指示偵錯工具繼續進行使用者未處理的例外](#BKMK_UserUnhandled)狀況。

<!-- Two consecutive notes are intentional here...-->

> [!NOTE]
> 在 Visual Basic 應用程式中，即使使用 On Error 樣式的錯誤處理常式，偵錯工具還是會將所有錯誤都當成例外狀況管理。

## <a name="tell-the-debugger-to-break-when-an-exception-is-thrown"></a>告知偵錯工具在擲回例外狀況時中斷

偵錯工具可以在擲回例外狀況的位置中斷執行，因此您可以在叫用處理程式之前檢查例外狀況。

在 [**例外狀況設定**] 視窗中（[**Debug > Windows > 例外狀況設定**]），展開 [例外狀況] 類別的節點，例如 [ **Common Language Runtime 例外**狀況]。 然後選取該類別中特定例外狀況的核取方塊，例如 [ **AccessViolationException**]。 您也可以選取例外狀況的整個類別。

![已檢查 AccessViolationException](../debugger/media/exceptionsettingscheckaccess.png "ExceptionSettingsCheckAccess")

> [!TIP]
> 您可以使用 [**例外狀況設定**] 工具列中的 [**搜尋**] 視窗，尋找特定的例外狀況，或使用搜尋來篩選特定命名空間（例如**System.IO**）。

如果您在 [**例外狀況設定**] 視窗中選取例外狀況，偵錯工具執行將會在擲回例外狀況的任何位置中斷，不論是否已處理。 例外狀況現在稱為第一個可能發生的例外狀況。 例如，以下是幾個情節：

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

  如果您已**AccessViolationException**簽入**例外狀況設定**，則當您在偵錯工具中執行此程式碼時，執行將會在 `throw` 行上中斷。 然後，您可以繼續執行。 主控台應該會顯示這兩行：

  ```cmd
  caught exception
  goodbye
  ```

  但它不會顯示 `here` 行。

- C#主控台應用程式會使用具有兩個方法的類別來參考類別庫。 其中一個方法會擲回例外狀況並加以處理，而第二個方法則擲回相同的例外狀況，但不會處理它。

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

  如果您已**AccessViolationException**簽入**例外狀況設定**，當您在偵錯工具中執行此程式碼時，執行將會在**ThrowHandledException （）** 和**ThrowUnhandledException （）** 中的 `throw` 行中斷。

若要將例外狀況設定還原為預設值，請選擇 [將**清單還原為預設設定**] 按鈕：

![還原例外狀況設定中的預設值](../debugger/media/restoredefaultexceptions.png "RestoreDefaultExceptions")

## <a name="BKMK_UserUnhandled"></a>告訴偵錯工具在使用者未處理的例外狀況時繼續進行

如果您要使用[Just My Code](../debugger/just-my-code.md)來進行 .Net 或 JavaScript 程式碼的偵錯工具，可以告訴偵錯工具避免在使用者程式碼中未處理，但在其他地方處理的例外狀況中斷。

1. 在 [**例外狀況設定**] 視窗中，以滑鼠右鍵按一下資料行標籤以開啟快捷方式功能表，然後選取 [**顯示資料行 > 其他動作**]。 （如果您已關閉**Just My Code**，就不會看到此命令）。會出現名為 [**其他動作**] 的第三個數據行。

   ![其他動作資料行](../debugger/media/additionalactionscolumn.png "AdditionalActionsColumn")

   如需在本專欄的**使用者程式碼中未處理時**顯示 [繼續] 的例外狀況，如果使用者程式碼中未處理該例外狀況，但在外部處理，則偵錯工具會繼續。

2. 若要針對特定的例外狀況變更此設定，請選取例外狀況，以滑鼠右鍵按一下以顯示快捷方式功能表，然後選取 [**當使用者程式碼中未處理時繼續**]。 您也可以變更整個例外狀況類別的設定，例如整個 Common Language Runtime 例外狀況）。

   ![* * 在使用者程式碼中未處理時繼續執行 * * 設定](../debugger/media/continuewhenunhandledinusercodesetting.png "ContinueWhenUnhandledInUserCodeSetting")

例如，ASP.NET web 應用程式會藉由將例外狀況轉換成 HTTP 500 狀態碼（[ASP.NET Web API 中的例外狀況處理](/aspnet/web-api/overview/error-handling/exception-handling)）來處理它們，這可能無法説明您判斷例外狀況的來源。 在下列範例中，使用者程式碼會呼叫擲回 `String.Format()` 的 <xref:System.FormatException>。 執行中斷，如下所示：

![使用者&#45;未處理的例外狀況中斷](../debugger/media/exceptionunhandledbyuser.png "ExceptionUnhandledByUser")

## <a name="add-and-delete-exceptions"></a>新增及刪除例外狀況

您可以新增及刪除例外狀況。 若要從類別中刪除例外狀況類型，請選取例外狀況，然後在 [**例外狀況設定**] 工具列上，選擇 [**從清單中刪除選取的例外**狀況] 按鈕（減號）。 或者，您可以在例外狀況上按一下滑鼠右鍵，然後從快捷方式功能表選取 [**刪除**]。 刪除例外狀況的效果與將例外狀況取消核取相同，這是偵錯工具在擲回時不會中斷的情況。

若要加入例外狀況：

1. 在 [**例外狀況設定**] 視窗中，選取其中一個例外狀況類別（例如，[ **Common Language Runtime**]）。

2. 選擇 [**將例外狀況加入至選取的類別目錄**] 按鈕（加號）。

   ![* * 將例外狀況新增至選取的類別目錄 * * 按鈕](../debugger/media/addanexceptiontotheselectedcategorybutton.png "AddAnExceptionToTheSelectedCategoryButton")

3. 輸入例外狀況的名稱（例如， **system.uritemplatematchexception**）。

   ![輸入例外狀況名稱](../debugger/media/typetheexceptionname.png "TypeTheExceptionName")

   例外狀況會加入清單中（依字母順序）並自動核取。

若要將例外狀況新增至 GPU 記憶體存取例外狀況、JavaScript 執行時間例外狀況或 Win32 例外狀況分類，請包含錯誤碼和描述。

> [!TIP]
> 請檢查您的拼字！ [例外狀況設定] 視窗並不會檢查新增的例外狀況是否存在。 因此如果您鍵入 **Sytem.UriTemplateMatchException**，您會得到針對該例外狀況 (而非針對 **System.UriTemplateMatchException**) 的項目。

例外狀況設定會保存在此方案的 .suo 檔案中，因此可套用至特定的方案中。 您無法在不同方案間重複使用特定的例外狀況設定。 現在只會保存新增的例外狀況;刪除的例外狀況不是。 您可以新增例外狀況，關閉並重新開啟方案，例外狀況仍然會在該處。 但是，如果您刪除例外狀況，然後關閉/重新開啟此方案，則該例外狀況會重新出現。

[例外狀況設定] 視窗在 C# 中支援泛型例外狀況類型，但在 Visual Basic 中不支援。 若要中斷類似 `MyNamespace.GenericException<T>`的例外狀況，您必須新增例外狀況為 [MyNamespace.GenericException'1]。 也就是說，如果您建立了類似此程式碼的例外狀況：

```csharp
public class GenericException<T> : Exception
{
    public GenericException() : base("This is a generic exception.")
    {
    }
}
```

您可以使用先前的程式，將例外狀況新增至**例外狀況設定**：

![加入泛型例外狀況](../debugger/media/addgenericexception.png "AddGenericException")

## <a name="add-conditions-to-an-exception"></a>將條件新增至例外狀況

使用 [**例外狀況設定**] 視窗來設定例外狀況的條件。 目前支援的條件包括要針對例外狀況包含或排除的模組名稱。 藉由將模組名稱設定為條件，您可以選擇只在特定程式碼模組上中斷例外狀況。 您也可以選擇避免在特定模組上中斷。

> [!NOTE]
> 從 [!include[vs_dev15](../misc/includes/vs_dev15_md.md)]開始，支援將條件新增至例外狀況。

若要新增條件式例外狀況：

1. 選擇 [例外狀況設定] 視窗中的 [**編輯條件**] 按鈕，或以滑鼠右鍵按一下例外狀況，然後選擇 [**編輯條件**]。

   ![例外狀況的條件](../debugger/media/dbg-conditional-exception.png "DbgConditionalException")

2. 若要將額外的必要條件新增至例外狀況，請選取 [為每個新條件新增**條件**]。 其他條件線隨即出現。

   ![例外狀況的額外條件](../debugger/media/extraconditionsforanexception.png "ExtraConditionsForAnException")

3. 針對每個條件行，輸入模組的名稱，並將比較運算子清單變更為 [**等於**] 或 [**不等於**]。 您可以在名稱中指定萬用字元（ **\\\*** ），以指定一個以上的模組。

4. 如果您需要刪除條件，請選擇條件行結尾的 [ **X** ]。

## <a name="see-also"></a>另請參閱

- [於例外狀況之後繼續執行](../debugger/continuing-execution-after-an-exception.md)<br/>
- [如何：在發生例外狀況後檢查系統程式碼](../debugger/how-to-examine-system-code-after-an-exception.md)<br/>
- [如何：使用原生執行階段檢查](../debugger/how-to-use-native-run-time-checks.md)<br/>
- [不使用 C 執行階段程式庫進行執行階段檢查](../debugger/using-run-time-checks-without-the-c-run-time-library.md)<br/>
- [偵錯工具簡介](../debugger/debugger-feature-tour.md)
