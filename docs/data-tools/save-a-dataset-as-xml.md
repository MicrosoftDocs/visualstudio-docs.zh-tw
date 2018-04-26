---
title: 將資料集儲存為 XML
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
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 07c0b4b508acf90aac6e65e0a5f4a426bd2fce50
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="save-a-dataset-as-xml"></a>將資料集儲存為 XML

資料集內的 XML 資料可以存取的資料集上呼叫使用 XML 方法。 若要以 XML 格式儲存資料，您可以呼叫任何一個<xref:System.Data.DataSet.GetXml%2A>方法或<xref:System.Data.DataSet.WriteXml%2A>方法<xref:System.Data.DataSet>。

呼叫<xref:System.Data.DataSet.GetXml%2A>方法會傳回字串，包含所有資料的格式為 XML 的資料集內的資料表中的資料。

呼叫<xref:System.Data.DataSet.WriteXml%2A>方法會以 XML 格式的資料傳送給您指定的檔案。

## <a name="to-save-the-data-in-a-dataset-as-xml-to-a-variable"></a>若要將資料集中的資料儲存為 XML，變數

- <xref:System.Data.DataSet.GetXml%2A>方法會傳回<xref:System.String>。 宣告類型的變數<xref:System.String>並將其指派的結果<xref:System.Data.DataSet.GetXml%2A>方法。

     [!code-vb[VbRaddataSaving#12](../data-tools/codesnippet/VisualBasic/save-a-dataset-as-xml_1.vb)]
     [!code-csharp[VbRaddataSaving#12](../data-tools/codesnippet/CSharp/save-a-dataset-as-xml_1.cs)]

## <a name="to-save-the-data-in-a-dataset-as-xml-to-a-file"></a>若要將資料集中的資料為 XML 儲存至檔案

- <xref:System.Data.DataSet.WriteXml%2A>方法有數個多載。 宣告變數，並將它指派有效的路徑儲存至檔案。 下列程式碼會示範如何將資料儲存至檔案：

     [!code-vb[VbRaddataSaving#13](../data-tools/codesnippet/VisualBasic/save-a-dataset-as-xml_2.vb)]
     [!code-csharp[VbRaddataSaving#13](../data-tools/codesnippet/CSharp/save-a-dataset-as-xml_2.cs)]

## <a name="see-also"></a>另請參閱

- [將資料儲存回資料庫](../data-tools/save-data-back-to-the-database.md)