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
manager: jillfra
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: c1eff1b80807b040bd50d7e4e5f2045c73c46929
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "55011815"
---
# <a name="save-a-dataset-as-xml"></a>將資料集儲存為 XML

存取 XML 資料集中的資料集上呼叫可用的 XML 方法。 若要以 XML 格式儲存資料，您可以呼叫<xref:System.Data.DataSet.GetXml%2A>方法或<xref:System.Data.DataSet.WriteXml%2A>方法<xref:System.Data.DataSet>。

呼叫<xref:System.Data.DataSet.GetXml%2A>方法會傳回字串，包含所有資料表的資料會格式化為 XML 資料集裡的資料。

呼叫<xref:System.Data.DataSet.WriteXml%2A>方法會以 XML 格式的資料傳送至您指定的檔案。

## <a name="to-save-the-data-in-a-dataset-as-xml-to-a-variable"></a>若要將資料集中的資料為 XML 儲存至變數

- <xref:System.Data.DataSet.GetXml%2A> 方法會傳回 <xref:System.String>。 宣告類型的變數<xref:System.String>並將其指派的結果<xref:System.Data.DataSet.GetXml%2A>方法。

     [!code-vb[VbRaddataSaving#12](../data-tools/codesnippet/VisualBasic/save-a-dataset-as-xml_1.vb)]
     [!code-csharp[VbRaddataSaving#12](../data-tools/codesnippet/CSharp/save-a-dataset-as-xml_1.cs)]

## <a name="to-save-the-data-in-a-dataset-as-xml-to-a-file"></a>若要將資料集中的資料為 XML 儲存至檔案

- <xref:System.Data.DataSet.WriteXml%2A>方法有數個多載。 宣告變數，並將它指派有效的路徑來儲存檔案。 下列程式碼示範如何將資料儲存至檔案：

     [!code-vb[VbRaddataSaving#13](../data-tools/codesnippet/VisualBasic/save-a-dataset-as-xml_2.vb)]
     [!code-csharp[VbRaddataSaving#13](../data-tools/codesnippet/CSharp/save-a-dataset-as-xml_2.cs)]

## <a name="see-also"></a>另請參閱

- [將資料儲存回資料庫](../data-tools/save-data-back-to-the-database.md)