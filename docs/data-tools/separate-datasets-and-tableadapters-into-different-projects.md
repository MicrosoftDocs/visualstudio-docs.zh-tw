---
title: 使用個別專案錯誤
description: 瞭解如何將資料集和 Tableadapter 分成不同的專案，讓您可以快速分隔應用層，並產生多層式資料應用程式。
ms.date: 11/04/2016
ms.topic: how-to
ms.custom: SEO-VS-2020
helpviewer_keywords:
- TableAdapters, n-tier applications
- n-tier applications, separating Datasets and TableAdapters
ms.assetid: f66a3940-6227-46af-a930-9177f425f4fd
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 9463fe0371ee3184fd78684e7fe0565820ab3bf0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99866537"
---
# <a name="separate-datasets-and-tableadapters-into-different-projects"></a>將資料集和 TableAdapter 分成不同的專案
已增強具類型的資料集，以便可以在個別的專案中產生 [tableadapter](create-and-configure-tableadapters.md) 和資料集類別。 這可讓您快速地分隔應用層，並產生多層式資料應用程式。

下列程式描述使用 **DataSet 設計工具** 將資料集程式碼產生至與包含所產生之 TableAdapter 程式碼的專案不同的專案。

## <a name="separate-datasets-and-tableadapters"></a>個別資料集和 Tableadapter
當您將資料集程式碼與 TableAdapter 程式碼分開時，包含資料集程式碼的專案必須位於目前的方案中。 如果這個專案不在目前的方案中，就不會出現在 [**屬性**] 視窗的 [**資料集專案**] 清單中。

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

#### <a name="to-separate-the-dataset-into-a-different-project"></a>將資料集分隔成不同的專案

1. 開啟包含資料集 (*.xsd* 檔) 的方案。

    > [!NOTE]
    > 如果解決方案未包含您要用來分隔資料集程式碼的專案，請建立專案，或將現有的專案加入至方案。

2. 按兩下具類型的資料集檔案， (**方案總管** 中) 的 *.xsd* 檔，以在 **DataSet 設計工具** 中開啟資料集。

3. 選取 **DataSet 設計工具** 的空白區域。

4. 在 [ **屬性** ] 視窗中，找出 **資料集專案** 節點。

5. 在 [ **資料集專案** ] 清單中，選取您要在其中產生資料集程式碼的專案名稱。

     當您選取要在其中產生資料集程式碼的專案之後，就會使用預設的檔案名填入 [ **資料集** 檔案] 屬性。 如有必要，您可以變更此名稱。 此外，如果您想要在特定目錄中產生資料集程式碼，您可以將 [ **專案資料夾** ] 屬性設定為資料夾的名稱。

    > [!NOTE]
    > 當您藉由設定 [ **資料集專案** ] 屬性) 來分隔資料集和 tableadapter (時，不會自動移動專案中的現有部分資料集類別。 您必須手動將現有的部分資料集類別移至資料集專案。

6. 儲存資料集。

     資料集程式碼會產生到 [ **資料集專案** ] 屬性中選取的專案，而 **TableAdapter** 程式碼則會產生到目前的專案中。

根據預設，在您分隔資料集和 TableAdapter 程式碼之後，結果會是每個專案中的個別類別檔案。 原始專案有一個名為 *DatasetName* 的檔案， (或包含 TableAdapter 程式碼的 *DatasetName.Designer.cs*) 。 在 [ **資料集專案** ] 屬性中指定的專案具有名為 *DatasetName* 的檔案， (或包含資料集程式碼的 *DatasetName.DataSet.Designer.cs*) 。

> [!NOTE]
> 若要查看產生的類別檔案，請選取資料集或 TableAdapter 專案。 然後，在 **方案總管** 中，選取 [ **顯示所有** 檔案]。

## <a name="see-also"></a>另請參閱

- [多層式資料應用程式總覽](../data-tools/n-tier-data-applications-overview.md)
- [逐步解說：建立多層式資料應用程式](../data-tools/walkthrough-creating-an-n-tier-data-application.md)
- [階層式更新](../data-tools/hierarchical-update.md)
- [存取 Visual Studio 中的資料](../data-tools/accessing-data-in-visual-studio.md)
- [ADO.NET](/dotnet/framework/data/adonet/index)
