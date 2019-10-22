---
title: 將 WPF 控制項系結至資料 |Microsoft Docs
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
- data [WPF], displaying
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio]
- displaying data, WPF
- WPF [WPF], data
- WPF Designer, data binding
- data binding, WPF
ms.assetid: 00dd5147-db0b-4b59-8d6c-8229b09ca9dd
caps.latest.revision: 29
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f99c9a9ecbb18155ea8cd1197b94a7b383a80a1f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662510"
---
# <a name="bind-wpf-controls-to-data-in-visual-studio"></a>將 WPF 控制項繫結至 Visual Studio 中的資料
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以使用 [**資料來源**] 視窗，建立資料系結 [!INCLUDE[TLA#tla_titlewinclient](../includes/tlasharptla-titlewinclient-md.md)] 控制項。 首先，將資料來源加入至 [**資料來源**] 視窗。 然後，將專案從 [**資料來源**] 視窗拖曳至**WPF 設計**工具。

## <a name="adding"></a>將資料來源加入至 [資料來源] 視窗
 建立資料繫結控制項之前，您必須先將資料來源加入至 [**資料來源**] 視窗。

#### <a name="to-add-a-data-source-to-the-data-sources-window"></a>將資料來源加入至資料來源視窗

1. 在 [ **View** ] 功能表上，指向 [**其他視窗**]，然後按一下 [**資料來源**]。

2. 按一下 [新增資料來源]，並完成 [資料來源組態精靈]。

3. 執行下列工作之一，以建立資料繫結控制項：

    - [建立系結至單一資料欄位的控制項](#simple)。

    - [建立系結至多個資料欄位的控制項](#complex)。

    - [建立一組系結至多個資料欄位的控制項](#details)。

    - 將資料系結[至設計工具中的現有控制項](#existing)。

## <a name="simple"></a>建立系結至單一資料欄位的控制項
 將資料來源加入至 [**資料來源**] 視窗之後，您可以建立新的資料繫結控制項，以顯示資料的單一欄位，例如 <xref:System.Windows.Controls.ComboBox> 或 <xref:System.Windows.Controls.TextBox>。

#### <a name="to-create-a-control-that-is-bound-to-a-single-field-of-data"></a>建立繫結至資料的單一欄位的控制項

1. 在 [**資料來源**] 視窗中，展開代表資料表或物件的專案。 找出代表您想要與之繫結的資料行或屬性的子項目。 如需視覺效果範例，請參閱[資料來源視窗](https://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992)。

2. 或者，選取要建立的控制項。 [**資料來源**] 視窗中的每個專案都有一個預設控制項，會在您將專案拖曳至設計工具時建立。 預設控制項會根據項目的基礎資料類型而有所不同。

     若要選擇不同的控制項，請按一下項目旁邊的下拉式箭頭，並選取控制項。 如需詳細資訊，請參閱[設定從資料來源視窗拖曳時要建立的控制項](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)。

3. 將專案拖曳至設計工具中的有效容器。 如需有效容器的詳細資訊，請參閱[將 WPF 控制項系結至 Visual Studio 中的資料](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)。

     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 會在容器中建立新的資料繫結控制項和適當標題的 <xref:System.Windows.Controls.Label>。 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 也會產生 [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] 及程式碼，以將控制項繫結至資料。 如需詳細資訊，請參閱[將 WPF 控制項系結至 Visual Studio 中的資料](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)。

## <a name="complex"></a>建立系結至資料之多個欄位的控制項
 將資料來源加入至 [**資料來源**] 視窗之後，您可以建立新的資料繫結控制項，以顯示資料的多個欄位，例如 <xref:System.Windows.Controls.DataGrid> 或 <xref:System.Windows.Controls.ListView>。

#### <a name="to-create-a-control-that-is-bound-to-multiple-fields-of-data"></a>建立繫結至資料的多個欄位的控制項

1. 在 [**資料來源**] 視窗中，選取代表資料表或物件的專案。 如需視覺效果範例，請參閱[資料來源視窗](https://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992)。

2. 或者，選取要建立的控制項。 根據預設，[**資料來源**] 視窗中表示資料表或物件的每個專案都會設定為建立 <xref:System.Windows.Controls.DataGrid> （如果專案的目標為 .NET Framework 4）或 <xref:System.Windows.Controls.ListView> （適用于舊版的 .NET Framework）。

     若要選取不同的控制項，請按一下項目旁邊的下拉式箭頭，並選取控制項。 如需詳細資訊，請參閱[設定從資料來源視窗拖曳時要建立的控制項](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)。

    > [!NOTE]
    > 若您不想要顯示特定資料行或屬性，請展開項目以顯示其子項。 按一下您不想要顯示的資料行或屬性旁的下拉式箭號，然後按一下 [**無**]。

3. 將項目拖曳至設計工具中的有效容器中，例如 <xref:System.Windows.Controls.Grid>。 如需有效容器的詳細資訊，請參閱[將 WPF 控制項系結至 Visual Studio 中的資料](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)。

     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 會在容器中建立新的資料繫結控制項。 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 也會產生 [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] 及程式碼，以將控制項繫結至資料。 如需詳細資訊，請參閱[將 WPF 控制項系結至 Visual Studio 中的資料](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)。

## <a name="details"></a>建立一組系結至資料之多個欄位的控制項
 將資料來源加入至 [**資料來源**] 視窗之後，您就可以將資料表或物件系結至一組控制項。 會針對資料表或物件中的每個資料行或屬性建立不同的控制項。

#### <a name="to-create-a-set-of-controls-that-are-bound-to-multiple-fields-of-data"></a>建立一組繫結至資料的多個欄位的控制項

1. 在 [**資料來源**] 視窗中，選取代表資料表或物件的專案。 如需視覺效果範例，請參閱[資料來源視窗](https://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992)。

2. 按一下專案旁邊的下拉箭號，然後選取 [**詳細資料**]。

    > [!NOTE]
    > 若您不想要顯示特定資料行或屬性，請展開項目以顯示其子項。 按一下您不想要顯示的資料行或屬性旁的下拉式箭號，然後按一下 [**無**]。

3. 將項目拖曳至設計工具中的有效容器中，例如 <xref:System.Windows.Controls.Grid>。 如需有效容器的詳細資訊，請參閱[將 WPF 控制項系結至 Visual Studio 中的資料](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)。

     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 會在容器中建立新的資料繫結控制項。 每個控制項會繫結至不同的資料行或屬性，而且每個控制項都會隨附具有適當標題的 <xref:System.Windows.Controls.Label> 控制項。 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 也會產生可將控制項繫結至資料的 [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] 和程式碼。 如需詳細資訊，請參閱[將 WPF 控制項系結至 Visual Studio 中的資料](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)。

## <a name="existing"></a>Binddata 至設計工具中的現有控制項
 將資料來源加入至 [**資料來源**] 視窗之後，您可以將資料系結加入至設計工具中的現有控制項。

#### <a name="to-bind-data-to-an-existing-control-in-the-designer"></a>將資料繫結至設計工具中的現有控制項

1. 在 [**資料來源**] 視窗中，使用下列其中一個程式：

    - 若要將資料繫結加入至顯示資料的多個欄位的現有控制項，例如 <xref:System.Windows.Controls.DataGrid> 或 <xref:System.Windows.Controls.ListView>，請選取代表您想要繫結至控制項之資料表或物件的項目。

    - 若要將資料繫結加入至顯示資料的單一欄位的現有控制項，例如 <xref:System.Windows.Controls.ComboBox> 或 <xref:System.Windows.Controls.TextBox>，請展開代表資料表或物件 (其中包含該資料) 的項目，然後選取代表您想要繫結至控制項之資料的項目。

2. 將選取的專案從 [**資料來源**] 視窗拖曳至設計工具中的現有控制項。 控制項必須是能夠有效拖放的目標。 如需詳細資訊，請參閱[將 WPF 控制項系結至 Visual Studio 中的資料](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)。

     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 會產生 [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] 和程式碼，以將控制項系結至資料。 如需詳細資訊，請參閱[將 WPF 控制項系結至 Visual Studio 中的資料](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)。

    > [!NOTE]
    > 若控制項已繫結至資料，則會將控制項的資料繫結重設為已在最近拖曳至控制項的項目。

## <a name="see-also"></a>請參閱
 [將 wpf 控制項系結至](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md) [wpf 應用程式中 Visual Studio 建立查閱資料表](../data-tools/create-lookup-tables-in-wpf-applications.md)中的資料在 wpf 應用程式中[顯示相關資料](../data-tools/display-related-data-in-wpf-applications.md)將 wpf 控制項系結[至資料集](../data-tools/bind-wpf-controls-to-a-dataset.md)將 wpf 控制項系結[至 WCF 資料服務](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md)[逐步解說：在 WPF 應用程式中顯示相關資料](../data-tools/walkthrough-displaying-related-data-in-a-wpf-application.md)
