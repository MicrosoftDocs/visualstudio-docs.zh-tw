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
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 5b3aa23cb0fde98b4da4225b8e255b7cd6e7aef5
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72641347"
---
# <a name="save-a-dataset-as-xml"></a>將資料集儲存為 XML

藉由呼叫資料集上可用的 XML 方法，存取資料集中的 XML 資料。 若要以 XML 格式儲存資料，您可以呼叫 <xref:System.Data.DataSet.GetXml%2A> 方法或 <xref:System.Data.DataSet> 的 <xref:System.Data.DataSet.WriteXml%2A> 方法。

呼叫 <xref:System.Data.DataSet.GetXml%2A> 方法會傳回字串，其中包含格式為 XML 之資料集中所有資料表的資料。

呼叫 <xref:System.Data.DataSet.WriteXml%2A> 方法會將 XML 格式的資料傳送至您指定的檔案。

## <a name="to-save-the-data-in-a-dataset-as-xml-to-a-variable"></a>將 dataset 中的資料以 XML 形式儲存至變數

- <xref:System.Data.DataSet.GetXml%2A> 方法會傳回 <xref:System.String>。 宣告 <xref:System.String> 類型的變數，並為其指派 <xref:System.Data.DataSet.GetXml%2A> 方法的結果。

     [!code-vb[VbRaddataSaving#12](../data-tools/codesnippet/VisualBasic/save-a-dataset-as-xml_1.vb)]
     [!code-csharp[VbRaddataSaving#12](../data-tools/codesnippet/CSharp/save-a-dataset-as-xml_1.cs)]

## <a name="to-save-the-data-in-a-dataset-as-xml-to-a-file"></a>將 dataset 中的資料儲存為 XML 檔案

- @No__t_0 方法有數個多載。 宣告變數，並為其指派可儲存檔案的有效路徑。 下列程式碼顯示如何將資料儲存至檔案：

     [!code-vb[VbRaddataSaving#13](../data-tools/codesnippet/VisualBasic/save-a-dataset-as-xml_2.vb)]
     [!code-csharp[VbRaddataSaving#13](../data-tools/codesnippet/CSharp/save-a-dataset-as-xml_2.cs)]

## <a name="see-also"></a>請參閱

- [將資料儲存回資料庫](../data-tools/save-data-back-to-the-database.md)