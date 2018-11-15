---
title: 使用 TextTransform 公用程式，在 Visual Studio 中產生檔案
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- text templates, TextTransform utility
- TextTransform.exe
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 6572ef97027466fa97c254664327f2f77b4ea7f2
ms.sourcegitcommit: 768d7877fe826737bafdac6c94c43ef70bf45076
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/02/2018
ms.locfileid: "50967073"
---
# <a name="generate-files-with-the-texttransform-utility"></a>產生使用 TextTransform 公用程式的檔案

TextTransform.exe 是命令列工具，可用來轉換文字範本。 當您呼叫 TextTransform.exe 時，您可以指定文字範本檔案的名稱做為引數。 TextTransform.exe 呼叫文字轉換引擎，並處理文字範本。 TextTransform.exe 通常會從指令碼呼叫。 不過，它通常不需要，因為在 Visual Studio 中或在建置流程中，您可以執行文字轉換。

> [!NOTE]
> 如果您想要執行建置程序的一部分的文字轉換，請考慮使用 MSBuild 的文字轉換工作。 如需詳細資訊，請參閱 <<c0> [ 建置流程中的程式碼產生](../modeling/code-generation-in-a-build-process.md)。 在機器安裝 Visual Studio 中，您也可以撰寫的應用程式或可以轉換文字範本的 Visual Studio 擴充功能。 如需詳細資訊，請參閱 <<c0> [ 藉由使用自訂主機處理文字範本](../modeling/processing-text-templates-by-using-a-custom-host.md)。

 TextTransform.exe 位於下列目錄：

 **\Program Files (x86)\Microsoft Visual Studio\2017\Professional\Common7\IDE**

Professional edition，或

 **\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE**

 針對 Enterprise edition。

在舊版的 Visual Studio 中，在下列位置找到的檔案：

**\Program Files (x86)\Common Files\Microsoft Shared\TextTemplating\{version}**

其中 {version} 取決於已安裝先前版本。

## <a name="syntax"></a>語法

```
TextTransform [<options>] <templateName>
```

### <a name="parameters"></a>參數

|**引數**|**描述**|
|-|-|
|`templateName`|識別您想要轉換的範本檔案的名稱。|

|**選項**|**描述**|
|-|-|
|**-out** \<filename>|要轉換的輸出寫入檔案。|
|**-r** \<assembly>|用來編譯和執行文字範本組件。|
|**-u** \<namespace>|用於編譯範本命名空間。|
|**-I** \<includedirectory>|包含指定的文字範本中所包含的文字範本的目錄。|
|**-P** \<referencepath >|要搜尋的文字範本中指定的組件，或使用的目錄 **-r**選項。<br /><br /> 例如，若要包含 Visual Studio API 所使用的組件，請使用<br /><br /> `-P "%VSSHELLFOLDER%\Common7\IDE\PublicAssemblies"`|
|**-dp** \<processorName>!\<className>!\<assemblyName&#124;codeBase>|名稱、 完整類型名稱和組件可用來處理自訂指示詞內的文字範本指示詞處理器。|
|**-a** [processorName]![directiveName]!\<parameterName>!\<parameterValue>|指定指示詞處理器的參數值。 如果您指定參數名稱和值，此參數可指示詞的所有處理器。 如果您指定指示詞處理器，參數是僅適用於指定的處理器。 如果您指定指示詞的名稱，參數才可使用正在處理指定的指示詞。<br /><br /> 若要存取的參數值，指示詞處理器或文字範本，使用[ITextTemplatingEngineHost.ResolveParameterValue](/previous-versions/visualstudio/visual-studio-2012/bb126369\(v\=vs.110\))。 在文字範本中，包括`hostspecific`在範本指示詞上叫用的訊息和`this.Host`。 例如: <br /><br /> `<#@template language="c#" hostspecific="true"#> [<#= this.Host.ResolveParameterValue("", "", "parameterName") #>]`.<br /><br /> 一律使用類型 '！' 標記，即使您省略選擇性的處理器和指示詞的名稱。 例如: <br /><br /> `-a !!param!value`|
|**-h**|提供說明。|

## <a name="related-topics"></a>相關主題

|工作|主題|
|-|-|
|在 Visual Studio 方案中產生檔案。|[使用 T4 文字範本在設計階段產生程式碼](../modeling/design-time-code-generation-by-using-t4-text-templates.md)|
|撰寫指示詞處理器，以轉換您專屬的資料來源。|[自訂 T4 文字轉換](../modeling/customizing-t4-text-transformation.md)|
|撰寫文字範本化主應用程式，可讓您叫用您自己的應用程式從文字範本。|[使用自訂主機處理文字範本](../modeling/processing-text-templates-by-using-a-custom-host.md)|
