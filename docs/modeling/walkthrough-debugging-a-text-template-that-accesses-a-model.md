---
title: 逐步解說：可存取模型的偵錯工具文字模板
description: 提供有關如何對存取模型的文字模板進行 debug 的資訊。
ms.date: 11/04/2016
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: SEO-VS-2020
ms.workload:
- multiple
ms.openlocfilehash: 394fe7b1a368d3d4c6a47fd4350ac6644112aa57
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99924115"
---
# <a name="walkthrough-debugging-a-text-template-that-accesses-a-model"></a>逐步解說：偵錯存取模型的文字範本
當您修改或新增特定領域語言方案中的文字模板時，當引擎將範本轉換為原始程式碼或編譯產生的程式碼時，可能會收到錯誤。 下列逐步解說將示範您可以用來對文字模板進行的一些動作。

> [!NOTE]
> 如需文字模板的一般詳細資訊，請參閱程式 [代碼產生和 T4 文字模板](../modeling/code-generation-and-t4-text-templates.md)。 如需有關偵錯工具文字模板的詳細資訊，請參閱 [逐步解說：進行文字模板的調試](debugging-a-t4-text-template.md)程式。

## <a name="creating-a-domain-specific-language-solution"></a>建立 Domain-Specific 語言方案
 在此程式中，您會建立具有下列特性的特定領域語言方案：

- 名稱： DebuggingTestLanguage

- 解決方案範本：基礎語言

- 副檔名： ddd

- 公司名稱： Fabrikam

  如需有關建立特定領域語言解決方案的詳細資訊，請參閱 [如何：建立 Domain-Specific 語言方案](../modeling/how-to-create-a-domain-specific-language-solution.md)。

## <a name="creating-a-text-template"></a>建立文字模板
 將文字模板加入至您的方案。

#### <a name="to-create-a-text-template"></a>若要建立文字模板

1. 建立方案，並在偵錯工具中開始執行。  (在 [ **組建** ] 功能表上，按一下 [ **重建方案**]，然後在 [ **調試** 程式] 功能表上，按一下 [ **開始調試** 程式]。 ) 新的實例時，Visual Studio 會開啟偵錯工具專案。

2. 將名為的文字檔加入 `DebugTest.tt` 至調試專案。

3. 請確定 DebugTest.tt 的 **自訂工具** 屬性已設定為 `TextTemplatingFileGenerator` 。

## <a name="debugging-directives-that-access-a-model-from-a-text-template"></a>從文字模板存取模型的偵錯工具指示詞
 在您可以從文字模板中的語句和運算式存取模型之前，您必須先呼叫產生的指示詞處理器。 呼叫產生的指示詞處理器會讓模型中的類別可作為屬性的文字模板程式碼。 如需詳細資訊，請參閱 [從文字模板存取模型](../modeling/accessing-models-from-text-templates.md)。

 在下列程式中，您將會偵測不正確的指示詞名稱和不正確的屬性名稱。

#### <a name="to-debug-an-incorrect-directive-name"></a>若要偵測不正確的指示詞名稱

1. 將 DebugTest.tt 中的程式碼取代為下列程式碼：

    > [!NOTE]
    > 程式碼包含錯誤。 您將會引入錯誤以進行 debug。

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

2. 在 **方案總管** 中，以滑鼠右鍵按一下 [DebugTest.tt]，然後按一下 [ **執行自訂工具**]。

     [ **錯誤清單** ] 視窗會顯示下列錯誤：

     **名為 ' DebuggingTestLanguageDirectiveProcessor ' 的處理器不支援名為 ' modelRoot ' 的指示詞。轉換將不會執行。**

     在此情況下，指示詞呼叫包含不正確的指示詞名稱。 您已指定 `modelRoot` 為指示詞名稱，但正確的指示詞名稱為 `DebuggingTestLanguage` 。

3. 按兩下 [ **錯誤清單** ] 視窗中的錯誤，以跳至程式碼。

4. 若要修正程式碼，請將指示詞名稱變更為 `DebuggingTestLanguage` 。

     變更即會反白顯示。

    ```csharp
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=ExampleModel" #>
    ```

    ```vb
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=ExampleModel" #>
    ```

5. 在 **方案總管** 中，以滑鼠右鍵按一下 [DebugTest.tt]，然後按一下 [ **執行自訂工具**]。

     現在系統會轉換文字模板，並產生對應的輸出檔。 您將不會在 [ **錯誤清單** ] 視窗中看到任何錯誤。

#### <a name="to-debug-an-incorrect-property-name"></a>若要偵測不正確的屬性名稱

1. 將 DebugTest.tt 中的程式碼取代為下列程式碼：

    > [!NOTE]
    > 程式碼包含錯誤。 您將會引入錯誤以進行 debug。

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

2. 在 **方案總管** 中，以滑鼠右鍵按一下 [DebugTest.tt]，然後按一下 [ **執行自訂工具**]。

     [ **錯誤清單** ] 視窗隨即出現，並顯示下列其中一個錯誤：

     (C#)

     **編譯轉換： Microsoft. VisualStudio. TextTemplating \<GUID> 。GeneratedTextTransformation ' 不包含 ' Examplemodel.store.customer ' 的定義**

      (Visual Basic) 

     **編譯轉換： ' Examplemodel.store.customer ' 不是 ' Microsoft. VisualStudio. TextTemplating 的成員 \<GUID> 。GeneratedTextTransformation'.**

     在此情況下，文字模板程式碼會包含不正確的屬性名稱。 您已指定 `ExampleModel` 為屬性名稱，但正確的屬性名稱為 `LibraryModel` 。 您可以在提供的參數中找到正確的屬性名稱，如下列程式碼所示：

    ```
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=LibraryModel" #>
    ```

3. 按兩下 [錯誤清單] 視窗中的錯誤，以跳至程式碼。

4. 若要修正程式碼，請將屬性名稱變更為 `LibraryModel` 文字模板程式碼中的。

     所做的變更已醒目提示。

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

5. 在 **方案總管** 中，以滑鼠右鍵按一下 [DebugTest.tt]，然後按一下 [ **執行自訂工具**]。

     現在系統會轉換文字模板，並產生對應的輸出檔。 您將不會在 [ **錯誤清單** ] 視窗中看到任何錯誤。
