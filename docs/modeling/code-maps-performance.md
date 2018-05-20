---
title: Code map 很慢
ms.date: 05/16/2018
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: 2dece1e63fffdba67678422ad9241babc63b7abd
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2018
---
# <a name="improve-performance-for-code-maps"></a>改善效能的 code map

當您第一次產生對應時，Visual Studio 會為所有找到的相依性編製索引。 此程序可能需要一些時間，特別是針對大型方案，但可改善更新的效能。 如果程式碼變更，則 Visual Studio 只會重新編製更新過的程式碼索引。 若要將完成轉譯對應所花費的時間降到最低，請考慮下列建議：

- [對應您感興趣的相依性。](#create-a-code-map-to-see-specific-dependencies)

- 在您產生整個方案的對應前，請縮小方案範圍。

- 關閉自動建置方案，只要選取**略過建置**code map 工具列上。

- 關閉選取的父項目自動加入**包含父代**code map 工具列上。

   ![略過組建及包含父代按鈕](../modeling/media/codemapsfilterskipbuildicons.png)

- 編輯 Code Map，直接移除您不需要的節點和連結。 變更對應不會影響基礎程式碼。 請參閱 [藉由編輯 DGML 檔案自訂 Code Map](../modeling/customize-code-maps-by-editing-the-dgml-files.md)。

可能需要更多時間來建立對應，或將項目加入至地圖**方案總管 中**時的專案項目**複製到輸出目錄**屬性設定為**永遠複製**。 若要增加效能，請將這個屬性變更為 **有更新時才複製** 或 `PreserveNewest`。 請參閱[累加建置](../msbuild/incremental-builds.md)。

已完成的對應可顯示相依性，僅針對已成功建置程式碼。 如果某些元件發生建置錯誤，則對應上會出現這些錯誤。 在根據對應進行架構決策前，請確定元件可實際建置且具有相依性。