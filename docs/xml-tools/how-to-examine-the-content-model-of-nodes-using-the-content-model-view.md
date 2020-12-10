---
title: 檢查節點的內容模型
description: 瞭解如何使用 XML 架構設計工具中的內容模型視圖，檢查 XML 架構中節點的內容模型。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: c42ddac8-b0e3-48d6-9832-112a19d6c104
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f3ce3d1a47125c446521ceb60a851322c37209d0
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "96995274"
---
# <a name="how-to-examine-the-content-model-of-nodes-by-using-the-content-model-view"></a>如何：使用內容模型視圖來檢查節點的內容模型

本主題描述如何使用 [內容模型視圖](../xml-tools/content-model-view.md)來探索您的節點。

## <a name="to-create-a-new-xsd-file-and-display-the-root-element-in-the-content-model-view"></a>建立新的 XSD 檔案，並且在內容模型檢視中顯示根項目

1. 建立新的 XML 結構描述檔案。

2. 按一下 [使用 XML 編輯器]，即可在 [開始] 視圖上 **查看和編輯基礎 XML 架構** 檔案。

3. 從 [範例 xml 架構：採購單架構](../xml-tools/sample-xsd-file-purchase-order-schema.md) 中複製並貼上 xml 架構範例程式碼，以取代依預設加入至新 XSD 檔案的程式碼。

4. 以 `purchaseOrder` 滑鼠右鍵按一下 [xml 編輯器] 中的專案 `purchaseOrder` ，然後選取 [ **在 Xml Explorer 中顯示**]，以選取 [架構瀏覽器] 中的元素。

5. `purchaseOrder`在 [XML Explorer] 中，以滑鼠右鍵按一下，然後選取 [**在內容模型視圖中顯示**]。

     內容模型檢視的設計介面上會顯示 `purchaseOrder` 項目。

6. 在每個節點上按兩下，或按一下每個節點右邊的雙箭頭，展開 `shipTo`、`billTo` 和 `items` 節點。

     `purchaseOrder` 項目的節點已展開，您可以查看該項目的內容模型。

7. 按一下 `purchaseOrder` 項目下的任何節點並查看階層連結列，以查看所選節點在結構描述集中的位置。

8. 按一下 XSD 工具列中的 [ **顯示檔** ] 按鈕，以切換檔。 您也可以以滑鼠右鍵按一下設計介面來切換文件。

9. 以滑鼠右鍵按一下 `purchaseOrder` 節點，然後選取 [ **產生範例 xml** ] 以查看 XML 實例檔。
