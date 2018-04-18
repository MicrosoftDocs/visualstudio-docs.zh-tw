---
title: 將資料集儲存為 XML |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XML [Visual Basic], datasets
- data [Visual Studio], saving as XML
- datasets [Visual Basic], saving as XML
- saving data
ms.assetid: 68b8327c-ae05-49ff-b9ba-99183e70b52c
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: b9d91e964ddade89c8bce8f0519517995b7d75a0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="save-a-dataset-as-xml"></a>將資料集儲存為 XML
資料集內的 XML 資料可以存取的資料集上呼叫使用 XML 方法。 若要以 XML 格式儲存資料，您可以呼叫任何一個<xref:System.Data.DataSet.GetXml%2A>方法或<xref:System.Data.DataSet.WriteXml%2A>方法<xref:System.Data.DataSet>。  
  
 呼叫<xref:System.Data.DataSet.GetXml%2A>方法會傳回字串，包含所有資料的格式為 XML 的資料集內的資料表中的資料。  
  
 呼叫<xref:System.Data.DataSet.WriteXml%2A>方法會以 XML 格式的資料傳送給您指定的檔案。  
  
### <a name="to-save-the-data-in-a-dataset-as-xml-to-a-variable"></a>若要將資料集中的資料儲存為 XML，變數  
  
-   <xref:System.Data.DataSet.GetXml%2A>方法會傳回<xref:System.String>。這表示您宣告型別的變數<xref:System.String>並將其指派的結果<xref:System.Data.DataSet.GetXml%2A>方法。  
  
     [!code-vb[VbRaddataSaving#12](../data-tools/codesnippet/VisualBasic/save-a-dataset-as-xml_1.vb)]
     [!code-csharp[VbRaddataSaving#12](../data-tools/codesnippet/CSharp/save-a-dataset-as-xml_1.cs)]  
  
### <a name="to-save-the-data-in-a-dataset-as-xml-to-a-file"></a>若要將資料集中的資料為 XML 儲存至檔案  
  
-   <xref:System.Data.DataSet.WriteXml%2A>方法有數個多載。 下列程式碼會示範如何將資料儲存至檔案。宣告變數，並將它指派有效的路徑儲存至檔案。  
  
     [!code-vb[VbRaddataSaving#13](../data-tools/codesnippet/VisualBasic/save-a-dataset-as-xml_2.vb)]
     [!code-csharp[VbRaddataSaving#13](../data-tools/codesnippet/CSharp/save-a-dataset-as-xml_2.cs)]  
  
## <a name="see-also"></a>另請參閱  
 [將資料儲存回資料庫](../data-tools/save-data-back-to-the-database.md)