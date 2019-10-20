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
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72666103"
---
# <a name="generating-code-from-a-domain-specific-language"></a>從網域指定的語言產生程式碼
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Microsoft [!INCLUDE[dsl](../includes/dsl-md.md)] 提供一種強大的方式，可從模型中所代表的資料產生程式碼、檔、設定檔和其他成品。 您可以使用 [!INCLUDE[dsl](../includes/dsl-md.md)] 來建立一組代表資料的類別，也可以在名稱和屬性反映該資料的類別中撰寫文字模板。

 例如，Fabrikam 有客戶名稱和電子郵件地址的 XML 檔案。 他們的開發人員建立了一個模型，其中 Customer 是一個類別，其中包含屬性名稱和電子郵件。 它們會撰寫數個文字模板來處理資料，包括此片段會產生所有客戶的資料表做為 HTML 網頁的一部分：

```
<table>
<# foreach (Customer c in ContactList) {  #>
  <tr><td> <#= c.FullName #> </td>
      <td> <#= c.EmailAddress #> </td> </tr>
<# } #>  </table>
```

 處理客戶資料庫時，會將 XML 檔案讀入模型存放區中。 使用 [!INCLUDE[dsl](../includes/dsl-md.md)] 建立的指示詞*處理器*，可將 Customer 類別提供給文字模板中的程式碼使用。 許多文字模板都可以針對相同的存放區來執行。

 文字模板是 [!INCLUDE[dsl](../includes/dsl-md.md)] 的必備要素。 它們可用來產生領域模型專案的原始程式碼，以及用來將工具與 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 整合的 VSPackage 和控制項。

 本節討論一些建立、修改和調試 [!INCLUDE[dsl](../includes/dsl-md.md)] 中使用之文字模板的方式。

## <a name="in-this-section"></a>本章節內容
 [從文字範本存取模型](../modeling/accessing-models-from-text-templates.md)

 提供有關在文字模板中參考特定領域語言的基本資訊。

 [逐步解說：偵錯存取模型的文字範本](../modeling/walkthrough-debugging-a-text-template-that-accesses-a-model.md)

 描述如何在參照特定領域語言的文字模板上進行疑難排解和偵錯工具。

 [逐步解說：將主機連接至產生的指示詞處理器](../modeling/walkthrough-connecting-a-host-to-a-generated-directive-processor.md)

 說明如何將自訂主機連接至產生的指示詞處理器。

 [DslTextTransform 命令](../modeling/the-dsltexttransform-command.md)

 描述在命令列上執行 TextTransform 可執行檔的命令檔，以參考特定領域語言的文字模板。

## <a name="reference"></a>參考資料
 [撰寫 T4 文字範本](../modeling/writing-a-t4-text-template.md)

 提供文字模板指示詞和控制區塊的語法。

## <a name="related-sections"></a>相關章節
 [使用 T4 文字範本在設計階段產生程式碼](../modeling/design-time-code-generation-by-using-t4-text-templates.md)

 解說文字範本轉換程式。

 [建置流程中的程式碼產生](../modeling/code-generation-in-a-build-process.md)

 如果您是從組建伺服器上的 DSL 產生檔案，請閱讀本主題。
