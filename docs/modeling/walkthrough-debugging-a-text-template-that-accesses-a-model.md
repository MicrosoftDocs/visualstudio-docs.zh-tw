---
title: 逐步解說：偵錯存取模型的文字範本
ms.date: 11/04/2016
ms.topic: conceptual
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 344a9331ed63d2da27379770305905ecf5edee77
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72666964"
---
# <a name="walkthrough-debugging-a-text-template-that-accesses-a-model"></a>逐步解說：偵錯存取模型的文字範本
當您修改或加入特定領域語言方案中的文字模板時，您可能會在引擎將範本轉換成原始程式碼時，或在編譯產生的程式碼時收到錯誤。 下列逐步解說示範您可以執行哪些動作來進行文字模板的調試。

> [!NOTE]
> 如需有關一般文字模板的詳細資訊，請參閱程式[代碼產生和 T4 文字模板](../modeling/code-generation-and-t4-text-templates.md)。 如需有關偵錯工具文字模板的詳細資訊，請參閱[逐步解說：偵錯工具文字模板](debugging-a-t4-text-template.md)。

## <a name="creating-a-domain-specific-language-solution"></a>建立特定領域語言方案
 在此程式中，您會建立具有下列特性的特定領域語言解決方案：

- 名稱： DebuggingTestLanguage

- 解決方案範本：最小語言

- 副檔名： ddd

- 公司名稱： Fabrikam

  如需有關建立特定領域語言方案的詳細資訊，請參閱[如何：建立特定領域語言方案](../modeling/how-to-create-a-domain-specific-language-solution.md)。

## <a name="creating-a-text-template"></a>建立文字模板
 將文字模板加入至您的方案。

#### <a name="to-create-a-text-template"></a>若要建立文字模板

1. 建立解決方案，並在偵錯工具中開始執行它。 （在 [**建立**] 功能表上，按一下 [**重建方案**]，然後在 [**調試**] 功能表上，按一下 [**開始調試**]）。Visual Studio 的新實例會開啟調試專案。

2. 將名為 `DebugTest.tt` 的文字檔新增至調試專案。

3. 請確定 DebugTest.tt 的 [**自訂工具**] 屬性已設定為 [`TextTemplatingFileGenerator`]。

## <a name="debugging-directives-that-access-a-model-from-a-text-template"></a>從文字模板存取模型的偵錯工具指示詞
 您必須先呼叫產生的指示詞處理器，才可以從文字模板中的語句和運算式存取模型。 呼叫產生的指示詞處理器可讓您模型中的類別可供文字模板程式碼當做屬性使用。 如需詳細資訊，請參閱[從文字模板存取模型](../modeling/accessing-models-from-text-templates.md)。

 在下列程式中，您將會對不正確的指示詞名稱和不正確的屬性名稱進行偵錯工具。

#### <a name="to-debug-an-incorrect-directive-name"></a>若要進行不正確的指示詞名稱的偵錯工具

1. 將 DebugTest.tt 中的程式碼取代為下列程式碼：

    > [!NOTE]
    > 程式碼包含錯誤。 您將會導入錯誤，以便進行調試。

    ```csharp
    <#@ template language="C#" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation"#>
    <#@ output extension=".txt" #>
    <#@ modelRoot processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=ExampleModel" #>

    Model: <#= this.ExampleModel #>
    <#
    foreach (ExampleElement element in this.ExampleModel.Elements)
    {
    #>
        Element: <#= element.Name #>
    <#
    }
    #>
    ```

    ```vb
    <#@ template language="VB" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation"#>
    <#@ output extension=".txt" #>
    <#@ modelRoot processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=ExampleModel" #>

    Model: <#= Me.ExampleModel #>
    <#
    For Each element as ExampleElement in Me.ExampleModel.Elements
    #>
        Element: <#= element.Name #>
    <#
    Next
    #>
    ```

2. 在**方案總管**中，以滑鼠右鍵按一下 [DebugTest.tt]，然後按一下 [**執行自訂工具**]。

     [**錯誤清單**] 視窗會顯示此錯誤：

     **名為 ' DebuggingTestLanguageDirectiveProcessor ' 的處理器不支援名為 ' modelRoot ' 的指示詞。轉換將不會執行。**

     在此情況下，指示詞呼叫包含不正確的指示詞名稱。 您已指定 `modelRoot` 做為指示詞名稱，但 `DebuggingTestLanguage` 正確的指示詞名稱。

3. 按兩下 [**錯誤清單**] 視窗中的錯誤，跳至程式碼。

4. 若要修正程式碼，請將指示詞名稱變更為 `DebuggingTestLanguage`。

     變更會反白顯示。

    ```csharp
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=ExampleModel" #>
    ```

    ```vb
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=ExampleModel" #>
    ```

5. 在**方案總管**中，以滑鼠右鍵按一下 [DebugTest.tt]，然後按一下 [**執行自訂工具**]。

     現在系統會轉換文字模板，並產生對應的輸出檔。 您不會在 [**錯誤清單**] 視窗中看到任何錯誤。

#### <a name="to-debug-an-incorrect-property-name"></a>若要 debug 錯的屬性名稱

1. 將 DebugTest.tt 中的程式碼取代為下列程式碼：

    > [!NOTE]
    > 程式碼包含錯誤。 您將會導入錯誤，以便進行調試。

    ```csharp
    <#@ template language="C#" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation"#>
    <#@ output extension=".txt" #>
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=LibraryModel" #>

    Model: <#= this.ExampleModel #>
    <#
    foreach (ExampleElement element in this.ExampleModel.Elements)
    {
    #>
        Element: <#= element.Name #>
    <#
    }
    #>
    ```

    ```vb
    <#@ template language="VB" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation"#>
    <#@ output extension=".txt" #>
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=LibraryModel" #>

    Model: <#= Me.ExampleModel #>
    <#
    For Each element as ExampleElement in Me.ExampleModel.Elements
    #>
        Element: <#= element.Name #>
    <#
    Next
    #>
    ```

2. 在**方案總管**中，以滑鼠右鍵按一下 [DebugTest.tt]，然後按一下 [**執行自訂工具**]。

     [**錯誤清單**] 視窗隨即出現，並顯示下列其中一個錯誤：

     (C#)

     **編譯轉換： VisualStudio. TextTemplating \<GUID >。GeneratedTextTransformation ' 不包含 ' Examplemodel.store.customer ' 的定義**

     （Visual Basic）

     **正在編譯轉換： ' Examplemodel.store.customer ' 不是 ' VisualStudio. TextTemplating \<GUID > 的成員。GeneratedTextTransformation'.**

     在此情況下，文字模板程式碼會包含不正確的屬性名稱。 您已指定 `ExampleModel` 做為屬性名稱，但 `LibraryModel` 正確的屬性名稱。 您可以在提供的參數中找到正確的屬性名稱，如下列程式碼所示：

    ```
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=LibraryModel" #>
    ```

3. 按兩下 [錯誤清單] 視窗中的錯誤，跳至程式碼。

4. 若要修正程式碼，請將文字模板程式碼中的屬性名稱變更為 `LibraryModel`。

     所做的變更已醒目標示。

    ```csharp
    <#@ template language="C#" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation"#>
    <#@ output extension=".txt" #>
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=LibraryModel" #>

    Model: <#= this.LibraryModel #>
    <#
    foreach (ExampleElement element in this.LibraryModel.Elements)
    {
    #>
        Element: <#= element.Name #>
    <#
    }
    #>
    ```

    ```vb
    <#@ template language="VB" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation"#>
    <#@ output extension=".txt" #>
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=LibraryModel" #>

    Model: <#= Me.LibraryModel #>
    <#
    For Each element as ExampleElement in Me.LibraryModel.Elements
    #>
        Element: <#= element.Name #>
    <#
    Next
    #>
    ```

5. 在**方案總管**中，以滑鼠右鍵按一下 [DebugTest.tt]，然後按一下 [**執行自訂工具**]。

     現在系統會轉換文字模板，並產生對應的輸出檔。 您不會在 [**錯誤清單**] 視窗中看到任何錯誤。