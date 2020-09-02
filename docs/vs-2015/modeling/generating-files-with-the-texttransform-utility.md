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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72666088"
---
# <a name="generating-files-with-the-texttransform-utility"></a>使用 TextTransform 公用程式產生檔案
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

TextTransform.exe 是一種命令列工具，可讓您用來轉換文字模板。 當您呼叫 TextTransform.exe 時，您會將文字模板檔案的名稱指定為引數。 TextTransform.exe 會呼叫文字轉換引擎，並處理文字模板。 通常會從腳本呼叫 TextTransform.exe。 不過，這通常不是必要的，因為您可以在 Visual Studio 或在組建程式中執行文字轉換。

> [!NOTE]
> 如果您想要在組建流程中執行文字轉換，請考慮使用 MSBuild 文字轉換工作。 如需詳細資訊，請參閱 [在組建流程中產生程式碼](../modeling/code-generation-in-a-build-process.md)。 在安裝的電腦上 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ，您也可以撰寫 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 可轉換文字模板的應用程式或延伸模組。 如需詳細資訊，請參閱 [使用自訂主機處理文字模板](../modeling/processing-text-templates-by-using-a-custom-host.md)。

 TextTransform.exe 位於下列目錄：

 **\Program Files\Common Files\Microsoft Shared\TextTemplating\11。0**

## <a name="syntax"></a>語法

```
TextTransform [<options>] <templateName>
```

#### <a name="parameters"></a>參數

|**Argument**|**描述**|
|------------------|---------------------|
|`templateName`|識別您要轉換的範本檔案名。|

|**選項**|**說明**|
|----------------|---------------------|
|**-out** \<filename>|寫入轉換輸出的檔案。|
|**-r**\<assembly>|用來編譯和執行文字模板的元件。|
|**-u**\<namespace>|用來編譯範本的命名空間。|
|**-I**\<includedirectory>|包含指定文字模板中所包含文字模板的目錄。|
|**-P**\<referencepath>|用來搜尋文字模板內指定之元件或使用 **-r** 選項的目錄。<br /><br /> 例如，若要包含 Visual Studio API 所使用的元件，請使用<br /><br /> `-P "%VSSHELLFOLDER%\Common7\IDE\PublicAssemblies"`|
|**-dp** \<processorName> ！ \<className> ！\<assemblyName&#124;codeBase>|可以用來處理文字模板內自訂指示詞之指示詞處理器的名稱、完整類型名稱和元件。|
|**-a** [processorName]！[directiveName \<parameterName> ]！！！\<parameterValue>|指定指示詞處理器的參數值。 如果您只指定參數名稱和值，參數將可供所有指示詞處理器使用。 如果您指定指示詞處理器，參數只能提供給指定的處理器。 如果您指定指示詞名稱，只有在處理指定的指示詞時，才能使用此參數。<br /><br />  在文字模板中，將包含在範本指示詞中，並在上叫用 `hostspecific` 訊息 `this.Host` 。 例如：<br /><br /> `<#@template language="c#" hostspecific="true"#> [<#= this.Host.ResolveParameterValue("", "", "parameterName") #>]`.<br /><br /> 一律輸入 '！ ' 標記，即使您省略選擇性的處理器和指示詞名稱也一樣。 例如：<br /><br /> `-a !!param!value`|
|**-h**|提供協助。|

## <a name="related-topics"></a>相關主題

|Task|主題|
|----------|-----------|
|在 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 方案中產生檔案。|[使用 T4 文字範本在設計階段產生程式碼](../modeling/design-time-code-generation-by-using-t4-text-templates.md)|
|撰寫指示詞處理器，以轉換您專屬的資料來源。|[自訂 T4 文字轉換](../modeling/customizing-t4-text-transformation.md)|
|撰寫文字模板化主機，可讓您從自己的應用程式叫用文字模板。|[使用自訂主機處理文字範本](../modeling/processing-text-templates-by-using-a-custom-host.md)|
