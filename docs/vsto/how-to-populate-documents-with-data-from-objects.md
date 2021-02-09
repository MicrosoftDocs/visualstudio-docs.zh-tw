---
title: 如何：將物件的資料填入檔
description: 瞭解如何在您的方案中使用物件中的資料，而且您可以使用 Windows Forms 控制項來顯示檔中的資料。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], populating with data
- data [Office development in Visual Studio], adding to documents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 5bebc21fb02f6b5441c597fcfd25364991829e71
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99918572"
---
# <a name="how-to-populate-documents-with-data-from-objects"></a>如何：將物件的資料填入檔

在 Microsoft Office Word 文件層級專案中使用資料物件存取資料時，其運作方式與在 Windows Form 專案中的運作方式相同。 您可以使用相同的工具和程式碼，將資料從物件帶入方案中，也可以使用 Windows Form 控制項顯示資料。 此外，也可以使用主控制項來顯示資料。 主控制項是 Microsoft Office Word 中的原生物件，已使用事件和資料繫結功能強化。 如需詳細資訊，請參閱 [主專案和主控制項總覽](../vsto/host-items-and-host-controls-overview.md)。

[!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]

您必須先完成三個基本步驟，才能將物件的資料填入文件：

- 將控制項加入可繫結到資料的文件。

- 將資料物件加入文件。

- 將資料物件連接至 BindingSource。

## <a name="to-add-a-data-object"></a>若要加入資料物件

若要加入資料物件，請開啟 [ **資料來源** ] 視窗，並從物件建立資料來源。 如需詳細資訊，請參閱[新增資料來源](../data-tools/add-new-data-sources.md)。

## <a name="connect-the-data-object-to-the-bindingsource"></a>將資料物件連接至 BindingSource

在文件層級專案中，您可以在設計階段將控制項加入文件，並將控制項繫結至資料。

在 VSTO 增益集專案中，您可以在執行階段建立並繫結控制項。

### <a name="document-level-projects"></a>檔層級專案

若要將資料物件連接至 BindingSource：

1. 將想要的資料欄位從 [資料來源]  視窗拖曳至您的文件。 這樣會自動建立控制項。

2. 在程式碼中，針對您為資料來源所選取的物件類型，建立執行個體。

3. 將該執行個體指派給 <xref:System.Windows.Forms.BindingSource.DataSource%2A> 的 <xref:System.Windows.Forms.BindingSource>屬性。

### <a name="application-level-projects"></a>應用層級專案

若要將資料物件連接至 BindingSource：

1. 在程式碼中，針對與資料來源相關聯的物件類型，建立執行個體。

2. 建立 <xref:System.Windows.Forms.BindingSource> 的執行個體。

3. 將該資料來源執行個體指派給 <xref:System.Windows.Forms.BindingSource.DataSource%2A> 的 <xref:System.Windows.Forms.BindingSource>屬性。

4. 將資料來源做為資料繫結加入控制項中。

## <a name="see-also"></a>另請參閱

- [新增新資料來源](../data-tools/add-new-data-sources.md)
- [將 Windows Forms 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [如何：使用資料庫的資料填入檔](../vsto/how-to-populate-documents-with-data-from-a-database.md)
- [如何：使用主控制項的資料更新資料來源](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)
- [BindingSource 元件總覽](/dotnet/framework/winforms/controls/bindingsource-component-overview)