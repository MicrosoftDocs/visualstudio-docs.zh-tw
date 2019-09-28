---
title: 要逸出的特殊字元 | Microsoft Docs
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ca7df1c087e35fd188461382e4f44de6ab703964
ms.sourcegitcommit: 16175e0cea6af528e9ec76f0b94690faaf1bed30
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/28/2019
ms.locfileid: "71481959"
---
# <a name="special-characters-to-escape"></a>要逸出的特殊字元
只有正在使用特殊字元的內容中，特殊字元具有特殊意義時，才必須逸出。 例如，星號 (*) 只有在項目定義的 "Include" 和 "Exclude" 屬性中，或是呼叫  <xref:Microsoft.Build.Tasks.CreateItem> 時，才是特殊字元。 在其他情況下，星號會視為星號常值。 雖然您不需要逸出專案檔中的所有星號，但要這麼做也無妨。

 請使用標記 %\<xx> 取代特殊字元，其中 \<xx> 代表 ASCII 字元的十六進位值。 例如，若要使用星號 (*) 做為常值字元，請使用值 `%2A`。

 要逸出的特殊字元完整清單如下：

|字元|描述|
|---------------|-----------------|
|%|百分比符號，用以參考中繼資料。|
|$|錢幣符號，用以參考屬性。|
|@|@ 記號，用以參考項目清單。|
|(|左括號，用於清單中。|
|)|右括號，用於清單中。|
|;|分號，清單分隔字元。|
|?|問號，在項目的 Include/Exclude 區段中描述檔案規格時為萬用字元。|
|*|星號，在項目的 Include/Exclude 區段中描述檔案規格時為萬用字元。|

> [!NOTE]
> 在某些情況下，您可能需要將雙引號（"）字元（例如在 @no__t 0 工作內使用時）加以轉義。

## <a name="see-also"></a>另請參閱
- [如何：在 MSBuild 中逸出特殊字元](../msbuild/how-to-escape-special-characters-in-msbuild.md)
- [MSBuild 參考](../msbuild/msbuild-reference.md)
