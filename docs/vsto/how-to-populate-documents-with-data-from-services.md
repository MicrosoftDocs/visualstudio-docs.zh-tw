---
title: 如何： 擴展的資料服務文件
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], populating with data
- Web services [Office development in Visual Studio], populating documents
- data [Office development in Visual Studio], adding to documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 4ac901b524818086d6dbf23b7b55487054170b3e
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2018
ms.locfileid: "36758538"
---
# <a name="how-to-populate-documents-with-data-from-services"></a>如何： 擴展的資料服務文件

在 Microsoft Office 文件層級專案中存取資料時，其運作方式與在 Windows Forms 專案中的運作方式相同。 您可以使用相同的工具和程式碼將資料帶入方案中，甚至可以使用 Windows Forms 控制項顯示資料。 此外，還可以利用一種稱為主控制項的控制項，這是 Microsoft Office Excel 和 Microsoft Office Word 中的原生物件，但是經過事件和資料繫結功能的加強。 如需詳細資訊，請參閱 <<c0> [ 主項目和裝載控制項概觀](../vsto/host-items-and-host-controls-overview.md)。

[!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

下列範例說明如何在設計階段，將資料繫結控制項加入文件。 如需如何將 VSTO 增益集的資料繫結控制項，在執行階段的範例，請參閱 <<c0> [ 逐步解說： 從 VSTO 增益集專案中的服務繫結至資料](../vsto/walkthrough-binding-to-data-from-a-service-in-a-vsto-add-in-project.md)。

![影片連結](../vsto/media/playvideo.gif "影片連結")如需相關的影片示範，請參閱[How do i： 互動與 web 服務從 Microsoft Excel？](http://go.microsoft.com/fwlink/?LinkID=130284)。

## <a name="to-populate-a-document-level-project-with-data-from-a-web-service"></a>若要填入的文件層級專案與 web 服務的資料

1.  開啟 [資料來源]  視窗並為您的專案建立服務資料來源。 如需詳細資訊，請參閱[新增資料來源](../data-tools/add-new-data-sources.md)。

2.  將想要的資料表或欄位從 [資料來源]  視窗拖曳至您的文件。

     即會在文件中建立控制項，並建立 <xref:System.Windows.Forms.BindingSource> 以繫結至專案中的物件類別，然後再產生該服務的類別。

3.  在您的程式碼中，建立您在步驟 1 中連接到 web 服務類別的執行個體。

4.  如果有與 web 服務通訊所需的屬性，建立這些屬性的執行個體。

5.  使用 Web 服務所公開的方法以及您在步驟 4 建立的任何屬性執行個體，建立並傳送資料要求。

     您所使用的方法取決於 web 服務提供。

6.  從 web 服務，以指定的資料回應<xref:System.Windows.Forms.BindingSource.DataSource%2A>屬性<xref:System.Windows.Forms.BindingSource>。

當您執行專案時，控制項會顯示資料來源中的第一筆記錄。 您可以使用 <xref:System.Windows.Forms.BindingSource>中的物件處理貨幣事件，啟用捲動記錄的功能。

## <a name="see-also"></a>另請參閱

- [資料繫結至 Office 方案中的控制項](../vsto/binding-data-to-controls-in-office-solutions.md)
- [新增資料來源](../data-tools/add-new-data-sources.md)
- [將 Windows Forms 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [如何： 從資料庫的資料填入工作表](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)
- [如何： 的物件的資料填入文件](../vsto/how-to-populate-documents-with-data-from-objects.md)
- [如何： 的資料庫中的資料填入文件](../vsto/how-to-populate-documents-with-data-from-a-database.md)
- [如何： 從主控制項的資料更新資料來源](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)