---
title: MSBuild 特殊字元 | Microsoft Docs
description: 瞭解 MSBuild 保留字元，以供特定內容中的特殊用途使用，以及何時及如何將這些字元換用。
ms.custom: SEO-VS-2020
ms.date: 06/12/2019
ms.topic: conceptual
helpviewer_keywords:
- escape characters
- escape
- MSBuild Escape Characters
ms.assetid: 545e6a59-1093-4514-935e-78679a46fb3c
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c5db0b870e050a9235f719d83710747101b95c3c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99922534"
---
# <a name="msbuild-special-characters"></a>MSBuild 特殊字元

MSBuild 會在特定內容中保留一些特殊用途的字元。 如果您想要在保留這些字元的內容中按字面使用這些字元，只需要將其逸出即可。 比方說，星號僅在項目定義的 `Include` 和 `Exclude` 屬性，以及 `CreateItem` 呼叫中具有特殊意義。 如果您想要將這些內容之一的星號顯示為星號，則必須將其逸出。 而在其他內容中，您只要在想要顯示的位置鍵入星號即可。

 若要對特殊字元進行 escape，請使用語法% \<xx> ，其中 \<xx> 代表字元的 ASCII 十六進位值。 如需詳細資訊，請參閱 [如何：在 MSBuild 中 Escape 特殊字元](../msbuild/how-to-escape-special-characters-in-msbuild.md)。

## <a name="special-characters"></a>特殊字元

 下表列出 MSBuild 特殊字元：

|**字元**|**ASCII**|**保留的使用方式**|
|-------------------|---------------|------------------------|
|%|%25|參考中繼資料|
|$|%24|參考屬性|
|@|%40|參考項目清單|
|'|%27|條件和其他運算式|
|;|%3B|清單分隔字元|
|?|%3F|`Include` 和 `Exclude` 屬性中的檔案名稱萬用字元|
|*|%2A|用於 `Include` 和 `Exclude` 屬性中的檔案名稱萬用字元|

## <a name="see-also"></a>另請參閱

- [進階概念](../msbuild/msbuild-advanced-concepts.md)
- [項目](../msbuild/msbuild-items.md)
