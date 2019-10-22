---
title: 使用 TextTransform 公用程式產生檔案 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- text templates, TextTransform utility
- TextTransform.exe
ms.assetid: 06a48235-fe02-403e-a1cf-2ae70b4db62f
caps.latest.revision: 43
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 18776795fdf693c855edd3f629d674089daaaebd
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72666088"
---
# <a name="generating-files-with-the-texttransform-utility"></a>使用 TextTransform 公用程式產生檔案
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

TextTransform 是一種命令列工具，可讓您用來轉換文字模板。 當您呼叫 TextTransform 時，您可以指定文字模板檔案的名稱做為引數。 TextTransform 會呼叫文字轉換引擎，並處理文字模板。 TextTransform 通常會從腳本呼叫。 不過，通常不需要這麼做，因為您可以在 Visual Studio 或在組建程式中執行文字轉換。

> [!NOTE]
> 如果您想要在建立程式中執行文字轉換，請考慮使用「MSBuild 文字轉換」工作。 如需詳細資訊，請參閱[在組建流程中產生程式碼](../modeling/code-generation-in-a-build-process.md)。 在安裝 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 的電腦上，您也可以撰寫可轉換文字模板的應用程式或 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 延伸模組。 如需詳細資訊，請參閱[使用自訂主機處理文字模板](../modeling/processing-text-templates-by-using-a-custom-host.md)。

 TextTransform 位於下列目錄：

 **\Program Files\Common Files\Microsoft Shared\TextTemplating\11。0**

## <a name="syntax"></a>語法

```
TextTransform [<options>] <templateName>
```

#### <a name="parameters"></a>參數

|**引數**|**說明**|
|------------------|---------------------|
|`templateName`|識別您想要轉換的範本檔案名。|

|**選項**|**說明**|
|----------------|---------------------|
|**-out** \<filename >|寫入轉換輸出的目標檔案。|
|**-r** \<assembly >|用來編譯和執行文字模板的元件。|
|**-u** \<namespace >|用來編譯範本的命名空間。|
|**-I** \<includedirectory >|目錄，其中包含指定之文字模板中包含的文字模板。|
|**-P** \<referencepath >|目錄，用來搜尋文字模板中指定的元件，或使用 **-r**選項。<br /><br /> 例如，若要包含用於 Visual Studio API 的元件，請使用<br /><br /> `-P "%VSSHELLFOLDER%\Common7\IDE\PublicAssemblies"`|
|**-dp** \<processorName >！\<className >！\<assemblyName&#124;程式碼基底 >|指示詞處理器的名稱、完整類型名稱和元件，可以用來處理文字模板內的自訂指示詞。|
|**-a** [processorName]！[directiveName]!\<parameterName >！\<parameterValue >|指定指示詞處理器的參數值。 如果您只指定參數名稱和值，則所有指示詞處理器都可使用參數。 如果您指定指示詞處理器，則參數僅適用于指定的處理器。 如果您指定指示詞名稱，只有在處理指定的指示詞時，才可以使用參數。<br /><br />  在文字模板中，在範本指示詞中包含 `hostspecific`，並在 `this.Host` 上叫用訊息。 例如:<br /><br /> `<#@template language="c#" hostspecific="true"#> [<#= this.Host.ResolveParameterValue("", "", "parameterName") #>]`<br /><br /> 請一律輸入 '！ ' 標記，即使您省略選擇性的處理器和指示詞名稱也一樣。 例如:<br /><br /> `-a !!param!value`|
|**-h**|提供協助。|

## <a name="related-topics"></a>相關主題

|工作|主題|
|----------|-----------|
|在 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 方案中產生檔案。|[使用 T4 文字範本在設計階段產生程式碼](../modeling/design-time-code-generation-by-using-t4-text-templates.md)|
|撰寫指示詞處理器，以轉換您專屬的資料來源。|[自訂 T4 文字轉換](../modeling/customizing-t4-text-transformation.md)|
|撰寫文字模板化主機，可讓您從自己的應用程式叫用文字模板。|[使用自訂主機處理文字範本](../modeling/processing-text-templates-by-using-a-custom-host.md)|
