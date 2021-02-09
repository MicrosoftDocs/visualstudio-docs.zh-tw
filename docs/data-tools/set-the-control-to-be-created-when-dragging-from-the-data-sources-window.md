---
title: 設定拖曳時要建立的控制項
description: 探索如何設定當您從 [資料來源] 視窗拖曳至 WPF 設計工具或 Visual Studio 的 Windows Forms 設計工具時，所要建立的控制項。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Data Sources Window, select controls
- Windows Forms, displaying data
- data [Visual Studio], displaying on Windows Forms
- data [Visual Studio], Data Sources window
ms.assetid: 20597ff8-0c98-43ec-8fb1-05376804ba48
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 6b4d1782a82a1eb2147d540b1799f5152c4f2308
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99858432"
---
# <a name="set-the-control-to-be-created-when-dragging-from-the-data-sources-window"></a>設定從 [資料來源] 視窗拖曳時要建立的控制項

您可以從 [ **資料來源** ] 視窗將專案拖曳至 WPF 設計工具或 Windows Forms 設計工具，以建立資料繫結控制項。 [ **資料來源** ] 視窗中的每個專案都具有當您將它拖曳至設計工具時所建立的預設控制項。 不過，您可以選擇建立不同的控制項。

## <a name="set-the-controls-to-be-created-for-data-tables-or-objects"></a>設定要為數據表或物件建立的控制項

從 [ **資料來源** ] 視窗拖曳代表資料表或物件的專案之前，您可以選擇在一個控制項中顯示所有資料，或是在個別控制項中顯示每個資料行或屬性。

在此內容中，「 *物件* 」一詞指的是自訂商務物件、實體資料模型) 中的實體 (，或是服務所傳回的物件。

### <a name="to-set-the-controls-to-be-created-for-data-tables-or-objects"></a>若要設定要為數據表或物件建立的控制項

1. 請確定 **WPF** 設計工具或 **Windows Forms** 設計工具已開啟。

2. 在 [ **資料來源** ] 視窗中，選取代表您要設定之資料表或物件的專案。

   > [!TIP]
   > 如果 [**資料來源**] 視窗未開啟，您可以選取 [**查看**  >  **其他 Windows**  >  **資料來源**] 將它開啟。

3. 按一下專案的下拉式功能表，然後按一下功能表中的下列其中一個專案：

    - 若要在個別控制項中顯示每個資料欄位，請按一下 [ **詳細** 資料]。 當您將資料項目拖曳至設計工具時，此動作會為父資料表或物件的每個資料行或屬性建立不同的資料繫結控制項，以及每個控制項的標籤。

    - 若要在單一控制項中顯示所有資料，請在清單中選取不同的控制項，例如 WPF 應用程式中的 **DataGrid** 或 **list** ，或 Windows Forms 應用程式中的 **DataGridView** 。

    可用的控制項清單取決於您已開啟的設計工具、專案的目標 .NET 版本，以及您是否已將支援資料系結的自訂控制項加入至 **工具箱**。 如果您想要建立的控制項不在可用控制項的清單中，您可以將控制項加入清單中。 如需詳細資訊，請參閱 [將自訂控制項加入至 [資料來源] 視窗](../data-tools/add-custom-controls-to-the-data-sources-window.md)。

    若要瞭解如何建立可加入至 [ **資料來源** ] 視窗中之資料表或物件之控制項清單的自訂 Windows Forms 控制項，請參閱 [建立支援複雜資料系結的 Windows Forms 使用者控制項](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md)。

## <a name="set-the-controls-to-be-created-for-data-columns-or-properties"></a>設定要為數據行或屬性建立的控制項

將表示資料行或物件屬性的專案從 [ **資料來源** ] 視窗拖曳至設計工具之前，您可以設定要建立的控制項。

### <a name="to-set-the-controls-to-be-created-for-columns-or-properties"></a>設定要為數據行或屬性建立的控制項

1. 請確定 **WPF** 設計工具或 **Windows Forms** 設計工具已開啟。

2. 在 [ **資料來源** ] 視窗中，展開所要的資料表或物件以顯示其資料行或屬性。

3. 選取您要設定要建立之控制項的每個資料行或屬性。

4. 按一下資料行或屬性的下拉式功能表，然後選取您要在將專案拖曳至設計工具時建立的控制項。

     可用的控制項清單取決於您已開啟的設計工具、專案的目標 .NET 版本，以及支援您已新增至 [ **工具箱**] 之資料系結的自訂控制項。 如果您想要建立的控制項位於可用控制項的清單中，您可以將控制項加入清單中。 如需詳細資訊，請參閱 [將自訂控制項加入至 [資料來源] 視窗](../data-tools/add-custom-controls-to-the-data-sources-window.md)。

     若要瞭解如何建立自訂控制項，以便加入至 [ **資料來源** ] 視窗中資料行或屬性的控制項清單，請參閱 [建立支援簡單資料系結的 Windows Forms 使用者控制項](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md)。

     如果您不想要建立資料行或屬性的控制項，請在下拉式功能表中選取 [ **無** ]。 如果您想要將父資料表或物件拖曳至設計工具，但是不想要包含特定的資料行或屬性，這會很有用。

## <a name="see-also"></a>另請參閱

- [將控制項繫結至 Visual Studio 中的資料](../data-tools/bind-controls-to-data-in-visual-studio.md)
