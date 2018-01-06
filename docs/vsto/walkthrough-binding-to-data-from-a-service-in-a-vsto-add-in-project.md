---
title: "逐步解說： 繫結至資料服務中的 VSTO 增益集專案 |Microsoft 文件"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- databases [Office development in Visual Studio], scrolling records
- records [Office development in Visual Studio], scrolling
- data [Office development in Visual Studio], scrolling database records
ms.assetid: 9b008be4-06a3-4ffc-9f02-79dd6cfe00ab
caps.latest.revision: "38"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 035b74048aca3b91449bc857a36594bc280065c4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-binding-to-data-from-a-service-in-a-vsto-add-in-project"></a>逐步解說：在 VSTO 增益集專案中繫結至服務資料
  您可以將資料繫結至 VSTO 增益集專案中的主控制項。 本逐步解說示範如何將控制項加入 Microsoft Office Word 文件、將控制項繫結至從 MSDN 內容服務擷取的資料，以及在執行階段回應事件。  
  
 **適用對象：** 本主題資訊適用於 Word 2010 的應用程式層級專案。 如需詳細資訊，請參閱 [Features Available by Office Application and Project Type](../vsto/features-available-by-office-application-and-project-type.md)。  
  
 這個逐步解說將說明下列工作：  
  
-   在設計階段將 <xref:Microsoft.Office.Tools.Word.RichTextContentControl> 控制項加入文件。  
  
-   將 <xref:Microsoft.Office.Tools.Word.RichTextContentControl> 控制項繫結至來自 Web 服務的資料。  
  
-   回應 <xref:Microsoft.Office.Tools.Word.ContentControlBase.Entering> 控制項的 <xref:Microsoft.Office.Tools.Word.RichTextContentControl> 事件。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>必要條件  
 您需要下列元件才能完成此逐步解說：  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] 或 [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)]。  
  
## <a name="creating-a-new-project"></a>建立新專案  
 第一步是建立 Word VSTO 增益集專案。  
  
#### <a name="to-create-a-new-project"></a>建立新的專案  
  
1.  使用 Visual Basic 或 C#，建立名稱為 [MTPS 內容服務] 的 Word VSTO 增益集專案。  
  
     如需詳細資訊，請參閱 [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)。  
  
     Visual Studio 隨即開啟 `ThisAddIn.vb` 或 `ThisAddIn.cs` 檔案，並將專案加入 **方案總管**。  
  
## <a name="adding-a-web-service"></a>加入 Web 服務  
 此逐步解說中使用稱為 MTPS 內容服務的 Web 服務。 此 Web 服務會從指定的 MSDN 文章，以 XML 字串或純文字形式傳回資訊。 接下來的步驟示範如何在內容控制項中顯示傳回的資訊。  
  
#### <a name="to-add-the-mtps-content-service-to-the-project"></a>將 MTPS 內容服務加入專案  
  
1.  在 [ **資料** ] 功能表上，請按一下 [ **加入新資料來源**]。  
  
2.  在 [資料來源組態精靈] 中，按一下 [服務] ，然後按 [下一步] 。  
  
3.  在 [位址]  欄位中，輸入下列 URL：  
  
     **http://services.msdn.microsoft.com/ContentServices/ContentService.asmx**  
  
4.  按一下 [ **Go**]。  
  
5.  在 [命名空間]  欄位中，輸入 **ContentService**，然後按一下 [確定] 。  
  
6.  在 [加入參考精靈]  對話方塊中，按一下 [完成] 。  
  
## <a name="adding-a-content-control-and-binding-to-data-at-run-time"></a>在執行階段加入內容控制項並繫結至資料  
 在 VSTO 增益集專案中，您會在執行階段加入及繫結控制項。 此逐步解說中，請設定內容控制項，當使用者在控制項內按一下時，從 Web 服務擷取資料。  
  
#### <a name="to-add-a-content-control-and-bind-to-data"></a>加入內容控制項並繫結至資料  
  
1.  在 `ThisAddIn` 類別中，宣告 MTPS 內容服務、內容控制項和資料繫結的變數。  
  
     [!code-csharp[Trin_WordAddIn_BindingDataToContentControl#2](../vsto/codesnippet/CSharp/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.cs#2)]
     [!code-vb[Trin_WordAddIn_BindingDataToContentControl#2](../vsto/codesnippet/VisualBasic/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.vb#2)]  
  
2.  將下列方法加入 `ThisAddIn` 類別中。 這個方法會在使用中文件的開頭建立內容控制項。  
  
     [!code-csharp[Trin_WordAddIn_BindingDataToContentControl#4](../vsto/codesnippet/CSharp/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.cs#4)]
     [!code-vb[Trin_WordAddIn_BindingDataToContentControl#4](../vsto/codesnippet/VisualBasic/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.vb#4)]  
  
3.  將下列方法加入 `ThisAddIn` 類別中。 這個方法會初始化所需的物件，建立並傳送要求至 Web 服務。  
  
     [!code-csharp[Trin_WordAddIn_BindingDataToContentControl#6](../vsto/codesnippet/CSharp/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.cs#6)]
     [!code-vb[Trin_WordAddIn_BindingDataToContentControl#6](../vsto/codesnippet/VisualBasic/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.vb#6)]  
  
4.  建立事件處理常式來擷取 MSDN Library 文件，關於使用者在內容控制項內按一下並將資料繫結至內容控制項時的內容控制項資訊。  
  
     [!code-csharp[Trin_WordAddIn_BindingDataToContentControl#5](../vsto/codesnippet/CSharp/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.cs#5)]
     [!code-vb[Trin_WordAddIn_BindingDataToContentControl#5](../vsto/codesnippet/VisualBasic/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.vb#5)]  
  
5.  從 `AddRichTextControlAtRange` 方法呼叫 `InitializeServiceObjects` 和 `ThisAddIn_Startup` 方法。 C# 程式設計人員請加入事件處理常式。  
  
     [!code-csharp[Trin_WordAddIn_BindingDataToContentControl#3](../vsto/codesnippet/CSharp/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.cs#3)]
     [!code-vb[Trin_WordAddIn_BindingDataToContentControl#3](../vsto/codesnippet/VisualBasic/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.vb#3)]  
  
## <a name="testing-the-add-in"></a>測試增益集  
 當您開啟 Word 時， <xref:Microsoft.Office.Tools.Word.RichTextContentControl> 控制項就會出現。 當您在控制項內按一下時，它裡面的文字會改變。  
  
#### <a name="to-test-the-vsto-add-in"></a>測試 VSTO 增益集  
  
1.  請按 **F5**。  
  
2.  在內容控制項內按一下。  
  
     資訊會從 MTPS 內容服務下載並顯示在內容控制項內。  
  
## <a name="see-also"></a>請參閱  
 [將資料繫結至 Office 方案中的控制項](../vsto/binding-data-to-controls-in-office-solutions.md)  
  
  