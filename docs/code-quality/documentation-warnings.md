---
title: 檔警告
ms.date: 09/16/2019
ms.topic: reference
f1_keywords:
- vs.codeanalysis.documentationrules
helpviewer_keywords:
- documentation warnings
- managed code analysis warnings, documentation warnings
- warnings, documentation
author: mavasani
ms.author: mavasani
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 00b42dc20b228e30a9b2632a0525a1ec8a9ddbb1
ms.sourcegitcommit: 541a0556958201ad6626bc8638406ad02640f764
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2019
ms.locfileid: "71079206"
---
# <a name="documentation-warnings"></a>檔警告

檔警告支援透過正確使用外部可見 Api 的[XML 檔批註](https://docs.microsoft.com/dotnet/csharp/codedoc)，來撰寫妥善記載的程式庫。

## <a name="in-this-section"></a>本節內容

| 規則 | 描述 |
| - | - |
| [CA1200:避免使用具有前置詞的 cref 標記](../code-quality/ca1200.md) | XML 檔標記中的[cref](https://docs.microsoft.com/dotnet/csharp/programming-guide/xmldoc/cref-attribute)屬性工作表示「程式碼參考」。 它會指定標記的內部文字是程式碼項目，例如類型、方法或屬性。 請避免`cref`使用具有前置詞的標記，因為它會防止編譯器驗證參考。 它也會防止 Visual Studio 的整合式開發環境（IDE）在重構期間尋找和更新這些符號參考。 |

## <a name="see-also"></a>另請參閱

- [程式碼分析警告](../code-quality/code-analysis-for-managed-code-warnings.md)
