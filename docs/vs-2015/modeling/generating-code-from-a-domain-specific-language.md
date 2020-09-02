---
title: 從特定領域語言產生程式碼 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: e3706cc9-2afd-456a-a879-68425a248ebc
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 32cafb9e68fc2535ed3b570022a59d284f4c4cae
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72666103"
---
# <a name="generating-code-from-a-domain-specific-language"></a>從網域指定的語言產生程式碼
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Microsoft [!INCLUDE[dsl](../includes/dsl-md.md)] 提供了一種強大的方式，可從模型中表示的資料產生程式碼、檔、設定檔及其他成品。 使用 [!INCLUDE[dsl](../includes/dsl-md.md)] ，您可以建立一組代表資料的類別，而且您可以在名稱和屬性反映該資料的類別中撰寫文字模板。

 例如，Fabrikam 具有客戶名稱和電子郵件地址的 XML 檔。 他們的開發人員會建立模型，其中客戶是具有屬性名稱和電子郵件的類別。 他們撰寫數個文字模板來處理資料，包括這個片段，它會產生所有客戶的資料表做為 HTML 網頁的一部分：

```
<table>
<# foreach (Customer c in ContactList) {  #>
  <tr><td> <#= c.FullName #> </td>
      <td> <#= c.EmailAddress #> </td> </tr>
<# } #>  </table>
```

 當處理客戶資料庫時，會將 XML 檔案讀入模型存放區。 使用建立的指示詞 *處理器* [!INCLUDE[dsl](../includes/dsl-md.md)] 讓客戶類別可供文字模板中的程式碼使用。 許多文字模板都可以針對相同的存放區執行。

 文字模板是不可或缺的 [!INCLUDE[dsl](../includes/dsl-md.md)] 。 它們可用來產生網域模型專案的原始程式碼，以及用來整合工具的 VSPackage 和控制項的原始程式碼 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 。

 本節將討論一些建立、修改和偵錯工具中使用之文字模板的方式 [!INCLUDE[dsl](../includes/dsl-md.md)] 。

## <a name="in-this-section"></a>本節內容
 [從文字範本存取模型](../modeling/accessing-models-from-text-templates.md)

 提供有關在文字模板中參照特定領域語言的基本資訊。

 [逐步解說：偵錯存取模型的文字範本](../modeling/walkthrough-debugging-a-text-template-that-accesses-a-model.md)

 說明如何針對參考特定領域語言的文字模板進行疑難排解和偵錯工具。

 [逐步解說：將主機連接至產生的指示詞處理器](../modeling/walkthrough-connecting-a-host-to-a-generated-directive-processor.md)

 說明如何將自訂主機連接至產生的指示詞處理器。

 [DslTextTransform 命令](../modeling/the-dsltexttransform-command.md)

 描述在命令列上執行 TextTransform 可執行檔的命令檔，該文字檔會參考特定領域語言的文字模板。

## <a name="reference"></a>參考
 [撰寫 T4 文字範本](../modeling/writing-a-t4-text-template.md)

 提供文字模板指示詞和控制區塊的語法。

## <a name="related-sections"></a>相關章節
 [使用 T4 文字範本在設計階段產生程式碼](../modeling/design-time-code-generation-by-using-t4-text-templates.md)

 解說文字範本轉換流程。

 [建置流程中的程式碼產生](../modeling/code-generation-in-a-build-process.md)

 如果您是從組建伺服器上的 DSL 產生檔案，請閱讀本主題。
