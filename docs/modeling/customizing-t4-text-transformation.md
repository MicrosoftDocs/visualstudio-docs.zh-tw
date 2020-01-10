---
title: 自訂 T4 文字轉換
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, API
- text templates, custom hosts
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8e35c279f397f1228c17fb6a41a18a2fe583ab88
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/01/2020
ms.locfileid: "75589730"
---
# <a name="customize-t4-text-transformation"></a>自訂 T4 文字轉換

文字模板是 Visual Studio 的一項功能，可讓您透過轉換進程產生程式碼或其他文字檔。 使用 [!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)]，您可以藉由自訂文字模板指示詞處理器或文字模板主機來擴充預設範本轉換程式。

## <a name="in-this-section"></a>本章節內容

 [文字模板轉換流程](../modeling/the-text-template-transformation-process.md)描述文字轉換的運作方式，並說明範本主機和指示詞處理器的角色。

 [建立自訂 T4 文字模板](../modeling/creating-custom-t4-text-template-directive-processors.md)指示詞處理器指示詞處理器會處理範本中的指示詞，例如在編譯範本時執行 `<#@template#>.`，而且可以載入元件和其他資源。 它也可以插入會在執行時間載入資源的程式碼。 藉由定義您自己的指示詞處理器，您可以降低範本的複雜度。

 叫[用 VS 擴充功能中的文字轉換](../modeling/invoking-text-transformation-in-a-vs-extension.md)如果您要撰寫 Visual Studio 的延伸模組，例如功能表命令或事件處理常式，您的擴充功能可以使用文字模板化服務來轉換任何文字模板。 您可以使用 Session 物件將參數資料傳遞至範本，並使用 `<#@parameter#>` 指示詞從範本內取得值。

 [使用自訂主機處理文字模板](../modeling/processing-text-templates-by-using-a-custom-host.md)當文字模板的程式碼執行時，主機會提供外部檔案的存取權，以及應用程式的狀態。 例如，在 Visual Studio 中執行文字轉換的主控制項，可以提供**方案總管**的存取權。 它也會在錯誤訊息視窗中顯示錯誤。 如果您想要在不同的內容中執行文字轉換，您可以定義自己的主控制項，以提供該內容中可用服務的存取權。

 如果您要撰寫 Visual Studio 延伸模組，請考慮使用現有的文字轉換服務，而不是撰寫您自己的主機。 如需詳細資訊，請參閱叫[用 VS 擴充功能中的文字轉換](../modeling/invoking-text-transformation-in-a-vs-extension.md)。

## <a name="reference"></a>參考資料

- [[撰寫 T4 文字] 範本](../modeling/writing-a-t4-text-template.md)會提供文字模板指示詞和控制區塊的語法。
