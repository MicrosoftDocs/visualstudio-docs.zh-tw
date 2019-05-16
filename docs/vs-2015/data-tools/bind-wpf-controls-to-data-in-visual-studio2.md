---
title: 將 WPF 控制項繫結至資料 |Microsoft Docs
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: e37d17cbe67bd1e4e64e306831f38996a7f93c80
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65697963"
---
# <a name="bind-wpf-controls-to-data-in-visual-studio"></a>將 WPF 控制項繫結至 Visual Studio 中的資料
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以建立資料繫結[!INCLUDE[TLA#tla_titlewinclient](../includes/tlasharptla-titlewinclient-md.md)]使用的控制項**Zdroje dat**視窗。 首先，新增 資料來源，以便**Zdroje dat**視窗。 然後，將項目從**資料來源** 視窗來**WPF 設計工具**。

## <a name="adding"></a> 將資料來源加入資料來源視窗
 您可以建立資料繫結控制項之前，您必須先新增資料來源，以便**Zdroje dat**視窗。

#### <a name="to-add-a-data-source-to-the-data-sources-window"></a>將資料來源加入至資料來源視窗

1. 在上**檢視**功能表上，指向**其他 Windows**，然後按一下  **Zdroje dat**。

2. 按一下 [新增資料來源]，並完成 [資料來源組態精靈]。

3. 執行下列工作之一，以建立資料繫結控制項：

    - [建立控制項繫結至資料的單一欄位](#simple)。

    - [建立控制項繫結至多個欄位的資料](#complex)。

    - [建立一組控制項繫結至多個欄位的資料](#details)。

    - [資料繫結至設計工具中的現有控制項](#existing)。

## <a name="simple"></a> 建立繫結至資料的單一欄位的控制項
 新增資料來源，以便之後**資料來源** 視窗中，您可以建立新的資料繫結控制項顯示的單一欄位的資料，例如<xref:System.Windows.Controls.ComboBox>或<xref:System.Windows.Controls.TextBox>。

#### <a name="to-create-a-control-that-is-bound-to-a-single-field-of-data"></a>建立繫結至資料的單一欄位的控制項

1. 在 [ **Zdroje dat** ] 視窗中，展開代表資料表或物件的項目。 找出代表您想要與之繫結的資料行或屬性的子項目。 如需圖解示範，請參閱 <<c0> [ 資料來源視窗](https://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992)。

2. 或者，選取要建立的控制項。 在每個項目**Zdroje dat**視窗有當您將項目拖曳至設計工具會建立一個預設控制項。 預設控制項會根據項目的基礎資料類型而有所不同。

     若要選擇不同的控制項，請按一下項目旁邊的下拉式箭頭，並選取控制項。 如需詳細資訊，請參閱 <<c0> [ 設定要從資料來源視窗拖曳時要建立的控制項](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)。

3. 將項目拖曳至設計工具中是有效的容器中。 如需有效容器的詳細資訊，請參閱[繫結 WPF 控制項新增至 Visual Studio 中的資料](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)。

     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 建立新的資料繫結控制項，以及適當標題<xref:System.Windows.Controls.Label>容器中。 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 也會產生 [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] 及程式碼，以將控制項繫結至資料。 如需詳細資訊，請參閱 <<c0> [ 繫結 WPF 控制項新增至 Visual Studio 中的資料](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)。

## <a name="complex"></a> 建立多個欄位的資料繫結的控制項
 新增資料來源，以便之後**資料來源** 視窗中，您可以建立新的資料繫結控制項，會顯示多個欄位的資料，例如<xref:System.Windows.Controls.DataGrid>或<xref:System.Windows.Controls.ListView>。

#### <a name="to-create-a-control-that-is-bound-to-multiple-fields-of-data"></a>建立繫結至資料的多個欄位的控制項

1. 在 [ **Zdroje dat** ] 視窗中，選取代表資料表或物件的項目。 如需圖解示範，請參閱 <<c0> [ 資料來源視窗](https://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992)。

2. 或者，選取要建立的控制項。 根據預設，每個項目**資料來源**代表資料表或物件的範圍設定為建立<xref:System.Windows.Controls.DataGrid>（如果您的專案目標.NET Framework 4） 或<xref:System.Windows.Controls.ListView>（適用於舊版的.NET framework 中）。

     若要選取不同的控制項，請按一下項目旁邊的下拉式箭頭，並選取控制項。 如需詳細資訊，請參閱 <<c0> [ 設定要從資料來源視窗拖曳時要建立的控制項](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)。

    > [!NOTE]
    > 若您不想要顯示特定資料行或屬性，請展開項目以顯示其子項。 按一下下拉式清單旁的箭號的資料行或屬性，您不想要顯示此項目，並按一下**無**。

3. 將項目拖曳至設計工具中的有效容器中，例如 <xref:System.Windows.Controls.Grid>。 如需有效容器的詳細資訊，請參閱[繫結 WPF 控制項新增至 Visual Studio 中的資料](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)。

     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 會在容器中建立新的資料繫結控制項。 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 也會產生 [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] 及程式碼，以將控制項繫結至資料。 如需詳細資訊，請參閱 <<c0> [ 繫結 WPF 控制項新增至 Visual Studio 中的資料](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)。

## <a name="details"></a> 建立一組控制項繫結至多個欄位的資料
 新增資料來源，以便之後**Zdroje dat**  視窗中，您可以將資料表或物件繫結至一組控制項。 會針對資料表或物件中的每個資料行或屬性建立不同的控制項。

#### <a name="to-create-a-set-of-controls-that-are-bound-to-multiple-fields-of-data"></a>建立一組繫結至資料的多個欄位的控制項

1. 在 [ **Zdroje dat** ] 視窗中，選取代表資料表或物件的項目。 如需圖解示範，請參閱 <<c0> [ 資料來源視窗](https://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992)。

2. 按一下下拉式清單旁的箭號的項目並選取**詳細資料**。

    > [!NOTE]
    > 若您不想要顯示特定資料行或屬性，請展開項目以顯示其子項。 按一下下拉式清單旁的箭號的資料行或屬性，您不想要顯示此項目，並按一下**無**。

3. 將項目拖曳至設計工具中的有效容器中，例如 <xref:System.Windows.Controls.Grid>。 如需有效容器的詳細資訊，請參閱[繫結 WPF 控制項新增至 Visual Studio 中的資料](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)。

     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 會在容器中建立新的資料繫結控制項。 每個控制項會繫結至不同的資料行或屬性，而且每個控制項都會隨附具有適當標題的 <xref:System.Windows.Controls.Label> 控制項。 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 也會產生可將控制項繫結至資料的 [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] 和程式碼。 如需詳細資訊，請參閱 <<c0> [ 繫結 WPF 控制項新增至 Visual Studio 中的資料](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)。

## <a name="existing"></a> 在設計工具中的現有控制項的 Binddata
 新增資料來源，以便之後**Zdroje dat**  視窗中，您可以加入資料繫結至現有的控制項設計工具中。

#### <a name="to-bind-data-to-an-existing-control-in-the-designer"></a>將資料繫結至設計工具中的現有控制項

1. 在  **Zdroje dat**視窗中，使用下列程序的其中一個：

    - 若要將資料繫結加入至顯示資料的多個欄位的現有控制項，例如 <xref:System.Windows.Controls.DataGrid> 或 <xref:System.Windows.Controls.ListView>，請選取代表您想要繫結至控制項之資料表或物件的項目。

    - 若要將資料繫結加入至顯示資料的單一欄位的現有控制項，例如 <xref:System.Windows.Controls.ComboBox> 或 <xref:System.Windows.Controls.TextBox>，請展開代表資料表或物件 (其中包含該資料) 的項目，然後選取代表您想要繫結至控制項之資料的項目。

2. 拖曳選取的項目，從**Zdroje dat**視窗拖曳至設計工具中的現有控制項。 控制項必須是能夠有效拖放的目標。 如需詳細資訊，請參閱 <<c0> [ 繫結 WPF 控制項新增至 Visual Studio 中的資料](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)。

     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 會產生[!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)]，以及將控制項繫結至資料的程式碼。 如需詳細資訊，請參閱 <<c0> [ 繫結 WPF 控制項新增至 Visual Studio 中的資料](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)。

    > [!NOTE]
    > 若控制項已繫結至資料，則會將控制項的資料繫結重設為已在最近拖曳至控制項的項目。

## <a name="see-also"></a>另請參閱
 [將 WPF 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md) [WPF 應用程式中建立查閱資料表](../data-tools/create-lookup-tables-in-wpf-applications.md) [WPF 應用程式中顯示相關的資料](../data-tools/display-related-data-in-wpf-applications.md)[繫結 WPF 控制項新增至資料集](../data-tools/bind-wpf-controls-to-a-dataset.md)[繫結 WPF 控制項新增至 WCF data service](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md) [逐步解說：在 WPF 應用程式中顯示相關的資料](../data-tools/walkthrough-displaying-related-data-in-a-wpf-application.md)
