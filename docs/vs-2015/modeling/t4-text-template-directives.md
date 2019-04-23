---
title: T4 文字範本指示詞 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- text templates, import directive
- text templates, include directive
- text templates, assembly directive
- text templates, output directive
- text templates, directives
- text templates, template directive
ms.assetid: 6898ee02-ebb2-4635-a4e9-350774c13cf2
caps.latest.revision: 83
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 6f5c4c474ad737add8580381e7fda5fb0b0c1afc
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60044833"
---
# <a name="t4-text-template-directives"></a>T4 文字範本指示詞
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

指示詞會提供指令給文字範本轉換引擎。  
  
 指示詞的語法如下：  
  
```  
<#@ DirectiveName [AttributeName = "AttributeValue"] ... #>  
```  
  
 所有屬性值都必須包含在雙引號中。 如果值本身包含引號，則必須以 \ 字元逸出。  
  
 指示詞通常是範本檔案或被納入的檔案中的第一個項目。 在 `<#...#>` 程式碼區塊內，或 `<#+...#>` 類別功能區塊後面，都不應該放置指示詞。  
  
 [T4 範本指示詞](../modeling/t4-template-directive.md)  

```  
<#@ template [language="VB"] [hostspecific="true|TrueFromBase"] [debug="true"] [inherits="templateBaseClass"] [culture="code"] [compilerOptions="options"] [visibility="internal"] [linePragmas="false"] #>  
```  
  
 [T4 參數指示詞](../modeling/t4-parameter-directive.md)  

```  
<#@ parameter type="Full.TypeName" name="ParameterName" #>  
```  
  
 [T4 輸出指示詞](../modeling/t4-output-directive.md)  

```  
<#@ output extension=".fileNameExtension" [encoding="encoding"] #>  
```  
  
 [T4 組件指示詞](../modeling/t4-assembly-directive.md)  

```  
<#@ assembly name="[assembly strong name|assembly file name]" #>  
```  
  
 [T4 匯入指示詞](../modeling/t4-import-directive.md)  

```  
<#@ import namespace="namespace" #>  
```  
  
 [T4 包含指示詞](../modeling/t4-include-directive.md)  

```  
<#@ include file="filePath" #>  
```  
  
 [T4 CleanUpBehavior 指示詞](../modeling/t4-cleanupbehavior-directive.md)  

```  
<#@ CleanupBehavior processor="T4VSHost" CleanupAfterProcessingtemplate="true" #>  
```  
  
 此外，您也可以建立自己的指示詞。 如需詳細資訊，請參閱 <<c0> [ 建立自訂 T4 文字範本指示詞處理器](../modeling/creating-custom-t4-text-template-directive-processors.md)。 如果使用 Visualization and Modeling SDK 建立特定領域語言 (DSL)，則會產生指示詞處理器做為 DSL 的一部分。
