---
title: 針對程式碼片段的問題進行疑難排解
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: troubleshooting
helpviewer_keywords:
- IntelliSense Code Snippets, troubleshooting
- troubleshooting IntelliSense Code Snippets
- troubleshooting Visual Basic, IntelliSense Code Snippets
ms.assetid: 7b6dd40e-2f78-4b50-8e68-41fac1bcb81e
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 79db18df9f9961a539eb0efb3dd399f9be85a276
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54943243"
---
# <a name="troubleshoot-snippets"></a>針對程式碼片段的問題進行疑難排解

IntelliSense 程式碼片段的問題通常是由兩個問題所造成：損毀的程式碼片段檔案或程式碼片段檔案中有錯誤內容。

## <a name="the-snippet-cannot-be-dragged-from-file-explorer-to-a-visual-studio-source-file"></a>程式碼片段無法從 [檔案總管] 拖曳至 Visual Studio 的原始程式檔

- 程式碼片段檔案中的 XML 可能已損毀。 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 的 **XML 編輯器**可以找出 XML 結構中的問題。

- 程式碼片段檔案可能不符合程式碼片段結構描述。 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 的 **XML 編輯器**可以找出 XML 結構中的問題。

## <a name="the-code-has-compiler-errors-that-are-not-highlighted"></a>程式碼有未反白顯示的編譯器錯誤

-   您可能遺漏了專案參考。 檢查有關程式碼片段的文件。 如果電腦上找不到參考，您需要安裝它。 插入程式碼片段應該會在專案中新增所有需要的參考。 如果程式碼片段遺漏了參考資訊，可向程式碼片段建立者報告為錯誤。

-   可能未定義變數。 程式碼片段中未定義的變數應予反白顯示。 否則，會向程式碼片段建立者報告為錯誤。

## <a name="see-also"></a>另請參閱

- [程式碼片段](../ide/code-snippets.md)
