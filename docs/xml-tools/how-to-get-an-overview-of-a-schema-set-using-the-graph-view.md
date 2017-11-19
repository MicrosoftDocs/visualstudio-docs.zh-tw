---
title: "如何： 使用圖表檢視的結構描述集概觀 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c0df4b0d-52ef-4a6c-9676-1d8311aad7c7
caps.latest.revision: "3"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 88f2f9f565afef2cc3f8d3f6e9e9397fe5ce6955
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-get-an-overview-of-a-schema-set-using-the-graph-view"></a>HOW TO：使用圖表檢視取得結構描述集的概觀
本主題描述如何使用[圖表檢視](../xml-tools/graph-view.md)查看結構描述以及節點之間的關聯性中之節點的高階檢視。  
  
### <a name="to-create-a-new-xsd-file-and-display-the-root-element-in-the-content-model-view"></a>建立新的 XSD 檔案，並且在內容模型檢視中顯示根項目  
  
1.  建立新的 XML 結構描述檔案，並將檔案另存為 Relationships.xsd。  
  
2.  按一下**使用 XML 編輯器檢視與編輯基礎 XML 結構描述檔案**開始檢視上的連結。  
  
3.  XML 結構描述範例程式碼複製[範例 XML 結構描述： 關聯性](../xml-tools/sample-xsd-file-relationships.md)並貼上取代依預設加入至新 XSD 檔案的程式碼。  
  
4.  以滑鼠右鍵按一下 XML 編輯器中，選取**檢視表設計工具**。  
  
5.  從 XSD 工具列中選取圖表檢視。  
  
6.  選取**結構描述集**XML 結構描述總管和將該節點拖曳至 [圖形] 檢視的設計介面中的節點。 您會看見所有的全域節點，以及連接具有關聯性之節點的箭號。  
  
     ![圖形檢視](../xml-tools/media/relationshipingraphview.gif "RelationshipInGraphView")  
  
7.  按一下設計介面上的任何節點並查看階層連結列，以查看所選節點在結構描述集中的位置。  
  
8.  在設計介面，然後選取任何項目節點上滑鼠右鍵按一下**產生範例 XML**查看 XML 執行個體文件。