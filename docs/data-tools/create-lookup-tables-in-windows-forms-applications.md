---
title: 在 Windows Forms 應用程式中建立查閱資料表
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- lookup tables
- lookup tables, creating
ms.assetid: 0edd5385-c381-4b17-9096-74e2778db9d5
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 9a1ae368b7d2bf8548bf78a6a9795e19206bc277
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/23/2020
ms.locfileid: "85282653"
---
# <a name="create-lookup-tables-in-windows-forms-applications"></a>在 Windows Forms 應用程式中建立查閱資料表

「詞彙*查閱」資料表*描述系結至兩個相關資料表的控制項。 這些查閱控制項會根據第二個數據表中選取的值，顯示第一個資料表中的資料。

將父資料表的主要節點（從 [[資料來源] 視窗](add-new-data-sources.md#data-sources-window)）拖曳至表單上已系結至相關子資料工作表中之資料行的控制項，即可建立查閱資料表。

例如，請考慮 `Orders` sales 資料庫中的資料表。 資料表中的每筆記錄都 `Orders` 包含 `CustomerID` ，以指出訂單的客戶。 `CustomerID`是指向資料表中客戶記錄的外鍵 `Customers` 。 在此案例中，您會展開 `Orders` [**資料來源**] 視窗中的資料表，並將主要節點設定為 [**詳細**資料]。 然後，將資料 `CustomerID` 行設定為使用 <xref:System.Windows.Forms.ComboBox> （或任何其他支援查閱系結的控制項），並將 `Orders` 節點拖曳至表單上。 最後，將節點拖曳至系結 `Customers` 至相關資料行的控制項（在此案例中，系結 <xref:System.Windows.Forms.ComboBox> 至資料 `CustomerID` 行）。

## <a name="to-databind-a-lookup-control"></a>若要將查閱控制項進行 databind

1. 當您的專案開啟時，選擇 [**視圖**] [其他視窗] [ **Data Sources**  >  **Other Windows**  >  **資料來源**] 以開啟 [資料來源] 視窗。

    > [!NOTE]
    > 在 [**資料來源**] 視窗中，查閱資料表需要有兩個相關的資料表或物件。 如需詳細資訊，請參閱[dataset 中的關聯](relationships-in-datasets.md)性。

2. 展開 [**資料來源**] 視窗中的節點，直到您可以看到父資料表及其所有資料行，以及相關的子資料工作表及其所有資料行為止。

    > [!NOTE]
    > 子資料工作表節點是在父資料表中顯示為可擴充子節點的節點。

3. 從子資料工作表節點的控制項清單中選取 [**詳細資料**]，將子資料工作表的卸載類型變更為 [**詳細資料**]。 如需詳細資訊，請參閱[設定從資料來源視窗拖曳時要建立的控制項](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)。

4. 找出與兩個數據表相關聯的節點（ `CustomerID` 上一個範例中的節點）。 <xref:System.Windows.Forms.ComboBox>從控制項清單中選取 [ **ComboBox** ]，將其卸載類型變更為。

5. 將 [主要子資料工作表] 節點從 [**資料來源**] 視窗拖曳至表單上。

     資料系結控制項（具有描述性標籤）和工具區域（ <xref:System.Windows.Forms.BindingNavigator> ）會出現在表單上。 [資料集](../data-tools/dataset-tools-in-visual-studio.md)、 [TableAdapter](../data-tools/create-and-configure-tableadapters.md)、 <xref:System.Windows.Forms.BindingSource> 和 <xref:System.Windows.Forms.BindingNavigator> 會出現在元件匣中。

6. 現在，將 [主要父資料表] 節點從 [**資料來源**] 視窗直接拖曳至查閱控制項（ <xref:System.Windows.Forms.ComboBox> ）。

     現在已建立查閱系結。 請參閱下表，以瞭解在控制項上設定的特定屬性。

    |屬性|設定說明|
    |--------------| - |
    |**源**|Visual Studio 會將此屬性設定為針對您拖曳至控制項之資料表所建立的 <xref:System.Windows.Forms.BindingSource> (與建立控制項時所建立的 <xref:System.Windows.Forms.BindingSource> 相反)。<br /><br /> 如果您需要進行調整，請將此設定為 <xref:System.Windows.Forms.BindingSource> 包含您要顯示之資料行之資料表的。|
    |**DisplayMember**|Visual Studio 會將此屬性設定為主索引鍵後面具有字串資料類型的第一個資料行 (針對您拖曳至控制項的資料表)。<br /><br /> 如果您需要進行調整，請將此設定為您想要顯示的資料行名稱。|
    |**ValueMember**|Visual Studio 會將此屬性設定為參與主索引鍵的第一個資料行，或者，如果未定義索引鍵，則為資料表中的第一個資料行。<br /><br /> 如果您需要進行調整，請將此設定為數據表中具有您想要顯示之資料行的主要索引鍵。|
    |**SelectedValue**|Visual Studio 將此屬性設定為從 [**資料來源**] 視窗中卸載的原始資料行。<br /><br /> 如果您需要進行調整，請將此設定為相關資料表中的外鍵資料行。|

## <a name="see-also"></a>另請參閱

- [將 Windows Forms 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
