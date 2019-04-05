---
title: 從特定領域語言產生程式碼 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: e3706cc9-2afd-456a-a879-68425a248ebc
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 63e1b48a7582294c200b1e30147d85a9b26165d4
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58943519"
---
# <a name="generating-code-from-a-domain-specific-language"></a>從網域指定的語言產生程式碼
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Microsoft[!INCLUDE[dsl](../includes/dsl-md.md)]提供功能強大的方式，從模型中表示的資料產生程式碼、 文件、 組態檔和其他成品。 使用[!INCLUDE[dsl](../includes/dsl-md.md)]，您可以建立一組類別，代表您的資料，您可以撰寫文字範本中的類別名稱和屬性會反映該資料。  
  
 例如，Fabrikam 有客戶名稱和電子郵件地址的 XML 檔案。 開發人員建立客戶的類別，具有屬性名稱和電子郵件模型。 他們撰寫來處理資料，包括 HTML 網頁的過程中產生的所有客戶資料表的這個片段的數個文字範本：  
  
```  
<table>  
<# foreach (Customer c in ContactList) {  #>  
  <tr><td> <#= c.FullName #> </td>   
      <td> <#= c.EmailAddress #> </td> </tr>  
<# } #>  </table>  
```  
  
 當處理客戶資料庫時，會將 XML 檔案讀入模型存放區。 A*指示詞處理器*、 建立使用[!INCLUDE[dsl](../includes/dsl-md.md)]，讓 Customer 類別的程式碼可以使用文字範本中。 針對相同的存放區，可以執行多個文字範本。  
  
 文字範本是必要項目[!INCLUDE[dsl](../includes/dsl-md.md)]。 它們用來產生 VSPackage 和控制項用來整合的工具以及網域模型的項目原始程式碼[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]。  
  
 本章節將討論如何建立、 修改和偵錯文字範本中所使用的一些[!INCLUDE[dsl](../includes/dsl-md.md)]。  
  
## <a name="in-this-section"></a>本節內容  
 [從文字範本存取模型](../modeling/accessing-models-from-text-templates.md)  
  
 提供有關指的文字範本中的特定領域語言的基本資訊。  
  
 [逐步解說：偵錯存取模型的文字範本](../modeling/walkthrough-debugging-a-text-template-that-accesses-a-model.md)  
  
 描述如何進行疑難排解和偵錯是指特定領域語言的文字範本。  
  
 [逐步解說：將主機連線至產生的指示詞處理器](../modeling/walkthrough-connecting-a-host-to-a-generated-directive-processor.md)  
  
 描述如何將自訂主機連線至產生的指示詞處理器。  
  
 [DslTextTransform 命令](../modeling/the-dsltexttransform-command.md)  
  
 說明的命令檔，以參考特定領域語言的文字範本在命令列上執行的 TextTransform 可執行檔。  
  
## <a name="reference"></a>參考資料  
 [撰寫 T4 文字範本](../modeling/writing-a-t4-text-template.md)  
  
 提供的文字範本指示詞和控制區塊的語法。  
  
## <a name="related-sections"></a>相關章節  
 [使用 T4 文字範本在設計階段產生程式碼](../modeling/design-time-code-generation-by-using-t4-text-templates.md)  
  
 說明文字範本轉換流程。  
  
 [建置流程中的程式碼產生](../modeling/code-generation-in-a-build-process.md)  
  
 如果您要從組建伺服器上的 DSL 中產生檔案，請閱讀本主題。
