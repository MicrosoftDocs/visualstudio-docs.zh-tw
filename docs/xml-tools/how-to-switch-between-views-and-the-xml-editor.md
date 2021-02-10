---
title: 如何：在視圖與 XML 編輯器之間切換
description: 瞭解如何在 XML 架構設計工具 (XSD 設計工具) 視圖和 XML 編輯器之間切換。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: cb69fbbd-d99c-439e-9498-5df9050f8df0
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e14947bfb31fbf6fcb2246223a2394194a45035e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99970968"
---
# <a name="how-to-switch-between-views-and-the-xml-editor"></a>如何：在視圖與 XML 編輯器之間切換

本主題說明如何在 XML 架構設計工具 (XSD 設計工具) 視圖和 XML 編輯器之間切換。 此範例會使用訂單 [架構](../xml-tools/sample-xsd-file-simple-schema.md)。

## <a name="to-switch-between-the-views-and-the-xml-editor"></a>在 views 和 XML 編輯器之間切換

1. 若要建立和編輯新的 XML 架構檔案，請依照 how [to：建立和編輯 XSD 架構](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md)檔案中的步驟執行。

2. 若要從 XML 編輯器切換至 XML 架構設計工具，請以滑鼠右鍵按一下 XML 編輯器中的任何位置，然後選取 [ **視圖設計** 工具]。

3. 若要使用浮水印切換至圖形視圖，請按一下 [ **使用圖表視圖]，以查看開始視圖上的節點連結之間的關聯** 性。

4. 將 `USAddress` 節點從 **XML 架構瀏覽器** 拖曳到圖形視圖上。 以滑鼠右鍵按一下 `USAddress` [圖形] 視圖中的節點，然後在內容功能表中選取 [ **在內容模型視圖中顯示** ]。

     內容模型檢視隨即出現，其中包含 `USAddress` 節點的詳細資訊。

5. 若要使用工具列從內容模型視圖切換至開始視圖，請按一下 XSD 工具列上的 [ **開始視圖** ] 按鈕。

6. 若要在使用快速鍵的視圖之間切換，請按 **ctrl** + **1** 以進行 [開始] 視圖、按 **ctrl** + **2** （適用于圖形視圖）和 **ctrl** + **3** （內容模型視圖）。

7. 若要從內容模型視圖移至 XML 編輯器，請以滑鼠右鍵按一下節點，然後選取內容功能表中的 [ **View Code** ]。
