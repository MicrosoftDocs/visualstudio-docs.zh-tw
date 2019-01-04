---
title: Code map 速度很慢
ms.date: 05/16/2018
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.workload:
- multiple
ms.openlocfilehash: 5a7892e8e0bc347c4a22dd1a2ae2ee4b01882d6c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53905055"
---
# <a name="improve-performance-for-code-maps"></a>改善效能的 code map

當您第一次產生對應時，Visual Studio 會為所有找到的相依性編製索引。 此程序可能需要一些時間，特別是針對大型方案，但可改善之後的效能。 如果程式碼變更，則 Visual Studio 只會重新編製更新過的程式碼索引。 若要完成轉譯對應所花費的時間降到最低，請考慮下列建議：

- [只對應您感興趣的相依性。](#create-a-code-map-to-see-specific-dependencies)

- 在您產生整個方案的對應前，請縮小方案範圍。

- 關閉自動建置方案，方法是選取**略過建置**code map 工具列上。

- 關閉選取的父項目自動加入**包含父代**code map 工具列上。

   ![略過組建及包含父代按鈕](../modeling/media/codemapsfilterskipbuildicons.png)

- 編輯 Code Map，直接移除您不需要的節點和連結。 變更對應不會影響基礎程式碼。 請參閱 [藉由編輯 DGML 檔案自訂 Code Map](../modeling/customize-code-maps-by-editing-the-dgml-files.md)。

可能需要更多時間來建立對應或新增至從對應的項目**方案總管**的專案項目時**複製到輸出目錄**屬性設定為**永遠複製**。 若要增加效能，請將這個屬性變更為 **有更新時才複製** 或 `PreserveNewest`。 請參閱[累加建置](../msbuild/incremental-builds.md)。

完成的對應圖只會針對成功建置的程式碼的相依性。 如果某些元件發生建置錯誤，則對應上會出現這些錯誤。 在根據對應進行架構決策前，請確定元件可實際建置且具有相依性。