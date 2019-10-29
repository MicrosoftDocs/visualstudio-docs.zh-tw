---
title: InfoPath 方案
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- solutions [Office development in Visual Studio], InfoPath
- templates [Office development in Visual Studio], InfoPath
- InfoPath [Office development in Visual Studio]
- Office development in Visual Studio, InfoPath solutions
- projects [Office development in Visual Studio], InfoPath
- Office solutions [Office development in Visual Studio], InfoPath
- Office projects [Office development in Visual Studio], InfoPath
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 7eda46c04cdbe5ba73e32e124486cfc391e5ac17
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985736"
---
# <a name="infopath-solutions"></a>InfoPath 方案
  Visual Studio 提供的專案範本，可用來建立 Microsoft Office InfoPath 2013 與 InfoPath 2010 的 VSTO 增益集。 Office 2016 不提供 InfoPath。

> [!NOTE]
> 即使您已安裝 Office 2016，仍然可以建立 InfoPath 的 VSTO 增益集。 只安裝與 Office 2016 並行的 InfoPath 2013 或 Office 2013。

 [!INCLUDE[appliesto_infoallapp](../vsto/includes/appliesto-infoallapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

 InfoPath 的 VSTO 增益集類似於其他 Microsoft Office 應用程式的 VSTO 增益集。 這類方案是由應用程式載入的組件所組成。 無論開啟何種表單或表單範本，使用者都可以存取此組件的功能。 如需 VSTO 增益集的詳細資訊，請參閱 vsto 增益集程式[設計入門](../vsto/getting-started-programming-vsto-add-ins.md)和[vsto 增益集的架構](../vsto/architecture-of-vsto-add-ins.md)。

> [!NOTE]
> Visual Studio 2015 不包含舊版 Visual Studio 曾提供的 InfoPath 表單範本專案。 在舊版 Visual Studio 中建立的 InfoPath 表單範本專案，也無法使用 Visual Studio 2015 開啟或編輯。 不過，您可以使用 Visual Studio Tools for Applications 開啟和編輯 InfoPath 表單範本專案。 如需詳細資訊，請參閱[在 InfoPath 2010 中使用 VSTO 2008 專案](https://blogs.msdn.microsoft.com/infopath/2011/04/14/working-with-vsto-2008-projects-in-infopath-2010/)。

## <a name="automate-infopath-by-using-an-add-in"></a>使用增益集自動化 InfoPath
 若要從在 Visual Studio 中使用 Office 開發工具建立的 Office VSTO 增益集存取 InfoPath 物件模型，請使用專案中 `Application` 類別的 `ThisAddIn` 欄位。 `Application` 欄位傳回的 <xref:Microsoft.Office.Interop.InfoPath.Application> 物件，代表 InfoPath 目前的執行個體。 如需詳細資訊，請參閱[VSTO 增益集程式](../vsto/programming-vsto-add-ins.md)設計。

 當您從 VSTO 增益集呼叫 InfoPath 物件模型時，您會使用 InfoPath 的主要 interop 元件中提供的類型。 主要 Interop 組件的作用，如同 VSTO 增益集中 Managed 程式碼與 InfoPath 中 COM 物件模型之間的橋樑。 InfoPath 主要 Interop 組件中的所有類型，都是在 <xref:Microsoft.Office.Interop.InfoPath> 命名空間中定義。 如需 InfoPath 主要 interop 元件的詳細資訊，請參閱[關於 Microsoft Office infopath 主要 interop 元件](https://msdn.microsoft.com/1b3ae03c-6951-49e4-a489-4712d3f7ba72)。 如需主要 interop 元件的一般詳細資訊，請參閱[Office 方案開發&#40;總覽&#41; VSTO](../vsto/office-solutions-development-overview-vsto.md)和[Office 主要 interop 元件](../vsto/office-primary-interop-assemblies.md)。

## <a name="customize-the-user-interface-of-infopath-by-using-an-add-in"></a>使用增益集自訂 InfoPath 的使用者介面
 當您建立 InfoPath 的 VSTO 增益集時，您會有數個不同的 UI 自訂選項。 下表列出其中一些選項。

|工作|如需詳細資訊|
|----------|--------------------------|
|建立自訂工作窗格。|[自訂工作窗格](../vsto/custom-task-panes.md)|
|在 InfoPath 的功能區中加入自訂索引標籤。|[自訂 InfoPath 的功能區](../vsto/customizing-a-ribbon-for-infopath.md)|

 如需自訂 InfoPath 和其他 Microsoft Office 應用程式之 UI 的詳細資訊，請參閱[OFFICE UI 自訂](../vsto/office-ui-customization.md)。

## <a name="see-also"></a>請參閱
- [關於 Microsoft Office InfoPath 主要 interop 元件](https://msdn.microsoft.com/1b3ae03c-6951-49e4-a489-4712d3f7ba72)
- [VSTO 增益集程式設計入門](../vsto/getting-started-programming-vsto-add-ins.md)
- [Office 方案開發總覽&#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [VSTO 增益集的架構](../vsto/architecture-of-vsto-add-ins.md)
- [如何：在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [程式 VSTO 增益集](../vsto/programming-vsto-add-ins.md)
- [在 Office 方案中撰寫程式碼](../vsto/writing-code-in-office-solutions.md)
- [Office 主要 interop 元件](../vsto/office-primary-interop-assemblies.md)
- [Office UI 自訂](../vsto/office-ui-customization.md)
- [Office 開發中的 InfoPath 2010](/previous-versions/office/developer/office-2010/ff604966(v=office.14))
