---
title: 要逸出的特殊字元 | Microsoft Docs
description: 瞭解只有在使用這些特殊字元的內容中有特殊意義時，才需要將這些特殊字元換用。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- special characters to escape
- msbuild, special characters to escape
ms.assetid: 5b5172c3-41e4-4f38-a16f-2aeac831a5fc
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5e665c214ea75de67a6c339bb516dfb812936448
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99878145"
---
# <a name="special-characters-to-escape"></a>要逸出的特殊字元

只有正在使用特殊字元的內容中，特殊字元具有特殊意義時，才必須逸出。 例如，星號 (*) 只有在項目定義的 "Include" 和 "Exclude" 屬性中，或是呼叫  <xref:Microsoft.Build.Tasks.CreateItem> 時，才是特殊字元。 在其他情況下，星號會視為星號常值。 雖然您不需要逸出專案檔中的所有星號，但要這麼做也無妨。

 使用標記法% \<xx> 代替特殊字元，其中 \<xx> 代表 ASCII 字元的十六進位值。 例如，若要使用星號 (*) 做為常值字元，請使用值 `%2A`。

 要逸出的特殊字元完整清單如下：

|字元|ASCII 編碼|Description|
|---------|----------|-----------|
|%|%25|百分比符號，用以參考中繼資料。|
|$|%24|錢幣符號，用以參考屬性。|
|@|%40|@ 記號，用以參考項目清單。|
|(|%28|左括號，用於清單中。|
|)|%29|右括號，用於清單中。|
|;|%3B|分號，清單分隔字元。|
|?|%3F|問號，在項目的 Include/Exclude 區段中描述檔案規格時為萬用字元。|
|* |%2A|星號，在項目的 Include/Exclude 區段中描述檔案規格時為萬用字元。|

> [!NOTE]
> 在某些情況下，您可能需要將雙引號 ( ") 字元，例如在工作中使用時 `Exec` 。

## <a name="see-also"></a>另請參閱

- [如何：在 MSBuild 中 Escape 特殊字元](../msbuild/how-to-escape-special-characters-in-msbuild.md)
- [MSBuild 參考](../msbuild/msbuild-reference.md)
