---
title: MSBuild 特殊字元 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- escape characters
- escape
- MSBuild Escape Characters
ms.assetid: 545e6a59-1093-4514-935e-78679a46fb3c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a87013ff3a1911caa667f7ba431e408fc87a98f4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63004635"
---
# <a name="msbuild-special-characters"></a>MSBuild 特殊字元
[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 保留一些針對特定內容中特殊用法的字元。 如果您想要在保留這些字元的內容中按字面使用這些字元，只需要將其逸出即可。 比方說，星號僅在項目定義的 `Include` 和 `Exclude` 屬性，以及 `CreateItem` 呼叫中具有特殊意義。 如果您想要將這些內容之一的星號顯示為星號，則必須將其逸出。 而在其他內容中，您只要在想要顯示的位置鍵入星號即可。

 若要逸出特殊字元，請使用 %\<xx> 語法，其中 \<xx> 代表字元的 ASCII 十六進位值。 如需詳細資訊，請參閱[如何：在 MSBuild 中逸出特殊字元](../msbuild/how-to-escape-special-characters-in-msbuild.md)。

## <a name="special-characters"></a>特殊字元
 下表列出 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 特殊字元：

|**字元**|**ASCII**|**保留的使用方式**|
|-------------------|---------------|------------------------|
|%|%25|參考中繼資料|
|$|%24|參考屬性|
|@|%40|參考項目清單|
|\'|%27|條件和其他運算式|
|;|%3B|清單分隔字元|
|?|%3F|`Include` 和 `Exclude` 屬性中的檔案名稱萬用字元|
|*|%2A|用於 `Include` 和 `Exclude` 屬性中的檔案名稱萬用字元|

## <a name="see-also"></a>另請參閱
- [進階概念](../msbuild/msbuild-advanced-concepts.md)
- [項目](../msbuild/msbuild-items.md)