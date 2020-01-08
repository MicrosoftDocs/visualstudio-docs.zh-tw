---
title: 如何：在視圖和 XML 編輯器之間切換
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: cb69fbbd-d99c-439e-9498-5df9050f8df0
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 54e43b00c877f5453d1dc28bbc9d5546fcef056f
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/01/2020
ms.locfileid: "75592618"
---
# <a name="how-to-switch-between-views-and-the-xml-editor"></a>如何：在視圖和 XML 編輯器之間切換

本主題說明如何在 XML 架構設計工具（XSD 設計工具）和 XML 編輯器之間切換。 這個範例會使用[採購單架構](../xml-tools/sample-xsd-file-simple-schema.md)。

## <a name="to-switch-between-the-views-and-the-xml-editor"></a>在視圖和 XML 編輯器之間切換

1. 若要建立和編輯新的 XML 架構檔案，請依照[如何：建立和編輯 XSD 架構](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md)檔案中的步驟執行。

2. 若要從 XML 編輯器切換至 XML 架構設計工具，請以滑鼠右鍵按一下 XML 編輯器中的任何位置，然後選取 [ **View Designer**]。

3. 若要使用浮水印切換至圖表視圖，請按一下 [**使用圖表視圖] 查看 [開始] 視圖上 [節點間的關聯性]** 連結。

4. 將 [`USAddress`] 節點從 [ **XML 架構瀏覽器**] 拖曳至 [圖表] 視圖。 以滑鼠右鍵按一下圖形視圖中的 [`USAddress`] 節點，然後選取操作功能表中的 [**在內容模型視圖中顯示**]。

     內容模型檢視隨即出現，其中包含 `USAddress` 節點的詳細資訊。

5. 若要使用工具列從內容模型視圖切換到 [開始] 視圖，請按一下 XSD 工具列上的 [**開始視圖**] 按鈕。

6. 若要使用快速鍵在不同的視圖之間切換，請按**ctrl**+**1**作為 [開始] 視圖，針對 [圖形] 視圖按**ctrl**+**2** ，並針對 [內容模型] 視圖按**ctrl**+**3** 。

7. 若要從內容模型視圖移至 XML 編輯器，請以滑鼠右鍵按一下節點，然後選取操作功能表中的 [**查看程式碼**]。
