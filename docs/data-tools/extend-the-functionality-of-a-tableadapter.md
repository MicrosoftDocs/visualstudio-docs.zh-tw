---
title: 擴充 TableAdapter 的功能
description: 瞭解如何將程式碼加入至 TableAdapter 的部分類別檔案，以擴充 TableAdapter 的功能。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Visual Studio], TableAdapters
- data [Visual Studio], extending TableAdapters
- TableAdapters, adding functionality
ms.assetid: 418249c8-c7f3-47ef-a94c-744cb6fe6aaf
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: f8cea8ec761bf50ddc0f928112975c366f62418b
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2021
ms.locfileid: "106215834"
---
# <a name="extend-the-functionality-of-a-tableadapter"></a>擴充 TableAdapter 的功能

您可以藉由將程式碼加入至 TableAdapter 的部分類別檔案，來擴充 TableAdapter 的功能。

當 **DataSet 設計工具** 中的 TableAdapter 進行任何變更，或當 Wizard 修改 tableadapter 的設定時，會重新產生定義 tableadapter 的程式碼。 為了避免在重新產生 TableAdapter 期間刪除您的程式碼，請將程式碼加入至 TableAdapter 的部分類別檔案。

部分類別可讓特定類別的程式碼在多個實體檔案之間分割。 如需詳細資訊，請參閱 [部分](/dotnet/visual-basic/language-reference/modifiers/partial) 或 [部分 (類型) ](/dotnet/csharp/language-reference/keywords/partial-type)。

## <a name="locate-tableadapters-in-code"></a>在程式碼中找出 Tableadapter

雖然 Tableadapter 是使用 **DataSet 設計工具** 所設計，但產生的 TableAdapter 類別不是的嵌套類別 <xref:System.Data.DataSet> 。 Tableadapter 會根據 TableAdapter 相關聯資料集的名稱，位於命名空間中。 例如，如果您的應用程式包含名為的資料集 `HRDataSet` ，tableadapter 就會位於 `HRDataSetTableAdapters` 命名空間中。  (命名慣例會遵循此模式： *DatasetName*  +  `TableAdapters`) 。

下列範例假設名為的 TableAdapter `CustomersTableAdapter` 在具有的專案中 `NorthwindDataSet` 。

### <a name="to-create-a-partial-class-for-a-tableadapter"></a>若要建立 TableAdapter 的部分類別

1. 前往 [ **專案** ] 功能表，然後選取 [ **加入類別**]，將新類別加入至您的專案。

2. 將類別命名為 `CustomersTableAdapterExtended`。

3. 選取 [新增]。

4. 將程式碼取代為您專案的正確命名空間和部分類別名稱，如下所示：

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataTableAdapters/CS/CustomersTableAdapterExtended.cs" id="Snippet2":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataTableAdapters/VB/CustomersTableAdapterExtended.vb" id="Snippet2":::

## <a name="see-also"></a>另請參閱

- [使用 TableAdapter 填入資料集](../data-tools/fill-datasets-by-using-tableadapters.md)
