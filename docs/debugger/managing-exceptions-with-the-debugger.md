---
title: 使用調試器管理異常 |微軟文檔
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
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302151"
---
# <a name="manage-exceptions-with-the-debugger-in-visual-studio"></a>使用視覺化工作室中的調試器管理異常

例外狀況是程式執行時發生之錯誤狀態的指示。 您可以告訴調試器要打開哪些異常或異常集，以及此時您希望調試器中斷（即在調試器中暫停）。 當調試器中斷時，它會顯示異常被拋出的位置。 您還可以添加或刪除異常。 在 Visual Studio 中打開解決方案後，請使用**調試> Windows >異常設置**來打開 **"例外設置"** 視窗。

提供回應最重要異常的處理常式。 如果需要知道如何添加例外處理常式，請參閱[編寫更好的 C# 代碼來修復 Bug。](../debugger/write-better-code-with-visual-studio.md) 此外，瞭解如何將調試器配置為始終中斷某些異常的執行。

發生異常時，調試器將異常消息寫入**輸出**視窗。 在下列情況下，它可能會中斷執行：

- 引發未處理的異常。
- 調試器配置為在調用任何處理程式之前中斷執行。
- 您已設置["僅我的代碼](../debugger/just-my-code.md)"，調試器配置為在使用者代碼中未處理的任何異常時中斷。

> [!NOTE]
> ASP.NET 具有最上層例外狀況處理常式，這會在瀏覽器中顯示錯誤頁面。 除非啟用 **"我的代碼"，** 否則不會中斷執行。 例如，請參閱[告訴調試器繼續處理使用者未處理的異常](#BKMK_UserUnhandled)。

<!-- Two consecutive notes are intentional here...-->

> [!NOTE]
> 在 Visual Basic 應用程式中，即使使用 On Error 樣式的錯誤處理常式，偵錯工具還是會將所有錯誤都當成例外狀況管理。

## <a name="tell-the-debugger-to-break-when-an-exception-is-thrown"></a>告訴調試器在引發異常時中斷

調試器可以在引發異常時中斷執行，因此您可以在調用處理程式之前檢查異常。

在 **"異常設置**"視窗中（**調試> Windows >異常設置**），展開異常類別（如**通用語言運行時異常）的**節點。 然後，選擇該類別中特定異常的核取方塊，如**System.Access"異常**"。 您也可以選取例外狀況的整個類別。

![已檢查的 AccessViolationException](../debugger/media/exceptionsettingscheckaccess.png "異常設置檢查訪問")

> [!TIP]
> 您可以使用 **"異常設置"** 工具列中的 **"搜索**"視窗查找特定異常，或使用搜索來篩選特定命名空間（如**System.IO**）。

如果在 **"異常設置"** 視窗中選擇異常，則調試器將在引發異常的位置中斷，無論是否處理。 現在，異常稱為第一次機會異常。 例如，以下是幾個情節：

- 在以下 C# 主控台應用程式中，Main 方法在`try/catch`塊內引發**Access"衝突異常**"。

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

  如果在 **"異常設置"** 中選中**了 Access"衝突異常**"，則`throw`當您在調試器中運行此代碼時，將在行上執行。 然後，您可以繼續執行。 主控台應該會顯示這兩行：

  ```cmd
  caught exception
  goodbye
  ```

  但它不顯示線條`here`。

- C# 主控台應用程式引用具有兩種方法的類庫。 一種方法引發異常並處理它，而第二個方法引發相同的異常，但不處理它。

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

  如果在 **"異常設置"** 中選中**了 Access"異常"，** 則當您`throw`在調試器中運行此代碼時，執行將在**ThrowHandledException（）** 和 **"Throw Unhandled異常"** 中執行。

要將異常設置還原到預設值，請選擇"**將清單還原到預設設置**"按鈕：

![將例外狀況設定還原成預設值](../debugger/media/restoredefaultexceptions.png "還原預設異常")

## <a name="tell-the-debugger-to-continue-on-user-unhandled-exceptions"></a><a name="BKMK_UserUnhandled"></a>告訴調試器繼續處理使用者未處理的異常

如果使用["我的代碼](../debugger/just-my-code.md)"調試 .NET 或 JavaScript 代碼，則可以告訴調試器，以防止在使用者代碼中處理但在其他地方處理的異常。

1. 在 **"例外設置"** 視窗中，通過按右鍵列標籤打開快顯功能表，然後選擇 **"顯示列>其他操作**"。 （如果您已關閉 **"僅我的代碼"，** 則看不到此命令。將顯示名為 **"其他操作"的第**三列。

   ![其他操作列](../debugger/media/additionalactionscolumn.png "其他動作列")

   對於在此列**中使用者代碼中未處理時顯示"繼續"** 的異常，如果該異常未在使用者代碼中處理，而是外部處理，則調試器將繼續。

2. 要更改特定異常的此設置，請選擇異常，按右鍵以顯示快顯功能表，然後選擇"**使用者代碼 中未處理時繼續**"。 您還可以更改整個異常類別（如整個通用語言運行時異常）的設置。

   ![[在使用者代碼中未處理時繼續]](../debugger/media/continuewhenunhandledinusercodesetting.png "在使用者代碼設置中未處理時繼續")

例如，ASP.NET Web 應用程式通過將異常轉換為 HTTP 500 狀態碼[（ASP.NET Web API 中的異常處理](/aspnet/web-api/overview/error-handling/exception-handling)）來處理異常，這可能無助于您確定異常的來源。 在下列範例中，使用者程式碼會呼叫擲回 `String.Format()` 的 <xref:System.FormatException>。 執行中斷，如下所示：

![使用者&#45;未處理異常的中斷](../debugger/media/exceptionunhandledbyuser.png "異常未按使用者處理")

## <a name="add-and-delete-exceptions"></a>新增及刪除例外狀況

您可以新增及刪除例外狀況。 要從類別中刪除異常類型，請選擇異常，然後從 **"例外設置"** 工具列上的清單按鈕（減號）**中選擇"刪除所選異常**"。 或者，您可以按右鍵異常並選擇"從快顯功能表**中刪除**"。 刪除異常的效果與取消選中異常的效果相同，即調試器在引發異常時不會中斷。

要添加異常：

1. 在 **"例外設置"** 視窗中，選擇一個異常類別（例如，**通用語言運行時**）。

2. 選擇"**向所選類別添加異常**"按鈕（加號）。

   ![[向所選類別添加異常] 按鈕](../debugger/media/addanexceptiontotheselectedcategorybutton.png "添加"異常"到所選類別按鈕")

3. 鍵入異常的名稱（例如，**系統.UriTemplate 匹配異常**）。

   ![鍵入異常名稱](../debugger/media/typetheexceptionname.png "鍵入異常名稱")

   異常將添加到清單中（按字母順序排列），並自動選中。

要向 GPU 記憶體訪問異常添加異常，JavaScript 運行時異常或 Win32 異常類別包括錯誤代碼和說明。

> [!TIP]
> 請檢查您的拼字！ **"例外設置"** 視窗不檢查是否存在添加的異常。 因此，如果您鍵入**Sytem.UriTemplateMatchException，** 您將獲得該異常的條目（而不是**針對 System.UriTemplate 匹配異常**）。

例外狀況設定會保存在此方案的 .suo 檔案中，因此可套用至特定的方案中。 您無法在不同方案間重複使用特定的例外狀況設定。 現在只保留添加的異常;刪除的異常不是。 您可以添加異常，關閉並重新打開解決方案，並且該異常仍將存在。 但是，如果您刪除例外狀況，然後關閉/重新開啟此方案，則該例外狀況會重新出現。

[例外狀況設定] **** 視窗在 C# 中支援泛型例外狀況類型，但在 Visual Basic 中不支援。 若要中斷類似 `MyNamespace.GenericException<T>`的例外狀況，您必須新增例外狀況為 [MyNamespace.GenericException'1] ****。 也就是說，如果您創建了如下所示的異常：

```csharp
public class GenericException<T> : Exception
{
    public GenericException() : base("This is a generic exception.")
    {
    }
}
```

您可以使用前面的過程將異常添加到**異常設置**：

![加入泛型例外狀況](../debugger/media/addgenericexception.png "添加通用異常")

## <a name="add-conditions-to-an-exception"></a>向異常添加條件

使用 **"例外設置"** 視窗設置異常條件。 當前支援的條件包括要包括或排除異常的模組名稱。 通過將模組名稱設置為條件，您可以選擇僅在某些代碼模組上為異常設置中斷。 您也可以選擇避免中斷特定模組。

> [!NOTE]
> 支援從 中[!include[vs_dev15](../misc/includes/vs_dev15_md.md)]開始向異常添加條件。

要添加條件異常：

1. 在"異常設置"視窗中選擇 **"編輯條件**"按鈕，或按右鍵異常並選擇 **"編輯條件**"。

   ![異常的條件](../debugger/media/dbg-conditional-exception.png "Dbg條件異常")

2. 要向異常添加額外的必需條件，請選擇為每個新條件**添加條件**。 將顯示其他條件行。

   ![異常的額外條件](../debugger/media/extraconditionsforanexception.png "例外的外附加條件")

3. 對於每個條件行，鍵入模組的名稱，並將比較運算子清單更改為**等於**或不**等於**。 您可以在名稱中指定通配**\\**符 （ ） 以指定多個模組。

4. 如果需要刪除條件，請選擇條件行末尾的**X。**

## <a name="see-also"></a>另請參閱

- [於例外狀況之後繼續執行](../debugger/continuing-execution-after-an-exception.md)<br/>
- [如何：在發生例外狀況後檢查系統程式碼](../debugger/how-to-examine-system-code-after-an-exception.md)<br/>
- [如何：使用原生執行階段檢查](../debugger/how-to-use-native-run-time-checks.md)<br/>
- [使用沒有 C 運行時庫的運行時檢查](../debugger/using-run-time-checks-without-the-c-run-time-library.md)<br/>
- [首先查看調試器](../debugger/debugger-feature-tour.md)
