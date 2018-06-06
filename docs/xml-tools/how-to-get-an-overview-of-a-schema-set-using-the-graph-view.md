---
title: 如何： 取得設計工具的 XML 結構描述中使用圖表檢視的結構描述集概觀
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: c0df4b0d-52ef-4a6c-9676-1d8311aad7c7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 05f690d76d61ffd52abbc7b73cf162d7f6609708
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2018
ms.locfileid: "34751893"
---
# <a name="how-to-get-an-overview-of-a-schema-set-using-the-graph-view"></a>如何： 取得設定使用圖表檢視的結構描述的概觀

本主題描述如何使用[圖表檢視](../xml-tools/graph-view.md)查看結構描述以及節點之間的關聯性中之節點的高階檢視。

## <a name="to-create-a-new-xsd-file-and-display-the-root-element-in-the-content-model-view"></a>建立新的 XSD 檔案，並且在內容模型檢視中顯示根項目

1.  建立新的 XML 結構描述檔案，並將檔案儲存為*Relationships.xsd*。

2.  按一下**使用 XML 編輯器檢視與編輯基礎 XML 結構描述檔案**開始檢視上的連結。

3.  XML 結構描述範例程式碼複製[範例 XML 結構描述： 關聯性](../xml-tools/sample-xsd-file-relationships.md)並貼上取代依預設加入至新 XSD 檔案的程式碼。

4.  以滑鼠右鍵按一下 XML 編輯器中，選取**檢視表設計工具**。

5.  選取 [圖形] 檢視，從**XSD 工具列**。

6.  選取**結構描述集**節點**XML 結構描述總管**並拖曳至 [圖形] 檢視的設計介面的節點。 您會看見所有的全域節點，以及連接具有關聯性之節點的箭號。

     ![圖形檢視](../xml-tools/media/relationshipingraphview.gif)

7.  按一下設計介面上的任何節點並查看階層連結列，以查看所選節點在結構描述集中的位置。

8.  在設計介面，然後選取任何項目節點上滑鼠右鍵按一下**產生範例 XML**查看 XML 執行個體文件。