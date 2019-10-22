---
title: 如何：使用圖表視圖來取得架構集的總覽 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: c0df4b0d-52ef-4a6c-9676-1d8311aad7c7
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7009e5772b4f4c6977d58d2c52d733999a0d9369
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670887"
---
# <a name="how-to-get-an-overview-of-a-schema-set-using-the-graph-view"></a>HOW TO：使用圖表檢視取得結構描述集的概觀
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題描述如何使用[圖表視圖](../xml-tools/graph-view.md)來查看架構集內節點的高階視圖，以及節點之間的關聯性。

### <a name="to-create-a-new-xsd-file-and-display-the-root-element-in-the-content-model-view"></a>建立新的 XSD 檔案，並且在內容模型檢視中顯示根項目

1. 建立新的 XML 結構描述檔案，並將檔案另存為 Relationships.xsd。

2. 按一下 [使用 XML 編輯器]，即可在 [開始] 視圖上**查看和編輯基礎 XML 架構**檔案連結。

3. 複製[範例 Xml 架構：關聯](../xml-tools/sample-xsd-file-relationships.md)性中的 xml 架構範例程式碼，並貼上它，以取代預設新增至新 XSD 檔案的程式碼。

4. 以滑鼠右鍵按一下 XML 編輯器中的任何位置，然後選取 [ **View Designer**]。

5. 從 XSD 工具列中選取圖表檢視。

6. 在 XML 架構瀏覽器中選取**架構集**節點，並將節點拖曳至圖形視圖的 [設計] suface。 您會看見所有的全域節點，以及連接具有關聯性之節點的箭號。

     ![圖形檢視](../xml-tools/media/relationshipingraphview.gif "RelationshipInGraphView")

7. 按一下設計介面上的任何節點並查看階層連結列，以查看所選節點在結構描述集中的位置。

8. 在 desing 介面上，以滑鼠右鍵按一下任何專案節點，然後選取 [**產生範例 xml** ] 以查看 xml 實例檔。
