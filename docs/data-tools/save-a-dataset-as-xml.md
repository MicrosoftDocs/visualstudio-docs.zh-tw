---
title: 將資料集儲存為 XML
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XML [Visual Basic], datasets
- data [Visual Studio], saving as XML
- datasets [Visual Basic], saving as XML
- saving data
ms.assetid: 68b8327c-ae05-49ff-b9ba-99183e70b52c
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: cc8854581903ab58a327ff18be7b3b7c0f860a3b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85281730"
---
# <a name="save-a-dataset-as-xml"></a>將資料集儲存為 XML

藉由呼叫資料集上可用的 XML 方法，存取資料集中的 XML 資料。 若要以 XML 格式儲存資料，您可以呼叫 <xref:System.Data.DataSet.GetXml%2A> 方法或的 <xref:System.Data.DataSet.WriteXml%2A> 方法 <xref:System.Data.DataSet> 。

呼叫 <xref:System.Data.DataSet.GetXml%2A> 方法會傳回字串，其中包含格式化為 XML 之資料集中所有資料表的資料。

呼叫 <xref:System.Data.DataSet.WriteXml%2A> 方法會將 XML 格式的資料傳送至您指定的檔案。

## <a name="to-save-the-data-in-a-dataset-as-xml-to-a-variable"></a>將資料集內的資料儲存為變數的 XML

- <xref:System.Data.DataSet.GetXml%2A> 方法會傳回 <xref:System.String>。 宣告類型的變數 <xref:System.String> ，並為它指派方法的結果 <xref:System.Data.DataSet.GetXml%2A> 。

     [!code-vb[VbRaddataSaving#12](../data-tools/codesnippet/VisualBasic/save-a-dataset-as-xml_1.vb)]
     [!code-csharp[VbRaddataSaving#12](../data-tools/codesnippet/CSharp/save-a-dataset-as-xml_1.cs)]

## <a name="to-save-the-data-in-a-dataset-as-xml-to-a-file"></a>將資料集中的資料儲存為檔案的 XML

- <xref:System.Data.DataSet.WriteXml%2A>方法有數個多載。 宣告變數，並為它指派儲存檔案的有效路徑。 下列程式碼顯示如何將資料儲存至檔案：

     [!code-vb[VbRaddataSaving#13](../data-tools/codesnippet/VisualBasic/save-a-dataset-as-xml_2.vb)]
     [!code-csharp[VbRaddataSaving#13](../data-tools/codesnippet/CSharp/save-a-dataset-as-xml_2.cs)]

## <a name="see-also"></a>另請參閱

- [將資料儲存回資料庫](../data-tools/save-data-back-to-the-database.md)
