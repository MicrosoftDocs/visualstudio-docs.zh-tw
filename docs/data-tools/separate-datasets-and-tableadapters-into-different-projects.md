---
title: 將資料集和 TableAdapter 分成不同的專案
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- TableAdapters, n-tier applications
- n-tier applications, separating Datasets and TableAdapters
ms.assetid: f66a3940-6227-46af-a930-9177f425f4fd
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 9198378c5acf492216e2bebaceb210073766ea23
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72648191"
---
# <a name="separate-datasets-and-tableadapters-into-different-projects"></a>將資料集和 TableAdapter 分成不同的專案
具類型的資料集已經過增強，因此可以在不同的專案中產生[tableadapter](create-and-configure-tableadapters.md)和 dataset 類別。 這可讓您快速分隔應用層，並產生多層式資料應用程式。

下列程式描述如何使用**DataSet 設計工具**，將資料集程式碼產生到與包含所產生之 TableAdapter 程式碼的專案不同的專案中。

## <a name="separate-datasets-and-tableadapters"></a>個別的資料集和 Tableadapter
當您從 TableAdapter 程式碼分隔資料集程式碼時，包含資料集程式碼的專案必須位於目前的方案中。 如果這個專案不在目前的方案中，它就不會出現在 [**屬性**] 視窗的 [**資料集專案**] 清單中。

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

#### <a name="to-separate-the-dataset-into-a-different-project"></a>將資料集分隔成不同的專案

1. 開啟包含資料集（ *.xsd*檔案）的方案。

    > [!NOTE]
    > 如果方案不包含您要將資料集程式碼分隔的專案，請建立專案，或將現有的專案加入至方案。

2. 在**方案總管**中按兩下具類型的資料集檔案（ *.xsd*檔案），以在**DataSet 設計工具**中開啟資料集。

3. 選取**DataSet 設計工具**的空白區域。

4. 在 [**屬性**] 視窗中，找出 [**資料集專案**] 節點。

5. 在 [**資料集專案**] 清單中，選取您要在其中產生資料集程式碼的專案名稱。

     在您選取要產生資料集程式碼的專案之後，[**資料集**檔案] 屬性會填入預設檔案名。 如有必要，您可以變更此名稱。 此外，如果您想要將資料集程式碼產生到特定的目錄，您可以將 [**專案資料夾**] 屬性設定為資料夾的名稱。

    > [!NOTE]
    > 當您分隔資料集與 Tableadapter 時（藉由設定 [**資料集專案**] 屬性），不會自動移動專案中的現有部分資料集類別。 現有的部分資料集類別必須手動移至 dataset 專案。

6. 儲存資料集。

     資料集會在**資料集專案**屬性的選取專案中產生，而**TableAdapter**程式碼則會產生到目前的專案中。

根據預設，當您分隔資料集和 TableAdapter 程式碼之後，結果會是每個專案中的個別類別檔案。 原始專案具有名為*DatasetName*的檔案，也就是包含 TableAdapter 程式碼的*DatasetName.Designer.cs*。 在**資料集專案**屬性中指定的專案具有名為*DatasetName*的檔案，其中包含資料集程式碼。

> [!NOTE]
> 若要查看產生的類別檔案，請選取資料集或 TableAdapter 專案。 然後，在**方案總管**中，選取 [**顯示所有**檔案]。

## <a name="see-also"></a>請參閱

- [多層式架構 (N-Tier) 資料應用程式概觀](../data-tools/n-tier-data-applications-overview.md)
- [逐步解說：建立多層式架構 (N-Tier) 資料應用程式](../data-tools/walkthrough-creating-an-n-tier-data-application.md)
- [階層式更新](../data-tools/hierarchical-update.md)
- [存取 Visual Studio 中的資料](../data-tools/accessing-data-in-visual-studio.md)
- [ADO.NET](/dotnet/framework/data/adonet/index)