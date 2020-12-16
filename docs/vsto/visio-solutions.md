---
title: Visio 方案
description: 瞭解如何使用 VSTO 增益集來自動化 Visio、擴充 Visio 功能，或自訂 Visio 使用者介面 (UI) 。
ms.custom: SEO-VS-2020
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office projects [Office development in Visual Studio], Visio
- solutions [Office development in Visual Studio], Visio
- Visio [Office development in Visual Studio]
- templates [Office development in Visual Studio], Visio
- projects [Office development in Visual Studio], Visio
- Office solutions [Office development in Visual Studio], Visio
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: d5b4cbdfe6cceff279ae20518edf83b4f4ec8912
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2020
ms.locfileid: "97526379"
---
# <a name="visio-solutions"></a>Visio 方案
  Visual Studio 提供的專案範本可用來建立 Microsoft Office Visio 的 VSTO 增益集。 您可以使用 VSTO 增益集來自動化 Visio、擴充 Visio 功能，或自訂 Visio 的使用者介面 (UI)。

 如需 VSTO 增益集的詳細資訊，請參閱 [開始程式設計 Vsto 增益集](../vsto/getting-started-programming-vsto-add-ins.md) 和 [vsto 增益集的架構](../vsto/architecture-of-vsto-add-ins.md)。如果您不熟悉如何使用 Microsoft Office 進行程式設計，請參閱 [Visual Studio&#41;的 &#40;Office 程式開發入門 ](../vsto/getting-started-office-development-in-visual-studio.md)。

 **適用對象：** 本主題資訊適用於 Visio 2010 的 VSTO 增益集專案。 如需詳細資訊，請參閱 [Features Available by Office Application and Project Type](../vsto/features-available-by-office-application-and-project-type.md)。

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="automate-visio-by-using-the-visio-object-model"></a>使用 Visio 物件模型將 Visio 自動化
 Visio 物件模型公開許多可用於自動化 Visio 的類別，來建立組織圖、流程圖、專案時間軸、網路圖表、辦公室等多種圖表。 應用程式開發介面可讓您撰寫程式碼以完成一般工作：

- 在圖表中建構並放置圖形和文字。

- 根據商務邏輯和使用者輸入管理圖形行為。

- 控制圖表的視覺效果，例如移動瀏覽和縮放。

- 自訂應用程式 UI。

- 將外部資料匯入 Visio、連結至圖形，並以圖形方式顯示於頁面上。

  您可以觀看逐步程式和程式碼範例，以使用 visio 的物件模型來處理 [與 visio 檔搭配](../vsto/working-with-visio-documents.md) 使用的檔和圖形，以及使用 [visio 圖形](../vsto/working-with-visio-shapes.md)。

  若要存取 VSTO 增益集中的 Visio 物件模型，請使用專案中 `Application` 類別的 `ThisAddIn` 欄位。 `Application` 欄位傳回的 `Microsoft.Office.Interop.Visio.Application` 物件，代表 Visio 目前的執行個體。 如需詳細資訊，請參閱 [程式 VSTO 增益集](../vsto/programming-vsto-add-ins.md)。

  呼叫 Visio 物件模型時，您使用的類型是由 Visio 的主要 Interop 組件 (PIA) 所提供。 PIA 的作用，如同 VSTO 增益集中 Managed 程式碼與 Visio 中 COM 物件模型之間的橋樑。 Visio PIA 的所有型別都是在 `Microsoft.Office.Interop.Visio` 命名空間中定義。 如需主要 interop 元件的詳細資訊，請參閱 [office 方案開發總覽 &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md) 和 [office 主要 interop 元件](../vsto/office-primary-interop-assemblies.md)。

## <a name="visio-object-model-overview"></a>Visio 物件模型總覽
 您可以在 Visio 物件模型 [總覽](../vsto/visio-object-model-overview.md)中找到 visio 物件模型的總覽，其中包括 visio 物件模型參考和 sdk 的連結。

## <a name="customize-the-user-interface-of-visio"></a>自訂 Visio 的使用者介面
 Visio UI 有下列自訂選項。

|工作|取得詳細資訊|
|----------|--------------------------|
|自訂功能區。|[功能區概觀](../vsto/ribbon-overview.md)|

 如需 Visio 自訂 UI 的相關資訊，請參閱 VBA 參考文件的 [Visio.UIObject](/office/vba/api/Visio.UIObject) 類別。

## <a name="see-also"></a>另請參閱
- [VSTO 增益集程式設計入門](../vsto/getting-started-programming-vsto-add-ins.md)
- [Office 方案開發總覽 &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [VSTO 增益集的架構](../vsto/architecture-of-vsto-add-ins.md)
- [如何：在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [程式 VSTO 增益集](../vsto/programming-vsto-add-ins.md)
- [在 Office 方案中撰寫程式碼](../vsto/writing-code-in-office-solutions.md)
- [Office 主要 interop 元件](../vsto/office-primary-interop-assemblies.md)
- [Office UI 自訂](../vsto/office-ui-customization.md)
- [Visio 物件模型總覽](../vsto/visio-object-model-overview.md)
- [Office 開發中的 Visio 2010](/previous-versions/office/developer/office-2010/ff604964(v=office.14))
