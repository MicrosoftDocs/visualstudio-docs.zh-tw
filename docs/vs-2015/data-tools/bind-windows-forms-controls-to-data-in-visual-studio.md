---
title: 將 Windows Forms 控制項繫結至資料
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
- data [Windows Forms], data sources
- Windows Forms, data binding
- Windows Forms, displaying data
- displaying data on forms
- forms, displaying data
- data sources, displaying data
- displaying data, Windows Forms
- data [Windows Forms], displaying
ms.assetid: 243338ef-41af-4cc5-aff7-1e830236f0ec
caps.latest.revision: 40
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8a03f4df57b216fa68e5ac24df80b67917aa3e3f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672992"
---
# <a name="bind-windows-forms-controls-to-data-in-visual-studio"></a>將 Windows Forms 控制項繫結至 Visual Studio 中的資料
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以藉由將資料系結至 Windows Forms，向應用程式的使用者顯示資料。 若要建立這些資料繫結控制項，您可以將專案從 [**資料來源**] 視窗拖曳至 Visual Studio 中的 Windows Form 設計工具。 本主題描述一些與建立資料系結 Windows Forms 應用程式相關的最常見工作、工具和類別。

 ![資料來源拖曳作業](../data-tools/media/raddata-data-source-drag-operation.png "raddata 資料來源拖曳操作")

 如需如何在 Visual Studio 中建立資料繫結控制項的一般資訊，請參閱將控制項系結[至 Visual Studio 中的資料](../data-tools/bind-controls-to-data-in-visual-studio.md)。 如需 Windows Forms 中資料系結的詳細資訊，請參閱[Windows Forms 資料](https://msdn.microsoft.com/library/c3826d8e-ea25-4ad4-a669-45bfb19192aa)系結。

## <a name="in-this-section"></a>本節內容

- [將 Windows Forms 控制項繫結至資料](../data-tools/bind-windows-forms-controls-to-data.md)

- [儲存資料前先認可資料繫結控制項上的同處理序編輯](../data-tools/commit-in-process-edits-on-data-bound-controls-before-saving-data.md)

- [在 Windows Forms 應用程式中建立查閱資料表](../data-tools/create-lookup-tables-in-windows-forms-applications.md)

- [建立 Windows Form 以搜尋資料](../data-tools/create-a-windows-form-to-search-data.md)

- [建立支援簡單資料繫結的 Windows Forms 使用者控制項](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md)

- [建立支援複雜資料繫結的 Windows Forms 使用者控制項](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md)

- [建立支援查閱資料繫結的 Windows Forms 使用者控制項](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md)

- [在表單之間傳遞資料](../data-tools/pass-data-between-forms.md)

## <a name="bindingsource-component"></a>BindingSource 元件
 <xref:System.Windows.Forms.BindingSource> 元件有兩種用途。 首先，它會在將您的表單上的控制項系結至資料時，提供抽象層。 表單上的控制項系結至 <xref:System.Windows.Forms.BindingSource> 元件（而不是直接系結至資料來源）。

 第二，它可以管理物件的集合。 將類型加入至 <xref:System.Windows.Forms.BindingSource> 會建立該類型的清單。

 如需 <xref:System.Windows.Forms.BindingSource> 元件的詳細資訊，請參閱：

- [BindingSource 元件](https://msdn.microsoft.com/library/3e2faf4c-f5b8-4fa6-9fbc-f59c37ec2fb9)

- [BindingSource 元件概觀](https://msdn.microsoft.com/library/be838caf-fcb0-4b68-827f-58b2c04b747f)

- [BindingSource 元件架構](https://msdn.microsoft.com/library/7bc69c90-8a11-48b1-9336-3adab5b41591)

## <a name="bindingnavigator-control"></a>BindingNavigator 控制項
 此元件提供使用者介面，可供流覽 Windows 應用程式所顯示的資料。 如需詳細資訊，請參閱 [BindingNavigator 控制項](https://msdn.microsoft.com/library/18c1e2a5-9834-40d3-9b2e-2b545e4e769e)。

## <a name="datagridview-control"></a>DataGridView 控制項
 若要顯示和編輯許多不同資料來源類型的表格式資料，請使用 <xref:System.Windows.Forms.DataGridView> 控制項。 您可以使用 <xref:System.Windows.Forms.DataGridView.DataSource%2A> 屬性，將資料系結至 <xref:System.Windows.Forms.DataGridView>。 如需詳細資訊，請參閱[DataGridView 控制項總覽](https://msdn.microsoft.com/library/0a45c661-89dc-4390-9cc6-c47eee501488)。

## <a name="see-also"></a>請參閱
 [將控制項繫結至 Visual Studio 中的資料](../data-tools/bind-controls-to-data-in-visual-studio.md)
