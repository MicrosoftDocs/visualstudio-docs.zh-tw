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
ms.sourcegitcommit: dda98068c0f62ccd1a19fdfde4bdb822428d0125
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2020
ms.locfileid: "87425952"
---
# <a name="common-msbuild-item-metadata"></a>一般 MSBuild 專案中繼資料

下表描述對某些 MSBuild Sdk 或目標有意義的選擇性專案中繼資料，但預設不會針對每個專案設定。 您可以設定這些來影響組建行為，但只有在您使用的 SDK 或目標檔案可辨識它時才會這樣做。

| 項目中繼資料 | SDK | 描述 |
|---------------| ------- | -------------|
|% （連結）| 全部 |Visual Studio 專案系統會使用 `Link` 中繼資料（如果有的話）來改變專案樹狀結構中顯示的內容; 您可以在**方案總管**中將檔案放在不同的邏輯資料夾結構中。<br />此外，此工作 `AssignTargetPath` 會查看， `Link` 以判斷輸出目錄中要複製檔案的位置（如果它是要複製的其中一個專案）。|
|% （程式庫）| .NET Core SDK | 用來設定要用於 `Link` 專案群組之中繼資料的資料夾。 |

## <a name="see-also"></a>另請參閱

- [一般 MSBuild 專案屬性](../msbuild/common-msbuild-project-properties.md)
- [一般 MSBuild 專案項目](../msbuild/common-msbuild-project-items.md)
- [MSBuild 已知的項目中繼資料](msbuild-well-known-item-metadata.md)