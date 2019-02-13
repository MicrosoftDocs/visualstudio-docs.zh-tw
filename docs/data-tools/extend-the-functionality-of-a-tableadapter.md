---
title: 擴充 TableAdapter 的功能
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Visual Studio], TableAdapters
- data [Visual Studio], extending TableAdapters
- TableAdapters, adding functionality
ms.assetid: 418249c8-c7f3-47ef-a94c-744cb6fe6aaf
author: gewarren
ms.author: gewarren
manager: jillfra
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: 989eb815a6e55b5ecaed0b960963eb036b73065a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54970535"
---
# <a name="extend-the-functionality-of-a-tableadapter"></a>擴充 TableAdapter 的功能

您可以擴充 TableAdapter 的功能，將程式碼加入至 TableAdapter 的部分類別檔案。

定義 TableAdapter 的程式碼在 TableAdapter 中對任何變更時重新產生**Dataset 設計工具**，或當精靈修改 TableAdapter 的組態。 若要避免您的程式碼在 TableAdapter 的重新產生期間遭到刪除，請在 TableAdapter 的部分類別檔案中加入程式碼。

部分類別可讓多個實體檔案分割為特定類別的程式碼。 如需詳細資訊，請參閱 <<c0> [ 部分](/dotnet/visual-basic/language-reference/modifiers/partial)或是[partial （類型）](/dotnet/csharp/language-reference/keywords/partial-type)。

## <a name="locate-tableadapters-in-code"></a>在程式碼中找出 Tableadapter

雖然 TableAdapters 的設計是以**Dataset 設計工具**，產生的 TableAdapter 類別不是巢狀的類別的<xref:System.Data.DataSet>。 Tableadapter 都位於與 TableAdapter 相關聯的資料集的名稱為基礎的命名空間。 例如，如果您的應用程式包含名為資料集`HRDataSet`，將位於 TableAdapters`HRDataSetTableAdapters`命名空間。 (命名慣例會遵循這個模式：DataSetName

下列範例假設名為 TableAdapter`CustomersTableAdapter`位於與專案`NorthwindDataSet`。

### <a name="to-create-a-partial-class-for-a-tableadapter"></a>若要建立 TableAdapter 部分類別

1.  將新類別加入專案，方法是前往**專案**功能表，然後選取**加入類別**。

2.  將類別命名為 `CustomersTableAdapterExtended` 。

3.  選取 [新增]。

4.  程式碼取代為您的專案的部分類別名稱與正確的命名空間，如下所示：

     [!code-csharp[VbRaddataTableAdapters#2](../data-tools/codesnippet/CSharp/extend-the-functionality-of-a-tableadapter_1.cs)]
     [!code-vb[VbRaddataTableAdapters#2](../data-tools/codesnippet/VisualBasic/extend-the-functionality-of-a-tableadapter_1.vb)]

## <a name="see-also"></a>另請參閱

- [使用 TableAdapter 填入資料集](../data-tools/fill-datasets-by-using-tableadapters.md)