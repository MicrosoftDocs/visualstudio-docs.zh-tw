---
title: 將自訂控制項加入 [資料來源] 視窗
description: 將自訂控制項加入至 Visual Studio 中的 [資料來源] 視窗。 自訂可系結的控制項清單。 加入相關聯的控制項。
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.datasource.howtoaddcustomcontrol
helpviewer_keywords:
- Data Sources Window, adding controls
- controls [Visual Studio], adding to Data Sources Window
- DefaultBindingPropertyAttribute class, using
- LookupBindingPropertiesAttribute class, using
- ComplexBindingPropertiesAttribute class, using
- Data Sources Window, selecting controls
ms.assetid: 8c43e7d2-ba94-4d9b-96de-3aa971955afd
author: ghogen
ms.author: ghogen
manager: jmartens
ms.openlocfilehash: 5591dc9c3422918fa8f9c605105ea10c8fbc447d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99867421"
---
# <a name="add-custom-controls-to-the-data-sources-window"></a>將自訂控制項加入 [資料來源] 視窗

當您從 [資料來源] 視窗將專案拖曳至設計介面以建立資料繫結控制項時，您可以選取您所建立的控制項類型。 視窗中的每個專案都有一個下拉式清單，顯示您可以選擇的控制項。 與每個專案相關聯的控制項集合是由專案的資料類型所決定。 如果您想要建立的控制項未出現在清單中，您可以依照本主題中的指示，將控制項新增至清單。

如需有關在 [資料來源] 視窗中選取要為專案建立之資料繫結控制項的詳細資訊，請參閱 [設定從資料來源視窗拖曳時要建立的控制項](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)。

## <a name="customize-the-bindable-controls-list"></a>自訂可系結控制項清單

若要從具有特定資料類型的 [資料來源] 視窗中專案的可用控制項清單中，加入或移除控制項，請執行下列步驟。

### <a name="to-select-the-controls-to-be-listed-for-a-data-type"></a>若要選取要針對資料類型列出的控制項

1. 確定已開啟 [WPF 設計工具] 或 [Windows Form 設計工具]。

2. 在 [ **資料來源** ] 視窗中，按一下您加入至視窗之資料來源中的專案，然後按一下該專案的下拉式功能表。

   > [!TIP]
   > 如果 [資料來源] 視窗未開啟，請選取 [ **View**  >  **Other Windows**  >  **資料來源**] 將它開啟。

3. 在下拉式功能表中，按一下 [ **自訂**]。 下列其中一個對話方塊隨即開啟：

    - 如果 **Windows Form 設計工具** 已開啟，[**選項**] 對話方塊的 [**資料 UI 自訂**] 頁面隨即開啟。 如需詳細資訊，請參閱 [資料 UI 自訂選項對話方塊](../ide/reference/options-windows-forms-designer-data-ui-customization.md)。

    - 如果 **WPF 設計** 工具已開啟，則會開啟 [ **自訂控制項** 系結] 對話方塊。

4. 在對話方塊中，從 [ **資料類型** ] 下拉式清單中選取資料類型。

    - 若要自訂資料表或物件的控制項清單，請選取 **[清單]**。

    - 若要自訂資料表或物件屬性之資料行的控制項清單，請在基礎資料存放區中選取資料行或屬性的資料類型。

    - 若要自訂控制項清單以顯示具有使用者定義圖形的資料物件，請選取 **[其他]**。 例如，如果您的應用程式具有自訂控制項，以顯示來自特定物件之多個屬性的資料，請選取 **[其他]** 。

5. 在 [ **關聯的控制項** ] 方塊中，選取您要提供給所選取資料類型的每個控制項，或清除您想要從清單中移除之任何控制項的選項。

    > [!NOTE]
    > 如果您想要選取的控制項未出現在 [關聯的 **控制項** ] 方塊中，則必須將控制項加入至清單。 如需詳細資訊，請參閱 [加入關聯的控制項](#add-associated-controls)。

6. 按一下 [確定]  。

7. 在 [ **資料來源** ] 視窗中，按一下您剛剛與一或多個控制項相關聯之資料類型的專案，然後按一下專案的下拉式功能表。

     您在 [ **關聯的控制項** ] 方塊中選取的控制項現在會出現在專案的下拉式功能表中。

## <a name="add-associated-controls"></a>加入關聯的控制項

如果您想要將控制項與資料類型產生關聯，但控制項未出現在 [關聯的 **控制項** ] 方塊中，您必須將控制項加入至清單。 控制項必須位於目前的方案或參考的元件中。 您也必須在 [ **工具箱** ] 中使用它，並具有指定控制項資料系結行為的屬性。

若要將控制項加入相關聯的控制項清單中：

1. 以滑鼠右鍵按一下 [**工具箱**]，然後選取 **[選擇專案**]，將所需的控制項新增至 **工具箱**。

     控制項必須具有下列其中一個屬性：

    |屬性|描述|
    |---------------|-----------------|
    |<xref:System.ComponentModel.DefaultBindingPropertyAttribute>|在顯示單一資料行 (或屬性) 資料的簡單控制項（例如）上，執行此屬性 <xref:System.Windows.Forms.TextBox> 。|
    |<xref:System.ComponentModel.ComplexBindingPropertiesAttribute>|在顯示 (或資料表) 資料清單的控制項（例如）上，執行此屬性 <xref:System.Windows.Forms.DataGridView> 。|
    |<xref:System.ComponentModel.LookupBindingPropertiesAttribute>|在顯示 (或資料表) 資料清單的控制項上執行這個屬性，但也需要呈現單一資料行或屬性，例如 <xref:System.Windows.Forms.ComboBox> 。|

2. 針對 Windows Forms，請在 [ **選項** ] 對話方塊中，開啟 [ **資料 UI 自訂** ] 頁面。 或者，如果是 WPF，請開啟 [ **自訂控制項** 系結] 對話方塊。 如需詳細資訊，請參閱 [自訂資料類型的可繫結控制項清單](#customize-the-bindable-controls-list)。

3. 在 [ **關聯的控制項** ] 方塊中，現在應該會顯示您剛剛新增至 **工具箱** 的控制項。

    > [!NOTE]
    > 只有位於目前方案內或參考元件內的控制項，才能加入相關聯的控制項清單中。  (控制項也必須執行上表中的其中一個資料系結屬性。 ) 將資料系結至 [資料來源] 視窗中未提供的自訂控制項，將控制項從 [ **工具箱** ] 拖曳至設計介面上，然後從 [ **資料來源** ] 視窗中拖曳要系結的專案至控制項。

## <a name="see-also"></a>另請參閱

- [將控制項繫結至 Visual Studio 中的資料](../data-tools/bind-controls-to-data-in-visual-studio.md)
- [資料 UI 自訂選項對話方塊](../ide/reference/options-windows-forms-designer-data-ui-customization.md)
