---
title: HOW TO：取得設計工具的 XML 結構描述中使用圖表檢視的結構描述集概觀
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c0df4b0d-52ef-4a6c-9676-1d8311aad7c7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9e6530f5f2856953041039171b2604236706bfd3
ms.sourcegitcommit: 3ca33862c1cfc3ccb83de3e95f1e69e860ab143a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57525135"
---
# <a name="how-to-get-an-overview-of-a-schema-set-using-the-graph-view"></a>HOW TO：取得使用 [圖形] 檢視設定的結構描述的概觀

本主題描述如何使用[圖表檢視](../xml-tools/graph-view.md)若要查看的節點在結構描述集合和節點之間的關聯性的高階檢視。

## <a name="to-create-a-new-xsd-file-and-display-the-root-element-in-the-content-model-view"></a>建立新的 XSD 檔案，並且在內容模型檢視中顯示根項目

1.  建立新的 XML 結構描述檔案，並將檔案儲存為*Relationships.xsd*。

2.  按一下 **使用 XML 編輯器檢視與編輯基礎 XML 結構描述檔案**開始檢視上的連結。

3.  XML 結構描述範例程式碼複製[範例 XML 結構描述： 關聯性](../xml-tools/sample-xsd-file-relationships.md)並貼上取代預設新增至新 XSD 檔案的程式碼。

4.  以滑鼠右鍵按一下 XML 編輯器中的任何位置，然後選取**檢視表設計工具**。

5.  選取 [圖形] 檢視，從**XSD 工具列**。

6.  選取 **結構描述集**中的節點**XML 結構描述總管**將節點拖曳至圖表檢視的設計介面。 您會看見所有的全域節點，以及連接具有關聯性之節點的箭號。

     ![圖形檢視](../xml-tools/media/relationshipingraphview.gif)

7.  按一下設計介面上的任何節點並查看階層連結列，以查看所選節點在結構描述集中的位置。

8.  在設計介面，然後選取任何項目節點的滑鼠右鍵按一下**產生範例 XML**查看 XML 執行個體文件。