---
title: 專案解決方案
description: 瞭解如何使用 VSTO 增益集來自動化專案、擴充專案功能，或自訂專案使用者介面 (UI) 。
ms.custom: SEO-VS-2020
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- projects [Office development in Visual Studio], Project
- Office solutions [Office development in Visual Studio], Project
- Project [Office development in Visual Studio]
- templates [Office development in Visual Studio], Project
- Office projects [Office development in Visual Studio], Project
- solutions [Office development in Visual Studio], Project
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c44e1208daaef11cb7fd9bd22e3e3ae574ca610d
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2020
ms.locfileid: "97527508"
---
# <a name="project-solutions"></a>專案解決方案
  [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] 提供的專案範本可用來建立 Microsoft Office Project 的 VSTO 增益集。 您可以使用 VSTO 增益集來自動化 Project、擴充 Project 功能，或自訂 Project 的使用者介面 (UI)。

 如需 VSTO 增益集的詳細資訊，請參閱 [開始程式設計 Vsto 增益集](../vsto/getting-started-programming-vsto-add-ins.md) 和 [vsto 增益集的架構](../vsto/architecture-of-vsto-add-ins.md)。如果您不熟悉如何使用 Microsoft Office 進行程式設計，請參閱 [Visual Studio&#41;的 &#40;Office 程式開發入門 ](../vsto/getting-started-office-development-in-visual-studio.md)。

 [!INCLUDE[appliesto_projallapp](../vsto/includes/appliesto-projallapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="automate-project-by-using-the-project-object-model"></a>使用 project 物件模型自動化專案
 Project 物件模型公開許多可用於自動化 Project 的類別。 這些類別可讓您撰寫程式碼以完成一般工作，例如以程式設計方式建立和修改專案中的工作。

 若要從 VSTO 增益集存取專案物件模型，請使用 `Application` `ThisAddIn` 專案中類別的欄位。 `Application`欄位 `Microsoft.Office.Interop.MsProject.Application` 會傳回物件，表示目前的專案實例。 如需詳細資訊，請參閱 [程式 VSTO 增益集](../vsto/programming-vsto-add-ins.md)。

 呼叫 Project 物件模型時，您使用的類型是由 Project 的主要 Interop 組件所提供。 主要 Interop 組件的作用，如同 VSTO 增益集中 Managed 程式碼與專案中 COM 物件模型之間的橋樑。 Project 主要 Interop 組件中的所有類型都定義在 `Microsoft.Office.Interop.MSProject` 命名空間中。 如需主要 interop 元件的詳細資訊，請參閱 [office 方案開發總覽 &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md) 和 [office 主要 interop 元件](../vsto/office-primary-interop-assemblies.md)。

## <a name="use-the-project-object-model-documentation"></a>使用 project 物件模型檔
 如需 Project 物件模型的完整資訊，您可以參考 Project VBA 物件模型參考。 VBA 物件模型參考記載公開給 Visual Basic for Applications (VBA) 程式碼時的專案物件模型。 如需詳細資訊，請參閱 [專案物件模型參考](/office/vba/api/project.object)。

 VBA 物件模型參考中的所有物件和成員都會對應至 Project 主要 Interop 組件 (PIA) 中的類型和成員。 例如，VBA 物件模型參考中的行事曆物件會對應至 `Microsoft.Office.Interop.MSProject.Calendar` 專案 PIA 中的類型。 雖然 VBA 物件模型參考提供大部分屬性、方法和事件的程式碼範例，但如果您想要在使用 Visual Studio 所建立的 Project VSTO 增益集專案中使用這些程式碼範例，則必須將這個參考中的 VBA 程式碼轉譯成 Visual Basic 或 Visual c #。

> [!NOTE]
> 目前沒有 Project 主要 Interop 組件的參考文件。

### <a name="infrastructure-types-in-the-project-primary-interop-assembly"></a>專案主要 interop 元件中的基礎結構類型
 在您撰寫使用 Project PIA 的程式碼時，可能會注意到未在 VBA 參考中描述的許多類型。 這些額外類型會協助將 Project 的 COM 架構物件模型轉譯成 Managed 程式碼，不適合直接在程式碼中使用。

 如需詳細資訊，請參閱 [Office 主要 interop 元件中的類別和介面總覽](/previous-versions/office/office-12/ms247299(v=office.12))。

## <a name="customize-the-user-interface-of-project"></a>自訂專案的使用者介面
 您可以使用下列方式自訂 Project UI。

|工作|取得詳細資訊|
|----------|--------------------------|
|在 Project 的功能區中加入自訂索引標籤。|[功能區總覽](../vsto/ribbon-overview.md)|

 如需自訂專案和其他 Microsoft Office 應用程式之 UI 的詳細資訊，請參閱 [OFFICE UI 自訂](../vsto/office-ui-customization.md)。

## <a name="see-also"></a>另請參閱
- [逐步解說：建立 project 的第一個 VSTO 增益集](../vsto/walkthrough-creating-your-first-vsto-add-in-for-project.md)
- [VSTO 增益集程式設計入門](../vsto/getting-started-programming-vsto-add-ins.md)
- [Office 方案開發總覽 &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [VSTO 增益集的架構](../vsto/architecture-of-vsto-add-ins.md)
- [如何：在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [程式 VSTO 增益集](../vsto/programming-vsto-add-ins.md)
- [在 Office 方案中撰寫程式碼](../vsto/writing-code-in-office-solutions.md)
- [Office 主要 interop 元件](../vsto/office-primary-interop-assemblies.md)
- [Office UI 自訂](../vsto/office-ui-customization.md)
- [Office 開發中的專案2010和 Project Server 2010](/previous-versions/office/developer/office-2010/ee758031(v=office.14))
