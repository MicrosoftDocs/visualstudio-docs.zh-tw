---
title: 從網域指定的語言產生程式碼
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 63599452347ce08140d4c530aa87f2deb938104d
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
ms.locfileid: "31948089"
---
# <a name="generating-code-from-a-domain-specific-language"></a>從網域指定的語言產生程式碼
Microsoft[!INCLUDE[dsl](../modeling/includes/dsl_md.md)]提供強大的方式，來從表示模型中的資料產生程式碼、 文件、 組態檔和其他成品。 使用[!INCLUDE[dsl](../modeling/includes/dsl_md.md)]，您可以建立一組類別，代表您的資料，您可以撰寫文字範本的類別名稱和屬性會反映該資料。

 例如，Fabrikam 有客戶名稱及電子郵件地址的 XML 檔案。 其開發人員建立客戶的類別，具有屬性名稱和電子郵件模型。 寫入數個文字範本來處理資料，包括此片段會產生資料表的所有客戶的 HTML 網頁的一部分：

```
<table>
<# foreach (Customer c in ContactList) {  #>
  <tr><td> <#= c.FullName #> </td>
      <td> <#= c.EmailAddress #> </td> </tr>
<# } #>  </table>
```

 當處理客戶資料庫時，會將 XML 檔案讀取到模型存放區。 A*指示詞處理器*建立使用[!INCLUDE[dsl](../modeling/includes/dsl_md.md)]，使 「 客戶 」 類別的程式碼能夠在文字範本中。 許多的文字範本可以針對相同的存放區來執行。

 文字範本，是必要條件[!INCLUDE[dsl](../modeling/includes/dsl_md.md)]。 它們用來產生原始程式碼的 VSPackage 和控制項，可用來將與工具整合以及網域模型項目[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。

 本章節將討論的數種方式來建立、 修改和偵錯文字範本中使用[!INCLUDE[dsl](../modeling/includes/dsl_md.md)]。

## <a name="in-this-section"></a>本節內容
 [從文字範本存取模型](../modeling/accessing-models-from-text-templates.md)

 提供有關特定領域語言的文字範本中參照的基本資訊。

 [逐步解說：偵錯存取模型的文字範本](../modeling/walkthrough-debugging-a-text-template-that-accesses-a-model.md)

 說明如何進行疑難排解和偵錯文字範本，它是指特定領域語言。

 [逐步解說：將主機連接至產生的指示詞處理器](../modeling/walkthrough-connecting-a-host-to-a-generated-directive-processor.md)

 描述如何連接到產生指示詞處理器的自訂主機。

 [DslTextTransform 命令](../modeling/the-dsltexttransform-command.md)

 描述命令檔參考的特定領域語言的文字範本在命令列上執行的 TextTransform 可執行檔。

## <a name="reference"></a>參考資料
 [撰寫 T4 文字範本](../modeling/writing-a-t4-text-template.md)

 提供的文字範本指示詞和控制區塊的語法。

## <a name="related-sections"></a>相關章節
 [使用 T4 文字範本在設計階段產生程式碼](../modeling/design-time-code-generation-by-using-t4-text-templates.md)

 說明文字範本轉換流程。

 [建置流程中的程式碼產生](../modeling/code-generation-in-a-build-process.md)

 如果您正在從組建伺服器上的 DSL 來產生檔案，請閱讀本主題。