---
title: 逐步解說：建立 PowerPoint 的第一個 VSTO 增益集
description: 建立 Microsoft PowerPoint 的應用層級增益集。 這項功能適用于應用程式本身，不論開啟的是哪一種簡報。
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application-level add-ins [Office development in Visual Studio], creating your first project
- Office development in Visual Studio, creating your first project
- PowerPoint [Office development in Visual Studio], creating your first project
- add-ins [Office development in Visual Studio], creating your first project
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: c73c5ab61c51ca4be749e9bf14700c7bea64023e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99966535"
---
# <a name="walkthrough-create-your-first-vsto-add-in-for-powerpoint"></a>逐步解說：建立 PowerPoint 的第一個 VSTO 增益集
  本逐步解說將說明如何建立 Microsoft Office PowerPoint 的 VSTO 增益集。 不論開啟哪一份簡報，您在這類方案中建立的功能都可供應用程式本身使用。 如需詳細資訊，請參閱 [Office 方案開發總覽 &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)。

 [!INCLUDE[appliesto_pptallapp](../vsto/includes/appliesto-pptallapp-md.md)]

 本逐步解說將說明下列工作：

- 建立 PowerPoint 的 PowerPoint VSTO 增益集專案。

- 撰寫使用 PowerPoint 物件模型將文字方塊加入每張新投影片的程式碼。

- 建置和執行專案來進行測試。

- 清除已完成的專案，使得 VSTO 增益集不再於開發電腦上自動執行。

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>必要條件
 您需要下列元件才能完成這個逐步解說：

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- PowerPoint

## <a name="create-the-project"></a>建立專案

### <a name="to-create-a-new-project"></a>建立新的專案

1. 啟動 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。

2. 在 **[檔案]** 功能表上，指向 **[開新檔案]** ，然後按一下 **[專案]** 。

3. 在範本窗格中，展開 [Visual C#] **Deploying Office Solutions** 或 [Visual Basic] ，然後展開 [Office/SharePoint] 。

4. 在展開的 [Office/SharePoint]  節點下，選取 [Office 增益集]  節點。

5. 在專案範本清單中，選取 PowerPoint VSTO 增益集專案。

6. 在 [ **名稱** ] 方塊中，輸入 **FirstPowerPointAddIn**。

7. 按一下 [確定]  。

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 建立 **FirstPowerPointAddIn** 專案，並在編輯器中開啟 **ThisAddIn** 程式碼檔案。

## <a name="write-code-that-adds-text-to-each-new-slide"></a>撰寫程式碼以將文字新增至每張新投影片
 接著，將程式碼加入 ThisAddIn 程式碼檔。 新的程式碼會使用 PowerPoint 的物件模型，將文字方塊加入每張新投影片。 根據預設，ThisAddIn 程式碼檔包含下列產生的程式碼：

- `ThisAddIn` 類別的部分定義。 這個類別提供您撰寫程式碼的進入點，並提供對 PowerPoint 物件模型的存取。 如需詳細資訊，請參閱 [程式 VSTO 增益集](../vsto/programming-vsto-add-ins.md)。類別的其餘部分 `ThisAddIn` 是在不應修改的隱藏程式碼檔案中定義。

- `ThisAddIn_Startup` 和 `ThisAddIn_Shutdown` 事件處理常式。 當 PowerPoint 載入和卸載 VSTO 增益集時，會呼叫這些事件處理常式。 請使用這些事件處理常式，在 VSTO 增益集載入時將它初始化，以及在 VSTO 增益集卸載時清除它所用的資源。 如需詳細資訊，請參閱 [Office 專案中的事件](../vsto/events-in-office-projects.md)。

### <a name="to-add-a-text-box-to-each-new-slide"></a>若要將文字方塊加入每張新的投影片

1. 在 ThisAddIn 程式碼檔中，將下列程式碼加入 `ThisAddIn` 類別。 此程式碼會定義[應用程式](/previous-versions/office/developer/office-2010/ff764034(v=office.14))物件的[Microsoft.Office.Interop.PowerPoint.EApplication_Event PresentationNewSlide](/previous-versions/office/developer/office-2010/ff762876(v%3doffice.14))事件的事件處理常式。

    當使用者將新投影片加入現用簡報時，這個事件處理常式會在新投影片頂端加入文字方塊，並將一些文字加入此文字方塊。

    [!code-vb[Trin_PowerPointAddInTutorial#1](../vsto/codesnippet/VisualBasic/Trin_PowerPointAddInTutorial/ThisAddIn.vb#1)]
    [!code-csharp[Trin_PowerPointAddInTutorial#1](../vsto/codesnippet/CSharp/Trin_PowerPointAddInTutorial/ThisAddIn.cs#1)]

2. 如果使用的是 C#，請將下列程式碼加入 `ThisAddIn_Startup` 事件處理常式中。 這是連接 `Application_PresentationNewSlide` 事件處理常式與 [Microsoft.Office.Interop.PowerPoint.EApplication_Event PresentationNewSlide](/previous-versions/office/developer/office-2010/ff762876(v%3doffice.14)) 事件的必要程式碼。

    [!code-csharp[Trin_PowerPointAddInTutorial#2](../vsto/codesnippet/CSharp/Trin_PowerPointAddInTutorial/ThisAddIn.cs#2)]

   若要修改每張新投影片，前面的程式碼範例可以使用下列物件：

- `Application` 類別的 `ThisAddIn` 欄位。 欄位會傳回 `Application` 代表目前 PowerPoint 實例的 [應用程式](/previous-versions/office/developer/office-2010/ff764034(v=office.14)) 物件。

- `Sld` [Microsoft.Office.Interop.PowerPoint.EApplication_Event PresentationNewSlide](/previous-versions/office/developer/office-2010/ff762876(v%3doffice.14))事件之事件處理常式的參數。 `Sld`參數是投影[片](/previous-versions/office/developer/office-2010/ff763417(v=office.14))物件，代表新投影片。 如需詳細資訊，請參閱 [PowerPoint 方案](../vsto/powerpoint-solutions.md)。

## <a name="test-the-project"></a>測試專案
 當您建置和執行專案時，請確認文字方塊有出現在您加入簡報的新投影片中。

### <a name="to-test-the-project"></a>測試專案

1. 按 **F5** 建置及執行專案。

     當您建置專案時，程式碼會編譯為放置在專案建置輸出資料夾中的組件。 Visual Studio 也會建立一組登錄項目，以便 PowerPoint 探索和載入 VSTO 增益集，而且會設定開發電腦中的安全性設定，讓 VSTO 增益集可以執行。 如需詳細資訊，請參閱 [建立 Office 方案](../vsto/building-office-solutions.md)。

2. 在 PowerPoint 中，將新投影片加入現用簡報。

3. 確認下列文字已加入投影片頂端的新文字方塊中。

     **This text was added by using code.**

4. 關閉 PowerPoint。

## <a name="clean-up-the-project"></a>清除專案
 當您完成專案開發時，請從開發電腦移除 VSTO 增益集組件、登錄項目和安全性設定。 否則，每次在開發電腦上開啟 PowerPoint 時，就會執行 VSTO 增益集。

### <a name="to-clean-up-your-project"></a>清除專案

1. 在 Visual Studio 中，按一下 [建置]  功能表上的 [清除方案] 。

## <a name="next-steps"></a>下一步
 現在您已經建立 PowerPoint 的基本 VSTO 增益集，可以從下列主題進一步了解如何開發 VSTO 增益集：

- 您可以透過 PowerPoint VSTO 增益集執行的一般程式設計工作。 如需詳細資訊，請參閱 [程式 VSTO 增益集](../vsto/programming-vsto-add-ins.md)。

- 使用 PowerPoint 物件模型。 如需詳細資訊，請參閱 [PowerPoint 方案](../vsto/powerpoint-solutions.md)。

- 自訂 PowerPoint 的 UI，例如，透過將自訂索引標籤加入功能區，或建立您專屬自訂工作窗格的方式。 如需詳細資訊，請參閱 [OFFICE UI 自訂](../vsto/office-ui-customization.md)。

- 建置及偵錯 PowerPoint VSTO 增益集。 如需詳細資訊，請參閱 [建立 Office 方案](../vsto/building-office-solutions.md)。

- 部署 PowerPoint VSTO 增益集。 如需詳細資訊，請參閱 [部署 Office 方案](../vsto/deploying-an-office-solution.md)。

## <a name="see-also"></a>另請參閱
- [程式 VSTO 增益集](../vsto/programming-vsto-add-ins.md)
- [PowerPoint 方案](../vsto/powerpoint-solutions.md)
- [Office UI 自訂](../vsto/office-ui-customization.md)
- [建立 Office 方案](../vsto/building-office-solutions.md)
- [部署 Office 方案](../vsto/deploying-an-office-solution.md)
- [Office 專案範本總覽](../vsto/office-project-templates-overview.md)
