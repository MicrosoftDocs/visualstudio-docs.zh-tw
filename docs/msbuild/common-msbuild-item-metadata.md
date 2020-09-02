---
title: 一般 MSBuild 專案中繼資料 |Microsoft Docs
ms.date: 07/13/2020
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- msbuild, common item metadata
- item metadata (MSBuild)
ms.assetid: 9857505d-ae15-42f1-936d-6cd7fb9dd276
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1c715c16782733a08bb617a464c1aa9510d35b54
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "87425952"
---
# <a name="common-msbuild-item-metadata"></a>一般 MSBuild 項目中繼資料

下表描述具有某些 MSBuild Sdk 或目標之意義的選擇性專案中繼資料，但預設不會針對每個專案設定。 您可以設定這些以影響組建行為，但只有在您使用的 SDK 或目標檔案可辨識它時才會這樣做。

| 項目中繼資料 | SDK | 描述 |
|---------------| ------- | -------------|
|% (連結) | 全部 |Visual Studio 專案系統會使用 `Link` 中繼資料 (如果有) 改變專案樹狀結構中顯示的專案，您可以在 **方案總管**中將檔案放在不同的邏輯資料夾結構中。<br />此外， `AssignTargetPath` `Link` 如果是複製的其中一個專案，則工作會在輸出目錄中查看要將檔案複製到其中的位置。|
|% (程式庫) | .NET Core SDK | 用來設定要用於 `Link` 專案群組之中繼資料的資料夾。 |

## <a name="see-also"></a>另請參閱

- [一般 MSBuild 專案屬性](../msbuild/common-msbuild-project-properties.md)
- [一般 MSBuild 專案項目](../msbuild/common-msbuild-project-items.md)
- [MSBuild 已知的項目中繼資料](msbuild-well-known-item-metadata.md)