---
title: 擴充 TableAdapter 的功能
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
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 245ea6791fde96c1ff08d43d138c522f43749c6b
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/23/2020
ms.locfileid: "85282419"
---
# <a name="extend-the-functionality-of-a-tableadapter"></a>擴充 TableAdapter 的功能

您可以藉由將程式碼加入至 TableAdapter 的部分類別檔案來擴充 TableAdapter 的功能。

定義 TableAdapter 的程式碼會在對**DataSet 設計工具**中的 TableAdapter 進行任何變更時，或是當 Wizard 修改 tableadapter 的設定時重新產生。 若要避免在重新產生 TableAdapter 期間刪除您的程式碼，請將程式碼加入至 TableAdapter 的部分類別檔案。

部分類別可讓特定類別的程式碼分割成多個實體檔案。 如需詳細資訊，請參閱[partial](/dotnet/visual-basic/language-reference/modifiers/partial)或[partial （類型）](/dotnet/csharp/language-reference/keywords/partial-type)。

## <a name="locate-tableadapters-in-code"></a>在程式碼中找出 Tableadapter

雖然 Tableadapter 是使用**DataSet 設計工具**所設計，但所產生的 TableAdapter 類別不是的嵌套類別 <xref:System.Data.DataSet> 。 Tableadapter 位於命名空間中，並以 TableAdapter 相關聯資料集的名稱為基礎。 例如，如果您的應用程式包含名為的資料集 `HRDataSet` ，則 tableadapter 會位於 `HRDataSetTableAdapters` 命名空間中。 （命名慣例會遵循此模式： *DatasetName*  +  `TableAdapters` ）。

下列範例假設名為的 TableAdapter 位於 `CustomersTableAdapter` 具有的專案中 `NorthwindDataSet` 。

### <a name="to-create-a-partial-class-for-a-tableadapter"></a>建立 TableAdapter 的部分類別

1. 前往 [**專案**] 功能表，然後選取 [新增**類別**]，將新的類別新增至您的專案。

2. 將類別命名為 `CustomersTableAdapterExtended`。

3. 選取 [新增]****。

4. 將程式碼取代為您專案的正確命名空間和部分類別名稱，如下所示：

     [!code-csharp[VbRaddataTableAdapters#2](../data-tools/codesnippet/CSharp/extend-the-functionality-of-a-tableadapter_1.cs)]
     [!code-vb[VbRaddataTableAdapters#2](../data-tools/codesnippet/VisualBasic/extend-the-functionality-of-a-tableadapter_1.vb)]

## <a name="see-also"></a>另請參閱

- [使用 TableAdapter 填入資料集](../data-tools/fill-datasets-by-using-tableadapters.md)
