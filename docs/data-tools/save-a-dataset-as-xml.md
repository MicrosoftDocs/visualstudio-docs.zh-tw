---
title: Save a dataset as XML | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XML [Visual Basic], datasets
- data [Visual Studio], saving as XML
- datasets [Visual Basic], saving as XML
- saving data
ms.assetid: 68b8327c-ae05-49ff-b9ba-99183e70b52c
caps.latest.revision: 11
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: eb5c9550fd29b0e98bf63a7240737da4f13f3249
ms.openlocfilehash: 6d8749d35693a61d34aeb3e252fd69e9c575cacb
ms.contentlocale: zh-tw
ms.lasthandoff: 08/30/2017

---
# <a name="save-a-dataset-as-xml"></a>Save a dataset as XML
The XML data in a dataset can be accessed by calling the available XML methods  on the dataset. To save the data in XML format, you can call either the <xref:System.Data.DataSet.GetXml%2A> method or the <xref:System.Data.DataSet.WriteXml%2A> method of a <xref:System.Data.DataSet>.  
  
 Calling the <xref:System.Data.DataSet.GetXml%2A> method returns a string that contains the data from all data tables in the dataset that's formatted as XML.  
  
 Calling the <xref:System.Data.DataSet.WriteXml%2A> method sends the XML-formatted data to a file that  you specify.  
  
### <a name="to-save-the-data-in-a-dataset-as-xml-to-a-variable"></a>To save the data in a dataset as XML to a variable  
  
-   The <xref:System.Data.DataSet.GetXml%2A> method returns a <xref:System.String>.This means that you declare a variable of type <xref:System.String> and assign it the results of the <xref:System.Data.DataSet.GetXml%2A> method.  
  
     [!code-vb[VbRaddataSaving#12](../data-tools/codesnippet/VisualBasic/save-a-dataset-as-xml_1.vb)]  [!code-csharp[VbRaddataSaving#12](../data-tools/codesnippet/CSharp/save-a-dataset-as-xml_1.cs)]  
  
### <a name="to-save-the-data-in-a-dataset-as-xml-to-a-file"></a>To save the data in a dataset as XML to a file  
  
-   The <xref:System.Data.DataSet.WriteXml%2A> method has several overloads. The following code shows how to save the data to a file.Declare a variable and assign it a valid path to save the file to.  
  
     [!code-vb[VbRaddataSaving#13](../data-tools/codesnippet/VisualBasic/save-a-dataset-as-xml_2.vb)]  [!code-csharp[VbRaddataSaving#13](../data-tools/codesnippet/CSharp/save-a-dataset-as-xml_2.cs)]  
  
## <a name="see-also"></a>See Also  
 [Save data back to the database](../data-tools/save-data-back-to-the-database.md)
