---
title: 自動程式碼 UI 測試的結構 | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- coded UI tests
ms.assetid: 9c5d82fc-3fb7-4bb1-a9ac-ac1fa3a4b500
caps.latest.revision: 25
ms.author: gewarren
manager: douge
ms.openlocfilehash: c9fea94f0298212bb8c3909d4227936437b8f24c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47489229"
---
# <a name="anatomy-of-a-coded-ui-test"></a>自動程式化 UI 測試的結構
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[自動程式化 UI 測試的結構](https://docs.microsoft.com/visualstudio/test/anatomy-of-a-coded-ui-test)。  
  
當您在自動程式化 UI 測試專案中建立自動程式碼 UI測試時，有數個檔案會加入至您的方案。 在本主題中，我們將使用範例自動程式化 UI 測試來探索這些檔案。  
  
 **需求**  
  
-   Visual Studio 企業版  
  
## <a name="contents-of-a-coded-ui-test"></a>自動程式化 UI 測試的內容  
 當您建立自動程式碼 UI 測試時，**自動程式碼 UI 測試產生器**會建立待測使用者介面的對應，以及所有測試的測試方法、參數和判斷提示。 它也會針對每個測試建立類別檔案。  
  
|檔案|內容|可編輯？|  
|----------|--------------|---------------|  
|[UIMap.Designer.cs](#UIMapDesignerFile)|[宣告區段](#UIMapDesignerFile)<br /><br /> [UIMap 類別](#UIMapClass) (部分、自動產生)<br /><br /> [方法](#UIMapMethods)<br /><br /> [屬性](#UIMapProperties)|否|  
|[UIMap.cs](#UIMapCS)|[UIMap 類別](#UIMapCS) (部分)|是|  
|[CodedUITest1.cs](#CodedUITestCS)|[CodedUITest1 類別](#CodedUITestCS)<br /><br /> [方法](#CodedUITestMethods)<br /><br /> [屬性](#CodedUITestProperties)|是|  
|[UIMap.uitest](#UIMapuitest)|測試的 UI XML 對應。|否|  
  
###  <a name="UIMapDesignerFile"></a> UIMap.Designer.cs  
 這個檔案包含的程式碼，是建立測試時由**自動程式碼 UI 測試產生器**所自動建立。 測試每次變更時都會重新建立這個檔案，因此這不是讓您加入或修改程式碼的檔案。  
  
#### <a name="declarations-section"></a>宣告區段  
 這個區段包含 Windows UI 的下列宣告。  
  
```csharp  
using System;  
using System.CodeDom.Compiler;  
using System.Collections.Generic;  
using System.Drawing;  
using System.Text.RegularExpressions;  
using System.Windows.Input;  
using Microsoft.VisualStudio.TestTools.UITest.Extension;  
using Microsoft.VisualStudio.TestTools.UITesting;  
using Microsoft.VisualStudio.TestTools.UITesting.WinControls;  
using Microsoft.VisualStudio.TestTools.UnitTesting;  
using Keyboard = Microsoft.VisualStudio.TestTools.UITesting.Keyboard;  
using Mouse = Microsoft.VisualStudio.TestTools.UITesting.Mouse;  
using MouseButtons = System.Windows.Forms.MouseButtons;  
```  
  
 包含 Windows 使用者介面 (UI) 的 <xref:Microsoft.VisualStudio.TestTools.UITesting.WinControls> 命名空間。 若為網頁 UI，命名空間為 <xref:Microsoft.VisualStudio.TestTools.UITesting.HtmlControls>，若為 Windows Presentation Foundation UI，命名空間為 <xref:Microsoft.VisualStudio.TestTools.UITesting.WpfControls>。  
  
####  <a name="UIMapClass"></a> UIMap 類別  
 檔案的下一個區段是 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap> 類別。  
  
```  
[GeneratedCode("Coded UITest Builder", "10.0.21221.0")]  
public partial class UIMap  
```  
  
 類別程式碼以套用至類別的 <xref:System.CodeDom.Compiler.GeneratedCodeAttribute> 開頭，而類別宣告為部分類別。 您會發現該屬性也會套用到此檔案中的每個類別。 另一個可能包含這個類別的其他程式碼的檔案是 `UIMap.cs`，稍後再討論。  
  
 產生的 `UIMap` 類別包含錄製測試時所指定的每個方法的程式碼。  
  
```  
public void LaunchCalculator()  
public void AddItems()  
public void VerifyTotal()  
public void CleanUp()  
```  
  
 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap> 類別的這部分也包含針對方法所需的每個屬性而產生的程式碼。  
  
```  
public virtual LaunchCalculatorParams LaunchCalculatorParams  
public virtual AddItemsParams AddItemsParams  
public virtual VerifyTotalExpectedValues VerifyTotalExpectedValues  
public virtual CalculateItemsParams CalculateItemsParams  
public virtual VerifyMathAppTotalExpectedValues   
    VerifyMathAppTotalExpectedValues  
public UIStartMenuWindow UIStartMenuWindow  
public UIRunWindow UIRunWindow  
public UICalculatorWindow UICalculatorWindow  
public UIStartWindow UIStartWindow  
public UIMathApplicationWindow UIMathApplicationWindow  
```  
  
#####  <a name="UIMapMethods"></a> UIMap 方法  
 每個方法的結構都類似 `AddItems()` 方法。 程式碼下方有更詳細的說明，同時加上換行以更清楚顯示。  
  
```  
/// <summary>  
/// AddItems - Use 'AddItemsParams' to pass parameters into this method.  
/// </summary>  
public void AddItems()  
{  
    #region Variable Declarations  
    WinControl uICalculatorDialog =   
        this.UICalculatorWindow.UICalculatorDialog;  
    WinEdit uIItemEdit =   
        this.UICalculatorWindow.UIItemWindow.UIItemEdit;  
    #endregion  
  
    // Type '{NumPad7}' in 'Calculator' Dialog  
    Keyboard.SendKeys(uICalculatorDialog,   
        this.AddItemsParams.UICalculatorDialogSendKeys,   
        ModifierKeys.None);  
  
    // Type '{Add}{NumPad2}{Enter}' in 'Unknown Name' text box  
    Keyboard.SendKeys(uIItemEdit,   
        this.AddItemsParams.UIItemEditSendKeys,   
        ModifierKeys.None);  
}  
```  
  
 每個方法定義的摘要註解指出哪一個類別用於該方法的參數值。 在此例子中是 `AddItemsParams` 類別，這在稍後的 `UIMap.cs` 檔案中定義，也是 `AddItemsParams` 屬性傳回的實值型別。  
  
 方法程式碼的頂端是`Variable Declarations`區域，定義方法將使用的 UI 物件的區域變數。  
  
 在這個方法中，`UIItemWindow` 和 `UIItemEdit` 都是使用 `UICalculatorWindow` 類別來存取的屬性，稍後的 `UIMap.cs` 檔案中定義此類別。  
  
 接下來的幾行使用 `AddItemsParams` 物件的屬性，將鍵盤的文字傳送至小算盤應用程式。  
  
 `VerifyTotal()` 方法有非常類似的結構，且包含下列判斷提示程式碼。  
  
```  
// Verify that 'Unknown Name' text box's property 'Text' equals '9. '  
Assert.AreEqual(  
    this.VerifyTotalExpectedValues.UIItemEditText,   
    uIItemEdit.Text);  
```  
  
 文字方塊的名稱列為未知，因為 Windows 小盤盤應用程式的開發人員未提供公開可用的控制項名稱。 當實際值不等於預期值時，<xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.AreEqual%2A?displayProperty=fullName> 方法會失敗，導致測試失敗。 也請注意，預期的值包含小數點，後面接著一個空格。 如果您曾經修改此特定測試的功能，則必須允許該小數點和空格。  
  
#####  <a name="UIMapProperties"></a> UIMap 屬性  
 在整個類別中，每一個屬性的程式碼也非常標準。 `AddItemsParams` 屬性的下列程式碼用於 `AddItems()` 方法中。  
  
```  
public virtual AddItemsParams AddItemsParams  
{  
    get  
    {  
        if ((this.mAddItemsParams == null))  
        {  
            this.mAddItemsParams = new AddItemsParams();  
        }  
        return this.mAddItemsParams;  
    }  
}  
```  
  
 請注意，此屬性在傳回值之前，先使用名為 `mAddItemsParams` 的私用區域變數來保留值。 它傳回的物件有相同的屬性名稱和類別名稱。 此類別在稍後的 `UIMap.cs` 檔案中定義。  
  
 屬性所傳回的每個類別有類似的結構。 以下是 `AddItemsParams` 類別。  
  
```  
/// <summary>  
/// Parameters to be passed into 'AddItems'  
/// </summary>  
[GeneratedCode("Coded UITest Builder", "10.0.21221.0")]  
public class AddItemsParams  
{  
    #region Fields  
    /// <summary>  
    /// Type '{NumPad7}' in 'Calculator' Dialog  
    /// </summary>  
    public string UICalculatorDialogSendKeys = "{NumPad7}";  
  
    /// <summary>  
    /// Type '{Add}{NumPad2}{Enter}' in 'Unknown Name' text box  
    /// </summary>  
    public string UIItemEditSendKeys = "{Add}{NumPad2}{Enter}";  
    #endregion  
}  
```  
  
 如同 `UIMap.cs` 檔案中的所有類別，這個類別也是以 <xref:System.CodeDom.Compiler.GeneratedCodeAttribute> 開頭。 這個小類別中有一個 `Fields` 區域，定義字串做為 <xref:Microsoft.VisualStudio.TestTools.UITesting.Keyboard.SendKeys%2A?displayProperty=fullName> 方法的參數，此方法在先前討論的 `UIMap.AddItems()` 方法中使用。 在呼叫使用這些參數的方法之前，您可以撰寫程式碼來取代這些字串欄位中的值。  
  
###  <a name="UIMapCS"></a> UIMap.cs  
 根據預設，此檔案包含一個部分 `UIMap` 類別，沒有方法或屬性。  
  
#### <a name="uimap-class"></a>UIMap 類別  
 這裡可讓您建立自訂程式碼來擴充 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap> 類別的功能。 您在此檔案中建立的程式碼，**自動程式碼 UI 測試產生器**即不會在每次修改測試時重新產生。  
  
 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap> 的所有部分都可以使用 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap> 類別的任何其他部分的方法和屬性。  
  
###  <a name="CodedUITestCS"></a> CodedUITest1.cs  
 這個檔案由**自動程式碼 UI 測試產生器**產生，但不會在每次修改測試時重新建立，因此您可以修改這個檔案中的程式碼。 此檔案的名稱是從您建立測試時所指定的名稱產生。  
  
#### <a name="codeduitest1-class"></a>CodedUITest1 類別  
 根據預設，此檔案只包含一個類別的定義。  
  
```  
[CodedUITest]  
public class CodedUITest1  
```  
  
 T:Microsoft.VisualStudio.TestTools.UITesting.CodedUITestAttribute 會自動套用至類別，可讓測試架構將它辨識為測試擴充功能。 也請注意，這不是部分類別。 此檔案包含整個類別程式碼。  
  
#####  <a name="CodedUITestProperties"></a> CodedUITest1 屬性  
 此類別包含位於檔案最下方的兩個預設屬性。 不得修改。  
  
```  
/// <summary>  
/// Gets or sets the test context which provides  
/// information about and functionality for the current test run.  
///</summary>  
public TestContext TestContext  
public UIMap UIMap  
```  
  
#####  <a name="CodedUITestMethods"></a> CodedUITest1 方法  
 根據預設，此類別只包含一個方法。  
  
```  
public void CodedUITestMethod1()  
```  
  
 這個方法會呼叫您記錄測試時所指定的每個 `UIMap` 方法；[UIMap 類別](#UIMapClass)一節中有相關說明。  
  
 標題為 `Additional test attributes` 的區域 (如果取消註解) 包含兩個選擇性方法。  
  
```  
// Use TestInitialize to run code before running each test   
[TestInitialize()]  
public void MyTestInitialize()  
{  
    // To generate code for this test, select "Generate Code for Coded   
    // UI Test" from the shortcut menu and select one of the menu items.  
    // For more information on generated code, see   
    // http://go.microsoft.com/fwlink/?LinkId=179463  
  
    // You could move this line from the CodedUITestMethod1() method  
    this.UIMap.LaunchCalculator();  
}  
  
// Use TestCleanup to run code after each test has run  
[TestCleanup()]  
public void MyTestCleanup()  
{  
    // To generate code for this test, select "Generate Code for Coded   
    // UI Test" from the shortcut menu and select one of the menu items.  
    // For more information on generated code, see   
    // http://go.microsoft.com/fwlink/?LinkId=179463  
  
    // You could move this line from the CodedUITestMethod1() method  
    this.UIMap.CloseCalculator();  
}  
```  
  
 `MyTestInitialize()` 方法套用 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestInitializeAttribute>，向測試架構表示在任何其他測試方法之前呼叫這個方法。 同樣地，`MyTestCleanup()` 方法套用 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCleanupAttribute>，向測試架構表示在呼叫任何其他測試方法之後呼叫這個方法。 使用這些方法是選擇性的。 對於此測試，`UIMap.LaunchCalculator()` 方法可以從 `MyTestInitialize()` 呼叫，而 `UIMap.CloseCalculator()` 方法可以從 `MyTestCleanup()` 而不是從 `CodedUITest1Method1()` 呼叫。  
  
 如果您使用 <xref:Microsoft.VisualStudio.TestTools.UITesting.CodedUITestAttribute> 將其他方法加入至此類別，測試架構會在測試時呼叫每個方法。  
  
###  <a name="UIMapuitest"></a> UIMap.uitest  
 這是一個 XML 檔案，代表自動程式化 UI 測試錄製及其所有部分的結構。 其中包括動作和類別，還有這些類別的方法和屬性。 [UIMap.Designer.cs](#UIMapDesignerFile) 檔案包含自動程式碼 UI 產生器為了重現測試結構而產生的程式碼，並提供測試架構的連線。  
  
 不可直接編輯 `UIMap.uitest` 檔案。 不過，您可以使用自動程式碼 UI 產生器來修改測試，進而自動修改 `UIMap.uitest` 檔案和 [UIMap.Designer.cs](#UIMapDesignerFile) 檔案。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap>   
 <xref:Microsoft.VisualStudio.TestTools.UITesting.WinControls>   
 <xref:Microsoft.VisualStudio.TestTools.UITesting.HtmlControls>   
 <xref:Microsoft.VisualStudio.TestTools.UITesting.WpfControls>   
 <xref:System.CodeDom.Compiler.GeneratedCodeAttribute>   
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.AreEqual%2A?displayProperty=fullName>   
 <xref:Microsoft.VisualStudio.TestTools.UITesting.Keyboard.SendKeys%2A?displayProperty=fullName>   
 <xref:Microsoft.VisualStudio.TestTools.UITesting.CodedUITestAttribute>   
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestInitializeAttribute>   
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCleanupAttribute>   
 [使用使用者介面自動化來測試您的程式碼](../test/use-ui-automation-to-test-your-code.md)   
 [建立自動程式化 UI 測試](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate)   
 [自動程式化 UI 測試的最佳做法](../test/best-practices-for-coded-ui-tests.md)   
 [測試含有多個 UI 對應的大型應用程式](../test/testing-a-large-application-with-multiple-ui-maps.md)   
 [自動程式化 UI 測試和動作記錄的支援組態和平台](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)



