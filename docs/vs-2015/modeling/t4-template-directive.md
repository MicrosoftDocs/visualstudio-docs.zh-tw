---
title: T4 範本指示詞 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 2b0a8e04-6fee-4c6c-b086-e49fc728a3ed
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d3a17275730cd093f8f9fa433aa28c7f9ca86e80
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2019
ms.locfileid: "74298143"
---
# <a name="t4-template-directive"></a>T4 範本指示詞
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] T4 文字範本的開頭通常是 `template` 指示詞，用於指定範本的處理方式。 文字範本和其所包含之任何檔案中的 template 指示詞不得超過一個。

 如需撰寫文字模板的一般總覽，請參閱[撰寫 T4 文字模板](../modeling/writing-a-t4-text-template.md)。

## <a name="using-the-template-directive"></a>使用範本指示詞

```
<#@ template [language="VB"] [compilerOptions="options"] [culture="code"] [debug="true"] [hostspecific="true"] [inherits="templateBaseClass"] [visibility="internal"] [linePragmas="false"] #>
```

 `template` 指示詞具有數個可讓您指定不同轉換層面的屬性。 所有屬性都是選擇性的。

## <a name="compileroptions-attribute"></a>compilerOptions 屬性
 範例：`compilerOptions="optimize+"`

 有效的值：任何有效的編譯器選項。 如需詳細資訊，請參閱[ C#依分類列出的編譯器選項](https://msdn.microsoft.com/library/96437ecc-6502-4cd3-b070-e9386a298e83)和[依分類列出的 Visual Basic 編譯器選項](https://msdn.microsoft.com/library/fbe36f7a-7cfa-4f77-a8d4-2be5958568e3)。

 忽略執行階段 (前置處理過的) 範本。

 將範本轉換為 [!INCLUDE[csprcs](../includes/csprcs-md.md)] 或 [!INCLUDE[vb_current_short](../includes/vb-current-short-md.md)] 並編譯產生的程式碼時會套用這些選項。

## <a name="culture-attribute"></a>culture 屬性
 範例：`culture="de-CH"`

 有效值： ""，不因文化特性而異，這是預設值。

 以 xx-XX 字串形式表示的文化特性。 例如，en-US、ja-JP、de-CH、de-DE。 如需詳細資訊，請參閱 <xref:System.Globalization.CultureInfo?displayProperty=fullName>。

 culture 屬性會指定當運算式區塊轉換為文字時所要使用的文化特性。

## <a name="debug-attribute"></a>debug 屬性
 範例：

```
debug="true"
```

 有效的值： `true, false`。 預設值為 False。

 如果 `debug` 屬性為 `true`，表示中繼程式碼檔案將會包含啟用偵錯工具所需的相關資訊，以更精確識別範本內中斷或例外狀況發生的位置。

 針對設計階段範本，中繼程式碼檔案會寫入您的 **% TEMP%** 目錄。

 若要在偵錯工具中執行設計階段範本，請儲存文字模板，然後在方案總管中開啟文字模板的快捷方式功能表，然後選擇 [ **Debug T4 template**]。

## <a name="hostspecific-attribute"></a>hostspecific 屬性
 範例：

```
hostspecific="true"
```

 有效的值： `true, false, trueFromBase`。 預設值為 False。

 如果您將這個屬性值設定為 `true`，就會有名為 `Host` 的屬性加入至文字範本所產生的類別中。 屬性是轉換引擎主控制項的參考，而且會宣告為[ITextTemplatingEngineHost](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110))。 如果您定義了自訂主應用程式，則可以將它轉換為自訂主應用程式類型。

 由於這個屬性的類型依主應用程式的類型而定，因此只有在撰寫僅限搭配特定主應用程式使用的文字範本時才有用處。 它適用于[設計階段範本](../modeling/design-time-code-generation-by-using-t4-text-templates.md)，但不適用於[執行時間範本](../modeling/run-time-text-generation-with-t4-text-templates.md)。

 當 `hostspecific` 為 `true` 且您正在使用 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 時，可以將 `this.Host` 的類型轉換為 IServiceProvider 來存取 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 的功能。 您也可以使用 `Host.ResolvePath(filename)` 取得專案中檔案的絕對路徑。 例如：

```csharp
<#@ template debug="false" hostspecific="true" language="C#" #>
<#@ output extension=".txt" #>
<#@ assembly name="EnvDTE" #>
<#@ import namespace="EnvDTE" #>
<#@ import namespace="System.IO" #>
<# // Get the Visual Studio API as a service:
 DTE dte = ((IServiceProvider)this.Host).GetCOMService(typeof(DTE)) as DTE;
#>
Number of projects in this solution: <#=  dte.Solution.Projects.Count #>

<#
 // Find a path within the current project:
 string myFile = File.ReadAllText(this.Host.ResolvePath("MyFile.txt"));
#>
Content of myFile is:
<#= myFile #>

```

 如果您同時使用 `inherits` 和 `hostspecific` 屬性，請在衍生類別中指定 host="trueFromBase"，在基底類別中指定 host="true"。 這可避免在產生的程式碼中出現 `Host` 屬性的雙重定義。

## <a name="language-attribute"></a>language 屬性
 範例：`language="VB"`

 有效的值： `C#` （預設值）

 `VB`

 Language 屬性會指定要用於語句和運算式區塊中之原始程式碼的語言（[!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 或 [!INCLUDE[csprcs](../includes/csprcs-md.md)]）。 從中產生輸出的中繼程式碼檔會使用這個語言。 這個語言與範本產生的語言無關，它可以是任何種類的文字。

 例如：

```vb
<#@ template language="VB" #>
<#@ output extension=".txt" #>
Squares of numbers:
<#
  Dim number As Integer
  For number = 1 To 4
#>
  Square of <#= number #> is <#= number * number #>
<#
  Next number
#>

```

## <a name="inherits-attribute"></a>inherits 屬性
 您可以指定範本的程式碼是否能繼承自另一個類別，而且這個類別也可從文字範本產生。

### <a name="inheritance-in-a-run-time-preprocessed-text-template"></a>執行階段 (前置處理過的) 文字範本中的繼承
 您可以在執行階段文字範本之間使用繼承，以建立基本範本，此範本會擁有數個衍生的變體。 執行時間範本是將**自訂工具**屬性設定為**TextTemplatingFilePreprocessor**的範本。 執行階段範本會產生您可以在應用程式中呼叫的程式碼，用以建立範本中定義的文字。 如需詳細資訊，請參閱[使用 T4 文字模板產生執行時間文字](../modeling/run-time-text-generation-with-t4-text-templates.md)。

 如果沒有指定 `inherits` 屬性，則會從文字範本產生基底類別和衍生類別。 指定 `inherits` 屬性時，只會產生衍生類別。 您可以手動撰寫基底類別，但是它必須提供衍生類別所用的方法。

 更典型的是，您會將另一個前置處理過的範本指定為基底類別。 基底範本提供通用的文字區塊，可以與衍生之範本的文字相互交錯。 您可以使用 `<#+ ... #>` 類別功能區塊，以定義包含文字片段的方法。 例如，您可以在基底範本中放置輸出文字的架構，提供可在衍生之範本中被覆寫的虛擬方法：

 執行階段 (前置處理過的) 文字範本 BaseTemplate.tt：

```scr
This is the common header.
<#
  SpecificFragment1();
#>
A common central text.
<#
  SpecificFragment2();
#>
This is the common footer.
<#+
  // Declare abstract methods
  protected virtual void SpecificFragment1() { }
  protected virtual void SpecificFragment2() { }
#>

```

 執行階段 (前置處理過的) 文字範本 DerivedTemplate1.tt：

```csharp
<#@ template language="C#" inherits="BaseTemplate" #>
<#
  // Run the base template:
  base.TransformText();
#>
<#+
// Provide fragments specific to this derived template:
protected override void SpecificFragment1()
{
#>
   Fragment 1 for DerivedTemplate1
<#+
}
protected override void SpecificFragment2()
{
#>
   Fragment 2 for DerivedTemplate1
<#+
}
#>

```

 用來叫用 DerivedTemplate1 的應用程式程式碼：

```csharp
Console.WriteLine(new DerivedTemplate().TransformText());
```

 產生的輸出：

```
This is the common header.
   Fragment 1 for DerivedTemplate1
A common central text.
   Fragment 2 for DerivedTemplate1
This is the common footer.
```

 您可以在不同的專案中建置基底和衍生類別。 請記得將基底專案或組件加入至衍生專案的參考。

 您也可以將一般手寫的類別當做基底類別。 基底類別必須提供衍生類別所用的方法。

> [!WARNING]
> 如果您同時使用 `inherits` 和 `hostspecific` 屬性，請在衍生類別中指定 hostspecific="trueFromBase"，在基底類別中指定 host="true"。 這可避免在產生的程式碼中出現 `Host` 屬性的雙重定義。

### <a name="inheritance-in-a-design-time-text-template"></a>設計階段文字範本中的繼承
 設計階段文字模板是**自訂工具**設定為**TextTemplatingFileGenerator**的檔案。 這種範本會為形成 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 專案之一部分的程式碼或文字產生輸出檔。 為產生輸出檔，會先將範本轉譯為中繼程式碼檔，後者通常不會顯示出來。 `inherits` 屬性會為這個中繼程式碼指定基底類別。

 如果是設計階段文字範本，您可指定任何衍生自 <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation?displayProperty=fullName> 的基底類別。 使用 `<#@assembly#>` 指示詞，可以載入包含基底類別的組件或專案。

 如需詳細資訊，請參閱 Gareth 的 Blog 中的「[文字模板中的繼承](https://go.microsoft.com/fwlink/?LinkId=208373)」。

## <a name="linepragmas-attribute"></a>LinePragmas 屬性
 範例：`linePragmas="false"`

 有效的值： `true` （預設值）

 `false`

 設定這個屬性為 false 可移除識別您在產生的程式碼中的行號標記。 這表示編譯器將會使用產生的程式碼中的行號來回報所有錯誤。這會為您提供更多偵錯選項，如此您可以選擇偵錯文字範本或產生的程式碼。

 如果您發現 pragma 的絕對檔名在原始程式碼控制之下產生分散合併，這個屬性也可派上用場。

## <a name="visibility-attribute"></a>可視性屬性
 範例：`visibility="internal"`

 有效的值： `public` （預設值）

 `internal`

 在執行階段文字範本中，這個屬性會設定所產生之類別的可視性屬性。 根據預設，類別是您的程式碼公開 API 的一部分，不過，您可以藉由設定 `visibility="internal"` 來確認只有您的程式碼可以使用文字產生的類別。
