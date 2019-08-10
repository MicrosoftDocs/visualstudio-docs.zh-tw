---
title: PowerPoint 方案
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office solutions [Office development in Visual Studio], PowerPoint
- templates [Office development in Visual Studio], PowerPoint
- solutions [Office development in Visual Studio], PowerPoint
- projects [Office development in Visual Studio], PowerPoint
- PowerPoint [Office development in Visual Studio]
- Office projects [Office development in Visual Studio], PowerPoint
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 9d2c85a4af986c62d3e3f3c3a3f4333baa2975ee
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2019
ms.locfileid: "68926422"
---
# <a name="powerpoint-solutions"></a>PowerPoint 方案
  Visual Studio 提供您可用來建立 Microsoft Office PowerPoint VSTO 增益集的專案範本。 您可以使用 VSTO 增益集來自動化 PowerPoint、擴充 PowerPoint 功能，或自訂 PowerPoint 使用者介面 (UI)。

 如需 VSTO 增益集的詳細資訊, 請參閱 vsto 增益集程式[設計入門](../vsto/getting-started-programming-vsto-add-ins.md)和[vsto 增益集的架構](../vsto/architecture-of-vsto-add-ins.md)。如果您是使用 Microsoft Office 進行程式設計的新手, 請參閱[Visual Studio &#40; &#41;中的 Office 程式開發入門](../vsto/getting-started-office-development-in-visual-studio.md)。

 [!INCLUDE[appliesto_pptallapp](../vsto/includes/appliesto-pptallapp-md.md)]

> [!NOTE]
> 想要開發可跨[多個平臺](https://dev.office.com/add-in-availability)擴充 Office 經驗的解決方案嗎？ 請參閱新的[Office 增益集模型](https://dev.office.com/docs/add-ins/overview/office-add-ins)。 相較于 VSTO 增益集和解決方案, Office 增益集的使用量很小, 而且您可以使用幾乎任何 web 程式設計技術 (例如 HTML5、JavaScript、CSS3 和 XML) 來建立它們。

 ![影片連結](../vsto/media/playvideo.gif "影片連結")如需相關的影片示範, [請參閱如何?:建立適用于 Microsoft PowerPoint 的增益集？](http://go.microsoft.com/fwlink/?LinkId=132767).

## <a name="automate-powerpoint-by-using-the-powerpoint-object-model"></a>使用 PowerPoint 物件模型自動化 PowerPoint
 PowerPoint 物件模型會公開您可用來自動化 PowerPoint 的許多類型。 這些類型可讓您撰寫程式碼來完成一般工作：

- 以程式設計方式建立和格式化簡報。

- 新增或移除簡報中的投影片。

- 新增或變更投影片上的圖案。

  若要從 VSTO 增益集存取 PowerPoint 物件模型, 請使用`Application`專案中`ThisAddIn`類別的欄位。 欄位會傳回代表目前 PowerPoint 實例的[應用程式](/previous-versions/office/developer/office-2010/ff764034(v=office.14))物件。 `Application` 如需詳細資訊, 請參閱[VSTO 增益集程式](../vsto/programming-vsto-add-ins.md)設計。

  呼叫 PowerPoint 物件模型時，您使用的類型是由 PowerPoint 的主要 Interop 組件所提供。 主要 Interop 組件的作用，如同 VSTO 增益集中 Managed 程式碼與 PowerPoint 中 COM 物件模型之間的橋樑。 PowerPoint 主要 interop 元件中的所有類型都定義于[Microsoft.](/previous-versions/office/developer/office-2010/ff763170(v=office.14)) 如需主要 interop 元件的詳細資訊, 請參閱[Office 方案&#40;開發&#41;總覽 VSTO](../vsto/office-solutions-development-overview-vsto.md)和[Office 主要 interop 元件](../vsto/office-primary-interop-assemblies.md)。

## <a name="WordOMDocumentation"></a>使用 PowerPoint 物件模型檔
 如需 PowerPoint 物件模型的完整資訊，您可以參閱 PowerPoint 主要 Interop 組件 (PIA) 參考和 VBA 物件模型參考。

### <a name="primary-interop-assembly-reference"></a>主要 interop 元件參考
 PowerPoint PIA 參考文件說明 PowerPoint 主要 Interop 組件中的類型。 本檔可從下列位置取得:[PowerPoint 2010 主要 interop 元件參考](http://go.microsoft.com/fwlink/?LinkId=189588)。

 如需 PowerPoint PIA 設計的詳細資訊, 例如 PIA 中類別和介面的差異以及 PIA 中的事件的執行方式, 請參閱[Office 主要 interop 元件中的類別和介面總覽](http://go.microsoft.com/fwlink/?LinkId=199885)。

### <a name="vba-object-model-reference"></a>VBA 物件模型參考
 VBA 物件模型參考記載公開給 Visual Basic for Applications (VBA) 程式碼時的 PowerPoint 物件模型。 如需詳細資訊, 請參閱[PowerPoint 2010 物件模型參考](http://go.microsoft.com/fwlink/?LinkId=199770)。

 VBA 物件模型參考中的所有物件和成員都會對應至 PowerPoint 主要 Interop 組件 (PIA) 中的類型和成員。 例如, VBA 物件模型參考中的呈現物件會對應至 PowerPoint PIA 中的[呈現](/previous-versions/office/developer/office-2010/ff761925(v=office.14))類型。 雖然 VBA 物件模型參考提供大部分屬性、方法和事件的程式碼範例，但如果您想要在以 Visual Studio 建立的 PowerPoint VSTO 增益集專案中使用這些程式碼範例，則必須將這個參考中的 VBA 程式碼轉譯為 Visual Basic 或 Visual C#。

## <a name="customize-the-user-interface-of-powerpoint"></a>自訂 PowerPoint 的使用者介面
 您可以使用下列方式來修改 PowerPoint 的 UI。

|工作|如需詳細資訊|
|----------|--------------------------|
|建立自訂工作窗格。|[自訂工作窗格](../vsto/custom-task-panes.md)|
|在功能區中新增自訂索引標籤。|[功能區總覽](../vsto/ribbon-overview.md)|
|將自訂群組新增至功能區上的內建索引標籤。|[如何：自訂內建索引標籤](../vsto/how-to-customize-a-built-in-tab.md)|

 如需自訂 PowerPoint 和其他 Microsoft Office 應用程式之 UI 的詳細資訊, 請參閱[OFFICE UI 自訂](../vsto/office-ui-customization.md)。

## <a name="see-also"></a>另請參閱
- [逐步解說：建立 PowerPoint 的第一個 VSTO 增益集](../vsto/walkthrough-creating-your-first-vsto-add-in-for-powerpoint.md)
- [VSTO 增益集程式設計入門](../vsto/getting-started-programming-vsto-add-ins.md)
- [Office 方案開發總覽&#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [VSTO 增益集的架構](../vsto/architecture-of-vsto-add-ins.md)
- [如何：在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [程式 VSTO 增益集](../vsto/programming-vsto-add-ins.md)
- [在 Office 方案中撰寫程式碼](../vsto/writing-code-in-office-solutions.md)
- [Office 主要 interop 元件](../vsto/office-primary-interop-assemblies.md)
- [Office UI 自訂](../vsto/office-ui-customization.md)
- [Office 開發中的 PowerPoint 2010](http://go.microsoft.com/fwlink/?LinkId=199015)
