---
title: 將資料儲存 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- DataRow.RowState
- DataSet.GetChanges
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- DBDirect methods
- updating data
- data [Visual Studio], saving
- TableAdapter DBDirect methods
- databases, updating
- TableAdapter.Update method
- data [Visual Studio], updating
- saving data
- updating databases
ms.assetid: 21d2b115-62e4-4ac9-a873-dcbb535b8af8
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: dc671d60ff37e9853dc64a62cbc1b91a6914e0e3
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49249297"
---
# <a name="saving-data"></a>儲存資料
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

將資料儲存為保存的程序變回原始的資料存放區，通常是關聯式資料庫，例如 SQL Server 的應用程式的資料模型中的資料。  
  
 透過資料模型更新資料來源，通常是兩步驟程序。 第一個步驟是使用新的資訊來更新資料模型-新的記錄變更的記錄，或已刪除的記錄。 第二個步驟是將變更儲存回資料庫的資料模型中。  
  
 下列主題說明的概念和儲存資料的相關聯的工作。  
  
## <a name="related-topics"></a>相關主題  
 [將資料儲存回資料庫](../data-tools/save-data-back-to-the-database.md)  
 概述如何在資料集進行變更，以及如何將資料集追蹤變更的相關資訊才能將這些變更儲存至資料庫。  
  
 [儲存實體資料](../data-tools/saving-entity-data.md)  
 描述如何將變更儲存在[ADO.NET Entity Framework](http://msdn.microsoft.com/library/a437041f-6899-4ae7-96ce-aabf528d7205)並[WCF Data Services 4.5](http://msdn.microsoft.com/library/73d2bec3-7c92-4110-b905-11bb0462357a)應用程式。