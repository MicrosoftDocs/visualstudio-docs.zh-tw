---
title: Visio 物件模型總覽
description: 瞭解如何與 Visio 物件模型互動，以開發適用于 Microsoft Visio 的 Office 方案。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visio [Office development in Visual Studio], object model
- object models [Office development in Visual Studio], Office
- object models [Office development in Visual Studio], Visio
- objects [Office development in Visual Studio], Office object models
- Office object models
- Visio object model
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 8d7a83b5a900defb63ceffe4f63d57e2b200c47b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99921778"
---
# <a name="visio-object-model-overview"></a>Visio 物件模型總覽
  若要開發 Microsoft Office Visio 的 Office 方案，您可以與 Visio 物件模型互動。 組成這個物件模型的類別和介面，是由 Visio 的主要 Interop 組件所提供，並在 `Microsoft.Office.Interop.Visio` 命名空間中定義。

 本主題提供簡短的 Visio 物件模型概觀。 如需使用 Visio 物件模型在 Office 專案中執行工作的詳細資訊，請參閱下列主題：

- [使用 Visio 檔](../vsto/working-with-visio-documents.md)

- [使用 Visio 圖形](../vsto/working-with-visio-shapes.md)

## <a name="understand-the-visio-object-model"></a>瞭解 Visio 物件模型
 Visio 會提供許多您可以與之互動的物件。 這些物件是在密切遵循使用者介面的階層內組合管理。 階層的頂端是 [Microsoft.Office.Interop.Visio.Application](/office/vba/api/Visio.Application) 物件。 這個物件代表 Visio 目前的執行個體。 `Microsoft.Office.Interop.Visio.Application`物件包含 `Microsoft.Office.Interop.Visio.Document` 和物件以及 `Microsoft.Office.Interop.Visio.Page` `Microsoft.Office.Interop.Visio.Documents` 和 `Microsoft.Office.Interop.Visio.Pages` 集合。 這些物件和集合每個都有許多方法和屬性，您可以存取操作並與之互動。

 如需詳細資訊，請參閱 [Microsoft.Office.Interop.Visio.Application](/office/vba/api/Visio.Application)、 [Microsoft.Office.Interop.Visio.Document](/office/vba/api/Visio.Document)和 [Microsoft.Office.Interop.Visio.Page](/office/vba/api/Visio.Page) 物件，以及 [Microsoft.Office.Interop.Visio.Documents](/office/vba/api/Visio.Documents) 和 [Microsoft.Office.Interop.Visio.Pages](/office/vba/api/Visio.Pages) 集合的 VBA 參考文件。

 下列各節簡述最上層物件，以及它們彼此之間的互動方式。 這些物件包含下列物件：

- 應用程式物件

- Document 物件

- Page 物件

### <a name="application-object"></a>應用程式物件
 然後，此物件代表 Visio 應用程式，而且是所有其他物件的父代。 其成員通常會整體套用至 Visio。 您可以使用 Microsoft 的屬性和方法，以及用 `Microsoft.Office.Interop.Visio.ApplicationSettings` 來控制 Visio 環境的物件。

 在 VSTO 增益集專案中，您可以使用類別的欄位來存取該應用程式物件 `Application` `ThisAddIn` 。 如需詳細資訊，請參閱 [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md)。

### <a name="document-object"></a>Document 物件
 Microsoft.Office.Interop.Visio.Doc>ument 物件是 Visio 程式設計的核心。 它代表繪圖、樣板或範本檔案。 當您開啟 Visio 檔或建立新檔時，您會建立新的 Microsoft.Office.Interop.Visio.Doc>ument 物件，這個物件會加入 Microsoft.Office.Interop.Visio.Doc至 uments 的集合中。

 具有焦點的文件稱為使用中文件。 它是以 Microsoft 的 `Microsoft.Office.Interop.Visio.Application.ActiveDocument` 屬性（property）表示。

### <a name="page-object"></a>Page 物件
 [中] 物件代表前景頁面的繪圖區域，或是背景頁面。 您可以使用 `Microsoft.Office.Interop.Visio.Page.Background` 屬性判斷頁面為前景或背景頁面。

 若要建立圖形，您可以使用包含 `Microsoft.Office.Interop.Visio.Page.DrawSpline` 和 `Microsoft.Office.Interop.Visio.Page.DrawOval` 方法的方法。 此外，您可以使用 `Microsoft.Office.Interop.Visio.Page.Drop` 或 `Microsoft.Office.Interop.Visio.Page.DropMany` 方法，從樣板擷取主圖形，並將圖形放在頁面上。

## <a name="use-the-visio-object-model-documentation"></a>使用 Visio 物件模型檔
 如需 Visio 物件模型的完整資訊，您可以參考 Visio VBA 物件模型參考。 VBA 物件模型參考記載公開給 Visual Basic for Applications (VBA) 程式碼時的 Visual 物件模型。 如需詳細資訊，請參閱 [Visio 物件模型參考](/office/vba/api/overview/visio/object-model)。

 VBA 物件模型參考中的所有物件和成員都會對應至 Visio 主要 Interop 組件 (PIA) 中的類型和成員。 例如， `Document` VBA 物件模型參考中的物件會對應至 VISIO PIA 中的 Microsoft.Office.Interop.Visio.Doc>ument 型別。 雖然 VBA 物件模型參考會提供大部分屬性、方法和事件的程式碼範例，但如果您想要在以 Visual Studio 建立的 Visio VSTO 增益集專案中使用這些程式碼範例，您必須將此參考中的 VBA 程式碼改成 Visual Basic 或 Visual C# 程式碼。

> [!NOTE]
> 目前沒有 Visio 主要 Interop 組件的參考文件。

 如需相關程式碼範例及其他建立 Visio 方案的工具，請參閱 [Visio 2010 軟體發展工具組](https://www.microsoft.com/download/details.aspx?id=12365)。

### <a name="additional-types-in-primary-interop-assemblies"></a>主要 interop 元件中的其他類型
 因為實作差異之故，您可以在主要 Interop 組件中找到對 VBA 不可見的類型。 VBA 提供檢視 Visio 物件模型，內含您可直接使用的物件和成員。 主要 Interop 組件會公開相同的物件模型，但也包含其他介面、類別和成員，可將 COM 物件模型中的物件轉譯成 managed 程式碼。 這些額外的項目不宜直接在程式碼中使用。

 如需詳細資訊，請參閱 Office 主要 interop 元件和[office 主要 interop 元件](../vsto/office-primary-interop-assemblies.md)[中的類別和介面總覽](/previous-versions/office/office-12/ms247299(v=office.12))。

## <a name="see-also"></a>另請參閱
- [Visio 方案](../vsto/visio-solutions.md)
- [使用 Visio 檔](../vsto/working-with-visio-documents.md)
- [使用 Visio 圖形](../vsto/working-with-visio-shapes.md)
