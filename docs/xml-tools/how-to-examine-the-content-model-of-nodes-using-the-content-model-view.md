---
title: 在 XML 架構設計工具中使用內容模型視圖檢查節點
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c42ddac8-b0e3-48d6-9832-112a19d6c104
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c109d167534dc969ae34c55d16f2ee55e34fe3aa
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72645892"
---
# <a name="how-to-examine-the-content-model-of-nodes-using-the-content-model-view"></a>如何：使用內容模型視圖檢查節點的內容模型

本主題說明如何使用[內容模型視圖](../xml-tools/content-model-view.md)探索您的節點。

## <a name="to-create-a-new-xsd-file-and-display-the-root-element-in-the-content-model-view"></a>建立新的 XSD 檔案，並且在內容模型檢視中顯示根項目

1. 建立新的 XML 結構描述檔案。

2. 按一下 [使用 XML 編輯器]，即可在 [開始] 視圖上**查看和編輯基礎 XML 架構**檔案。

3. 從[範例 xml 架構：採購單架構](../xml-tools/sample-xsd-file-purchase-order-schema.md)複製並貼上 xml 架構範例程式碼，以取代預設新增至新 XSD 檔案的程式碼。

4. 以滑鼠右鍵按一下 [XML 編輯器] 中的 [`purchaseOrder`] 專案，然後選取 [**在 Xml explorer 中顯示**]，以選取 [架構] explorer 中的 [`purchaseOrder`] 元素

5. 以滑鼠右鍵按一下 XML Explorer 中的 `purchaseOrder`，然後選取 [**在內容模型視圖中顯示**]。

     內容模型檢視的設計介面上會顯示 `purchaseOrder` 項目。

6. 在每個節點上按兩下，或按一下每個節點右邊的雙箭頭，展開 `shipTo`、`billTo` 和 `items` 節點。

     `purchaseOrder` 項目的節點已展開，您可以查看該項目的內容模型。

7. 按一下 `purchaseOrder` 項目下的任何節點並查看階層連結列，以查看所選節點在結構描述集中的位置。

8. 按一下 XSD 工具列中的 [**顯示檔**] 按鈕，以切換檔。 您也可以以滑鼠右鍵按一下設計介面來切換文件。

9. 以滑鼠右鍵按一下 [`purchaseOrder`] 節點，然後選取 [**產生範例 XML** ] 以查看 xml 實例檔。
