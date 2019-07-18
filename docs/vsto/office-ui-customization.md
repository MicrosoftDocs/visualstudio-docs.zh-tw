---
title: Office UI 自訂
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- menus [Office development in Visual Studio], customizing
- actions panes [Office development in Visual Studio], creating
- WPF [Office development in Visual Studio]
- toolbars [Office development in Visual Studio], customizing
- Office applications [Office development in Visual Studio], UI customization
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 052149783f93c1bf2f394be2fac9f6a51c9c0cf5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62977912"
---
# <a name="office-ui-customization"></a>Office UI 自訂
  您可以使用 Visual Studio 中的 Office 程式開發人員工具，自訂 Microsoft Office 應用程式的使用者介面 (UI)。 本主題在下列各節中描述您可以自訂的 UI 功能：

- [UI 功能的比較](#Comparison)

- [執行窗格和自訂工作窗格](#Actions)

- [自訂功能區 UI](#Ribbon)

- [Backstage 檢視](#Backstage)

- [Outlook 表單區域](#FormRegion)

- [在文件上的控制項](#Controls)

- [快顯功能表](#Shortcut)

## <a name="Comparison"></a> UI 功能的比較
 下表比較在 Microsoft Office 專案中，您可以自訂的主要 UI 功能。

|功能|支援的專案類型|支援的 Microsoft Office 應用程式|
|-------------|-----------------------------|---------------------------------------------|
|執行窗格|文件層級自訂|Excel<br /><br /> 字組|
|自訂工作窗格|VSTO 增益集|Excel<br /><br /> [!INCLUDE[InfoPath_15_short](../vsto/includes/infopath-15-short-md.md)]<br /><br /> [!INCLUDE[InfoPath_14_short](../vsto/includes/infopath-14-short-md.md)]<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> 字組<br /><br /> Excel|
|自訂功能區 UI|文件層級自訂<br /><br /> VSTO 增益集|Excel<br /><br /> [!INCLUDE[InfoPath_15_short](../vsto/includes/infopath-15-short-md.md)]<br /><br /> [!INCLUDE[InfoPath_14_short](../vsto/includes/infopath-14-short-md.md)]<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> 專案<br /><br /> 字組<br /><br /> Visio|
|Backstage 檢視|文件層級自訂<br /><br /> VSTO 增益集|Excel<br /><br /> [!INCLUDE[InfoPath_15_short](../vsto/includes/infopath-15-short-md.md)].<br /><br /> [!INCLUDE[InfoPath_14_short](../vsto/includes/infopath-14-short-md.md)]<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> 專案<br /><br /> 字組<br /><br /> Visio|
|Outlook 表單區域|VSTO 增益集|Outlook|
|文件上的控制項|文件層級自訂<br /><br /> VSTO 增益集|Excel<br /><br /> 字組|
|快顯功能表|文件層級自訂<br /><br /> VSTO 增益集|Excel<br /><br /> [!INCLUDE[InfoPath_15_short](../vsto/includes/infopath-15-short-md.md)]<br /><br /> [!INCLUDE[InfoPath_14_short](../vsto/includes/infopath-14-short-md.md)]<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> 專案<br /><br /> 字組<br /><br /> Visio<br /><br /> Excel|

## <a name="Actions"></a> 執行窗格和自訂工作窗格
 工作窗格是通常停駐在 Microsoft Office 應用程式視窗一側的使用者介面面板。 幾乎所有的 Microsoft Office 應用程式都包括內建的工作窗格。 工作窗格的範例是在 Word 中的 [說明] 工作窗格。

 Visual Studio 中的 Office 開發工具提供兩種不同的方式，可自訂工作窗格：

- 您可以將執行窗格加入文件層級自訂。 根據預設，執行窗格會顯示在應用程式的右側，文件的右邊。 不過，執行窗格也可以顯示在文件的左邊、上方或底部。

- 您可以將自訂工作窗格加入 VSTO 增益集。 使用者可以將自訂工作窗格固定至應用程式視窗的不同側，也可以將自訂工作窗格拖曳到視窗中的任何位置。

  執行窗格和自訂工作窗格裝載各種控制項，協助使用者進行例如輸入資料的工作來提供功能。 相較於功能區群組，執行窗格和自訂工作窗格提供更大的空間，以包含文字和控制項。

  如需有關執行窗格的詳細資訊，請參閱 <<c0> [ 執行窗格概觀](../vsto/actions-pane-overview.md)。 如需有關自訂工作窗格的詳細資訊，請參閱 <<c0> [ 自訂工作窗格](../vsto/custom-task-panes.md)。

## <a name="Ribbon"></a> 自訂功能區 UI
 您可以自訂功能區 UI 以公開您在 Office 中加入應用程式的功能。 功能區可組織相關的命令 (以控制項的形式)，以便能輕鬆找到它們。 您可以建立自己的功能區索引標籤和群組，讓使用者存取您在方案中提供的功能。 在較舊版本的 Microsoft Office 系統中，使用功能表和工具列存取的大多數功能，現在可以使用功能區來存取。

 如需詳細資訊，請參閱 <<c0> [ 功能區概觀](../vsto/ribbon-overview.md)。

## <a name="Backstage"></a> Backstage 檢視
 在 Office 應用程式，按一下**檔案** 索引標籤開啟 Backstage 檢視。 Backstage 檢視提供 UI，它會合併檔案層級工作和動作，並取代可從  2007 Microsoft Office system 的 Microsoft Office 按鈕使用的類似功能。 Backstage 檢視完全可使用 XML 延伸。

 Visual Studio 不提供設計工具或 API 來自訂 Backstage 檢視。 不過，如果您加入**功能區 (XML)** 項目加入 Office 專案，您可以將 XML 加入功能區 XML 檔案，以自訂 Backstage 檢視。 如需詳細資訊**功能區 (XML)** 項目，請參閱[功能區 XML](../vsto/ribbon-xml.md)。

 如需自訂 Backstage 檢視的詳細資訊，請參閱 <<c0> [ 開發人員的 Office 2010 Backstage 檢視簡介](http://go.microsoft.com/fwlink/?LinkId=182189)並[來自訂開發人員的 Office 2010 Backstage 檢視](http://go.microsoft.com/fwlink/?LinkId=182188)。

## <a name="FormRegion"></a> Outlook 表單區域
 使用表單區域，將自訂功能加入標準的 Microsoft Office Outlook 表單中。 您可以建立表單區域，以額外的欄位或控制項擴充任何現有的表單。 如果您在 Visual Studio 中使用 Office 開發工具建立新的表單區域，您在表單區域上只能使用 Windows Form 控制項。 如果您匯入在 Outlook 中設計的表單區域，則只能使用原生 Outlook 控制項。

 您可以建立表單區域，佔用 Outlook UI 的不同區域。 例如，相鄰表單區域會顯示在表單中的第一頁底部，而每個相鄰的表單區域都可摺疊。 您也可以加入另一個表單區域，顯示為完整的額外表單頁面，而且可以出現在任何現有的標準表單或自訂表單上。

 如需詳細資訊，請參閱 <<c0> [ 建立 Outlook 表單區域](../vsto/creating-outlook-form-regions.md)。

## <a name="Controls"></a> 在文件上的控制項
 您可以將各種控制項加入 Word 文件和 Excel 工作表。 例如，您可能想要將日期選擇器控制項加入文件，讓使用者可以用標準格式輸入日期，或在工作表上放置一個按鈕，將資料傳送至資料庫。

 當您開發 Excel 或 Word 的文件層級專案時，您可以使用 Visual Studio 設計工具在設計階段，在您的專案中將控制項加入文件或活頁簿，或您可以在執行階段以程式設計方式加入控制項。 當您為 Excel 或 Word 開發 VSTO 增益集專案時，您可以以程式設計方式將控制項加入任何開啟的文件或活頁簿，在執行階段中。

 如需詳細資訊，請參閱 <<c0> [ 主項目和裝載控制項概觀](../vsto/host-items-and-host-controls-overview.md)並[Windows forms 上的控制項 Office 文件概觀](../vsto/windows-forms-controls-on-office-documents-overview.md)。

## <a name="Shortcut"></a> 快顯功能表
 在文件或應用程式視窗上按一下滑鼠右鍵時，會出現快顯功能表。 您可以設定快顯功能表在事件發生之後出現，例如使用者以滑鼠右鍵按一下文件、活頁簿或主控制項之後。 您可以將多個不同的功能表命令或控制項加入快顯功能表。 使用 XML 建立快顯功能表。 如果您加入**功能區 (XML)** 項目加入 Office 專案，您可以將 XML 加入功能區 XML 檔案，以建立快顯功能表。 如需使用 XML 來建立快顯功能表的詳細資訊，請參閱[How to:將命令加入至捷徑功能表](../vsto/how-to-add-commands-to-shortcut-menus.md)。

## <a name="see-also"></a>另請參閱
- [功能區概觀](../vsto/ribbon-overview.md)
- [Windows forms 上的控制項 Office 文件概觀](../vsto/windows-forms-controls-on-office-documents-overview.md)
- [執行窗格概觀](../vsto/actions-pane-overview.md)
- [建立 Outlook 表單區域](../vsto/creating-outlook-form-regions.md)
- [自訂工作窗格](../vsto/custom-task-panes.md)
- [在 Office 方案中使用 WPF 控制項](../vsto/using-wpf-controls-in-office-solutions.md)
- [如何：在功能區顯示開發人員索引標籤](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md)
- [如何：顯示增益集使用者介面錯誤](../vsto/how-to-show-add-in-user-interface-errors.md)
- [逐步解說：使用 Windows form 收集資料](../vsto/walkthrough-collecting-data-using-a-windows-form.md)
