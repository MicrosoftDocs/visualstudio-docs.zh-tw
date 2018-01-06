---
title: "擴充功能的 TableAdapter |Microsoft 文件"
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
- data [Visual Studio], TableAdapters
- data [Visual Studio], extending TableAdapters
- TableAdapters, adding functionality
ms.assetid: 418249c8-c7f3-47ef-a94c-744cb6fe6aaf
caps.latest.revision: "11"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: a8c7bb5c33597d18242da188f54ea7bfa87e380a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="extend-the-functionality-of-a-tableadapter"></a>擴充 TableAdapter 的功能
您可以擴充 TableAdapter 的功能，將程式碼加入至 TableAdapter 的部分類別檔案。  
  
 定義 TableAdapter 的程式碼會重新產生任何變更的 TableAdapter 時**Dataset 設計工具**，或當精靈修改 TableAdapter 的組態。 若要防止在 TableAdapter 的重新產生期間正在刪除您的程式碼，將程式碼加入至 TableAdapter 的部分類別檔案。  
  
 部分類別可讓分割為多個實體檔案的特定類別的程式碼。 如需詳細資訊，請參閱[部分](/dotnet/visual-basic/language-reference/modifiers/partial)或[partial （類型）](/dotnet/csharp/language-reference/keywords/partial-type)。  
  
## <a name="locate-tableadapters-in-code"></a>在程式碼中找出 Tableadapter  
 雖然 Tableadapter 專搭配**Dataset 設計工具**，所產生的 TableAdapter 類別不是巢狀的類別的<xref:System.Data.DataSet>。 Tableadapter 都位於 TableAdapter 的相關聯的資料集的名稱為基礎的命名空間。 例如，如果您的應用程式包含名為資料集`HRDataSet`，Tableadapter 將位於`HRDataSetTableAdapters`命名空間。 (命名慣例遵循下列模式： *DatasetName* + `TableAdapters`)。  
  
 下列範例假設名為 TableAdapter`CustomersTableAdapter`位於與專案中`NorthwindDataSet`。  
  
#### <a name="to-create-a-partial-class-for-a-tableadapter"></a>若要建立部分類別的 TableAdapter  
  
1.  專案中加入新的類別，請前往**專案**功能表，然後選取**加入類別**。  
  
2.  將類別命名為 `CustomersTableAdapterExtended` 。  
  
3.  選取**新增**。  
  
4.  程式碼取代為您的專案的部分類別名稱與正確的命名空間，如下所示：  
  
     [!code-csharp[VbRaddataTableAdapters#2](../data-tools/codesnippet/CSharp/extend-the-functionality-of-a-tableadapter_1.cs)]
     [!code-vb[VbRaddataTableAdapters#2](../data-tools/codesnippet/VisualBasic/extend-the-functionality-of-a-tableadapter_1.vb)]  
  
## <a name="see-also"></a>請參閱  
 [使用 TableAdapter 填入資料集](../data-tools/fill-datasets-by-using-tableadapters.md)