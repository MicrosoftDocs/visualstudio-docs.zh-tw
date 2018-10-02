---
title: T4 文字範本指示詞 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: douge
ms.openlocfilehash: e079b21c3a85f883351808b8defda6d0d68619f7
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47490818"
---
# <a name="t4-text-template-directives"></a>T4 文字範本指示詞
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[T4 文字範本指示詞](https://docs.microsoft.com/visualstudio/modeling/t4-text-template-directives)。  
  
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



