---
title: 取得結構描述集的概觀
description: XML 架構設計工具：瞭解如何使用 XML 架構瀏覽器中的圖表視圖，查看架構集中節點的高階觀點，以及節點之間的關聯性。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: c0df4b0d-52ef-4a6c-9676-1d8311aad7c7
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 699167f8fe3662bbb162706f3f9fc6e5d53d82dc
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "96995287"
---
# <a name="how-to-get-an-overview-of-a-schema-set-by-using-the-graph-view"></a>如何：使用圖形視圖取得架構集的總覽

本主題說明如何使用 [圖形視圖](../xml-tools/graph-view.md) 來查看架構集中節點的高階觀點，以及節點之間的關聯性。

## <a name="to-create-a-new-xsd-file-and-display-the-root-element-in-the-content-model-view"></a>建立新的 XSD 檔案，並且在內容模型檢視中顯示根項目

1. 建立新的 XML 架構檔案，並將檔案儲存為 *xsd.exe 的關聯* 性。

2. 按一下 [使用 XML 編輯器]，即可在 [開始] 視圖上 **查看和編輯基礎 XML 架構** 檔案連結。

3. 從 [範例 xml 架構：關聯](../xml-tools/sample-xsd-file-relationships.md) 性複製並貼上 xml 架構範例程式碼，以取代預設加入至新 XSD 檔案的程式碼。

4. 以滑鼠右鍵按一下 XML 編輯器中的任何位置，然後選取 [ **視圖設計** 工具]。

5. 從 **XSD 工具列** 選取圖表視圖。

6. 在 **XML 架構瀏覽器** 中選取 [**架構集合**] 節點，然後將節點拖曳至圖形視圖的設計介面。 您會看見所有的全域節點，以及連接具有關聯性之節點的箭號。

     ![圖形檢視](../xml-tools/media/relationshipingraphview.gif)

7. 按一下設計介面上的任何節點並查看階層連結列，以查看所選節點在結構描述集中的位置。

8. 在設計介面上的任何專案節點上按一下滑鼠右鍵，然後選取 [ **產生範例 xml** ] 以查看 XML 實例檔。
