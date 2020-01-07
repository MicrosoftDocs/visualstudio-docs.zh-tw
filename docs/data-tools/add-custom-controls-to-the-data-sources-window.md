---
title: 將自訂控制項加入 [資料來源] 視窗
ms.date: 11/04/2016
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: cd4791e118d22aab1126987461547f9fa2fec317
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/01/2020
ms.locfileid: "75587104"
---
# <a name="add-custom-controls-to-the-data-sources-window"></a>將自訂控制項加入 [資料來源] 視窗

當您從 [資料來源] 視窗將專案拖曳至設計介面以建立資料繫結控制項時，可以選取您所建立的控制項類型。 視窗中的每個專案都有下拉式清單，其中顯示您可以選擇的控制項。 與每個專案相關聯的控制項集合取決於專案的資料類型。 如果您要建立的控制項沒有出現在清單中，您可以依照本主題中的指示，將控制項加入清單中。

如需選取要在 [資料來源] 視窗中為專案建立之資料繫結控制項的詳細資訊，請參閱[設定從資料來源視窗拖曳時要建立的控制項](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)。

## <a name="customize-the-bindable-controls-list"></a>自訂可系結控制項清單

若要在具有特定資料類型的 [資料來源] 視窗中，從專案的可用控制項清單中加入或移除控制項，請執行下列步驟。

### <a name="to-select-the-controls-to-be-listed-for-a-data-type"></a>若要選取要針對資料類型列出的控制項

1. 請確定 WPF 設計工具或 Windows Form 設計工具已開啟。

2. 在 [**資料來源**] 視窗中，按一下屬於您加入至視窗之資料來源中的專案，然後按一下該專案的下拉式功能表。

   > [!TIP]
   > 如果 [資料來源] 視窗未開啟，請選取 [ **View** > **其他 Windows** > **資料來源**] 來開啟它。

3. 在下拉式功能表中，按一下 [**自訂**]。 下列其中一個對話方塊隨即開啟：

    - 如果**Windows Form 設計工具**為開啟狀態，則會開啟 [**選項**] 對話方塊的 [**資料 UI 自訂**] 頁面。 如需詳細資訊，請參閱[資料 UI 自訂選項對話方塊](../ide/reference/options-windows-forms-designer-data-ui-customization.md)。

    - 如果**WPF 設計**工具已開啟，則會開啟 [**自訂控制項**系結] 對話方塊。

4. 在對話方塊中，從 [**資料類型**] 下拉式清單中選取資料類型。

    - 若要自訂資料表或物件的控制項清單，請選取 **[清單]** 。

    - 若要針對資料表的資料行或物件的屬性自訂控制項的清單，請在基礎資料存放區中選取資料行或屬性的資料類型。

    - 若要自訂控制項清單以顯示具有使用者定義圖形的資料物件，請選取 **[其他]** 。 例如，如果您的應用程式具有自訂控制項，它會顯示來自特定物件之多個屬性的資料，請選取 **[其他]** 。

5. 在 [**相關聯的控制項**] 方塊中，選取您要提供給所選取資料類型的每個控制項，或清除您想要從清單中移除之任何控制項的選取專案。

    > [!NOTE]
    > 如果您要選取的控制項並未出現在 [**關聯的控制項**] 方塊中，您就必須將控制項加入清單中。 如需詳細資訊，請參閱[新增相關聯的控制項](#add-associated-controls)。

6. 按一下 [ **確定**]。

7. 在 [**資料來源**] 視窗中，按一下您剛關聯一個或多個控制項之資料類型的專案，然後按一下該專案的下拉式功能表。

     您在 [**關聯的控制項**] 方塊中選取的控制項現在會出現在專案的下拉式功能表中。

## <a name="add-associated-controls"></a>新增相關聯的控制項

如果您想要將控制項與資料類型產生關聯，但控制項並未出現在 [關聯的**控制項**] 方塊中，您必須將控制項加入清單中。 控制項必須位於目前的方案或參考的元件中。 它也必須在 [**工具箱**] 中提供，而且具有指定控制項資料系結行為的屬性。

若要將控制項加入至相關聯的控制項清單：

1. 以滑鼠右鍵按一下 [**工具箱**]，然後選取 **[選擇專案**]，將所需的控制項加入 [**工具箱**] 中。

     控制項必須具有下列其中一個屬性：

    |屬性|描述|
    |---------------|-----------------|
    |<xref:System.ComponentModel.DefaultBindingPropertyAttribute>|在顯示資料之單一資料行（或屬性）的簡單控制項（例如 <xref:System.Windows.Forms.TextBox>）上，執行這個屬性。|
    |<xref:System.ComponentModel.ComplexBindingPropertiesAttribute>|在顯示資料之清單（或資料表）的控制項（例如 <xref:System.Windows.Forms.DataGridView>）上，執行這個屬性。|
    |<xref:System.ComponentModel.LookupBindingPropertiesAttribute>|在顯示資料之清單（或資料表）的控制項上執行這個屬性，但也需要呈現單一資料行或屬性，例如 <xref:System.Windows.Forms.ComboBox>。|

2. 針對 Windows Forms，請在 [**選項**] 對話方塊中，開啟 [**資料 UI 自訂**] 頁面。 或者，針對 WPF，開啟 [**自訂控制項**系結] 對話方塊。 如需詳細資訊，請參閱[自訂資料類型的可繫結控制項清單](#customize-the-bindable-controls-list)。

3. 在 [**相關聯的控制項**] 方塊中，您剛加入 [**工具箱**] 的控制項現在應該會出現。

    > [!NOTE]
    > 只有位於目前方案或參考元件內的控制項，才可以加入至相關聯控制項的清單。 （控制項也必須執行上表中的其中一個資料系結屬性。）若要將資料系結至 [資料來源] 視窗中無法使用的自訂控制項，請將控制項從 [**工具箱**] 拖曳至設計介面，然後將 [**資料來源**] 視窗中的專案拖曳至控制項上。

## <a name="see-also"></a>請參閱

- [將控制項繫結至 Visual Studio 中的資料](../data-tools/bind-controls-to-data-in-visual-studio.md)
- [[資料 UI 自訂選項] 對話方塊](../ide/reference/options-windows-forms-designer-data-ui-customization.md)
