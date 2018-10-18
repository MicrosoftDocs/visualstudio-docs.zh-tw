---
title: Windows Forms 控制項繫結至 Visual Studio 中的資料 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
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
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e63d20bc226abe0c0bdf4c77179a94b0d0e6212c
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49293666"
---
# <a name="bind-windows-forms-controls-to-data-in-visual-studio"></a>Windows Forms 控制項繫結至 Visual Studio 中的資料
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
您可以藉由將資料繫結至 Windows Forms 應用程式的使用者顯示資料。 若要建立這些資料繫結控制項，您可以將項目從**Zdroje dat**視窗拖曳至 Visual Studio 中的 Windows Form 設計工具。 本主題說明一些最常見的工作、 工具和建立資料繫結 Windows Forms 應用程式所需的類別。  
  
 ![資料來源拖曳作業](../data-tools/media/raddata-data-source-drag-operation.png "raddata 資料來源拖曳作業")  
  
 如需如何在 Visual Studio 中建立資料繫結控制項的一般資訊，請參閱[控制項繫結至 Visual Studio 中的資料](../data-tools/bind-controls-to-data-in-visual-studio.md)。 如需有關在 Windows Form 中的資料繫結的詳細資訊，請參閱[Windows Form 資料繫結](http://msdn.microsoft.com/library/c3826d8e-ea25-4ad4-a669-45bfb19192aa)。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [將 Windows Forms 控制項繫結至資料](../data-tools/bind-windows-forms-controls-to-data.md)  
  
-   [儲存資料前先認可資料繫結控制項上的同處理序編輯](../data-tools/commit-in-process-edits-on-data-bound-controls-before-saving-data.md)  
  
-   [在 Windows Forms 應用程式中建立查閱資料表](../data-tools/create-lookup-tables-in-windows-forms-applications.md)  
  
-   [建立 Windows Form 以搜尋資料](../data-tools/create-a-windows-form-to-search-data.md)  
  
-   [建立支援簡單資料繫結的 Windows Forms 使用者控制項](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md)  
  
-   [建立支援複雜資料繫結的 Windows Forms 使用者控制項](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md)  
  
-   [建立支援查閱資料繫結的 Windows Forms 使用者控制項](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md)  
  
-   [在表單之間傳遞資料](../data-tools/pass-data-between-forms.md)  
  
## <a name="bindingsource-component"></a>BindingSource 元件  
 <xref:System.Windows.Forms.BindingSource> 元件有兩種用途。 第一，它提供一個抽象層，當您在表單上的控制項繫結至資料。 在表單上的控制項繫結至<xref:System.Windows.Forms.BindingSource>元件 （而不是正在直接繫結至資料來源）。  
  
 其次，它可以管理物件的集合。 將類型加入<xref:System.Windows.Forms.BindingSource>會建立該類型的清單。  
  
 如需詳細資訊<xref:System.Windows.Forms.BindingSource>元件，請參閱：  
  
-   [BindingSource 元件](http://msdn.microsoft.com/library/3e2faf4c-f5b8-4fa6-9fbc-f59c37ec2fb9)  
  
-   [BindingSource 元件概觀](http://msdn.microsoft.com/library/be838caf-fcb0-4b68-827f-58b2c04b747f)  
  
-   [BindingSource 元件架構](http://msdn.microsoft.com/library/7bc69c90-8a11-48b1-9336-3adab5b41591)  
  
## <a name="bindingnavigator-control"></a>BindingNavigator 控制項  
 此元件提供使用者介面瀏覽 Windows 應用程式顯示的資料。 如需詳細資訊，請參閱 [BindingNavigator 控制項](http://msdn.microsoft.com/library/18c1e2a5-9834-40d3-9b2e-2b545e4e769e)。  
  
## <a name="datagridview-control"></a>DataGridView 控制項  
 若要顯示和編輯表格式資料從許多不同種類的資料來源，使用<xref:System.Windows.Forms.DataGridView>控制項。 您可以將資料繫結<xref:System.Windows.Forms.DataGridView>使用<xref:System.Windows.Forms.DataGridView.DataSource%2A>屬性。 如需詳細資訊，請參閱 < [DataGridView 控制項概觀](http://msdn.microsoft.com/library/0a45c661-89dc-4390-9cc6-c47eee501488)。  
  
## <a name="see-also"></a>另請參閱  
 [將控制項繫結至 Visual Studio 中的資料](../data-tools/bind-controls-to-data-in-visual-studio.md)

