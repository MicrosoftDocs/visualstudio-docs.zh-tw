---
title: 擴充 TableAdapter 的功能 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data [Visual Studio], TableAdapters
- data [Visual Studio], extending TableAdapters
- TableAdapters, adding functionality
ms.assetid: 418249c8-c7f3-47ef-a94c-744cb6fe6aaf
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 19367f812a87d6aa585e123100f1d08144c57ff9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672364"
---
# <a name="extend-the-functionality-of-a-tableadapter"></a>擴充 TableAdapter 的功能
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以藉由將程式碼加入至 TableAdapter 的部分類別檔案，來擴充 TableAdapter 的功能。

 當 **DataSet 設計工具**中的 TableAdapter 進行任何變更，或當 Wizard 修改 tableadapter 的設定時，會重新產生定義 tableadapter 的程式碼。 為了避免在重新產生 TableAdapter 期間刪除您的程式碼，請將程式碼加入至 TableAdapter 的部分類別檔案。

 部分類別可讓特定類別的程式碼在多個實體檔案之間分割。 如需詳細資訊，請參閱 [部分](https://msdn.microsoft.com/library/7adaef80-f435-46e1-970a-269fff63b448) 或 [部分 (類型) ](https://msdn.microsoft.com/library/27320743-a22e-4c7b-b0b3-53afe3607334)。

## <a name="locate-tableadapters-in-code"></a>在程式碼中找出 Tableadapter
 雖然 Tableadapter 是使用 **DataSet 設計工具**所設計，但產生的 TableAdapter 類別不是的嵌套類別 <xref:System.Data.DataSet> 。 Tableadapter 會根據 TableAdapter 相關聯資料集的名稱，位於命名空間中。 例如，如果您的應用程式包含名為的資料集 `HRDataSet` ，tableadapter 就會位於 `HRDataSetTableAdapters` 命名空間中。  (命名慣例會遵循此模式： *DatasetName*  +  `TableAdapters`) 。

 下列範例假設名為的 TableAdapter `CustomersTableAdapter` 在具有的專案中 `NorthwindDataSet` 。

#### <a name="to-create-a-partial-class-for-a-tableadapter"></a>若要建立 TableAdapter 的部分類別

1. 前往 [ **專案** ] 功能表，然後選取 [**加入類別**]，將新類別加入至您的專案。

2. 將類別命名為 `CustomersTableAdapterExtended`。

3. 選取 [新增]  。

4. 將程式碼取代為您專案的正確命名空間和部分類別名稱，如下所示：

     [!code-csharp[VbRaddataTableAdapters#2](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataTableAdapters/CS/CustomersTableAdapterExtended.cs#2)]
     [!code-vb[VbRaddataTableAdapters#2](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataTableAdapters/VB/CustomersTableAdapterExtended.vb#2)]

## <a name="see-also"></a>另請參閱
 [使用 TableAdapter 填入資料集](../data-tools/fill-datasets-by-using-tableadapters.md)
