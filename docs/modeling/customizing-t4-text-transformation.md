---
title: 自訂 T4 文字轉換
description: 瞭解如何藉由自訂文字模板指示詞處理器或文字模板主機，來擴充預設的範本轉換流程。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, API
- text templates, custom hosts
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4565e710d1b3172507cb3f966cd2a920d3b3aaa8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99935400"
---
# <a name="customize-t4-text-transformation"></a>自訂 T4 文字轉換

文字模板是 Visual Studio 的功能，可讓您透過轉換進程產生程式碼或其他文字檔。 使用 [!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)] ，您可以自訂文字模板指示詞處理器或文字模板主機，以擴充預設的範本轉換程式。

## <a name="in-this-section"></a>本節內容

 [文字模板轉換流程](../modeling/the-text-template-transformation-process.md) 描述文字轉換的運作方式，並說明範本主機和指示詞處理器的角色。

 [建立自訂 T4 文字模板](../modeling/creating-custom-t4-text-template-directive-processors.md) 指示詞處理器指示詞處理器會處理範本中的指示詞，例如 `<#@template#>.` 它會在編譯範本期間執行，而且可以載入元件和其他資源。 它也可以插入會在執行時間載入資源的程式碼。 藉由定義您自己的指示詞處理器，您可以降低範本的複雜度。

 叫[用 VS 擴充功能中的文字轉換](../modeling/invoking-text-transformation-in-a-vs-extension.md)如果您要撰寫 Visual Studio 的延伸模組（例如功能表命令或事件處理常式），則您的延伸模組可以使用文字模板化服務來轉換任何文字模板。 您可以使用 Session 物件將參數資料傳遞到範本中，並使用指示詞從範本中取得值 `<#@parameter#>` 。

 [使用自訂主機處理文字模板](../modeling/processing-text-templates-by-using-a-custom-host.md) 當文字模板的程式碼執行時，主機會提供外部檔案和應用程式狀態的存取權。 例如，在 Visual Studio 中執行文字轉換的主控制項可提供 **方案總管** 的存取權。 它也會在 [錯誤訊息] 視窗中顯示錯誤。 如果您想要在不同的內容中執行文字轉換，您可以定義自己的主控制項，以提供該內容中可用之服務的存取權。

 如果您要撰寫 Visual Studio 擴充功能，請考慮使用現有的文字轉換服務，而不是撰寫您自己的主控制項。 如需詳細資訊，請參閱 [在 VS 延伸模組中叫用文字轉換](../modeling/invoking-text-transformation-in-a-vs-extension.md)。

## <a name="reference"></a>參考

- [撰寫 T4 文字模板](../modeling/writing-a-t4-text-template.md) 提供文字模板指示詞和控制區塊的語法。
