---
title: Code map 很慢
description: 瞭解如何改善 code map 效能，以及如何將完成轉譯所需的時間減至最少。
ms.custom: SEO-VS-2020
ms.date: 05/16/2018
ms.topic: conceptual
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d5a279a04b1bd76933df335bc0b2527ab4b2418f
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2021
ms.locfileid: "112389640"
---
# <a name="improve-performance-for-code-maps"></a>改善 code map 的效能

當您第一次產生對應時，Visual Studio 會為所有找到的相依性編製索引。 此程式可能需要一些時間，特別是針對大型解決方案，但改善了較新的效能。 如果程式碼變更，則 Visual Studio 只會重新編製更新過的程式碼索引。 若要將地圖完成轉譯所需的時間降到最低，請考慮下列建議：

- 只對應您感興趣的相依性。

- 在您產生整個方案的對應前，請縮小方案範圍。

- 選取 code map 工具列上的 [ **略過組建** ]，關閉解決方案的自動組建。

- 選取 code map 工具列上的 [包含父 **代** ]，關閉父專案的自動加入。

   ![略過組建及包含父代按鈕](../modeling/media/codemapsfilterskipbuildicons.png)

- 編輯 Code Map，直接移除您不需要的節點和連結。 變更對應不會影響基礎程式碼。 請參閱 [Customize code maps by editing the DGML files](../modeling/customize-code-maps-by-editing-the-dgml-files.md)。

當專案專案的 [**複製到輸出目錄**] 屬性設定為 [**永遠複製**] 時，從 **方案總管** 建立對應或將專案加入至地圖可能需要更多時間。 若要增加效能，請將這個屬性變更為 **有更新時才複製** 或 `PreserveNewest`。 請參閱累加 [組建](../msbuild/incremental-builds.md)。

完成的對應只會顯示已成功建立程式碼的相依性。 如果某些元件發生建置錯誤，則對應上會出現這些錯誤。 在根據對應進行架構決策前，請確定元件可實際建置且具有相依性。
