---
title: 在執行階段功能區的存取
ms.custom: ''
ms.date: 02/02/2017
ms.technology: office-development
ms.prod: visual-studio-dev15
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Globals class, Ribbon
- Ribbon [Office development in Visual Studio], accessing
- RibbonManager class
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9a20297ee0d60173cbd0513f3d34e12f12388bdb
ms.sourcegitcommit: 81e9d90843ead658bc73b30c869f25921d99e116
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2018
ms.locfileid: "52304619"
---
# <a name="access-the-ribbon-at-runtime"></a>在執行階段功能區的存取
  您可以撰寫程式碼以顯示、隱藏和修改功能區，並且讓使用者從自訂工作窗格、執行窗格或 Outlook 表單區域中的控制項執行程式碼。  

 您可以使用 `Globals` 類別來存取功能區。 針對 Outlook 專案，您可以存取出現在特定 [Outlook 檢查] 或 [Outlook 總管] 視窗中的功能區。  

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  

## <a name="access-the-ribbon-by-using-the-globals-class"></a>使用 Globals 類別存取功能區  
 您可以使用 `Globals` 類別，從專案中任意位置存取文件層級專案或 VSTO 增益集專案中的功能區。  

 如需詳細資訊`Globals`類別，請參閱[全域存取 Office 專案中的物件](../vsto/global-access-to-objects-in-office-projects.md)。  

 以下範例將使用 `Globals` 類別存取名為 `Ribbon1` 的自訂功能區，並且將出現在功能區下拉式方塊中的文字設定為 `Hello World`。  

 [!code-vb[Trin_Outlook_FR_Access#4](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb#4)]
 [!code-csharp[Trin_Outlook_FR_Access#4](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs#4)]  

## <a name="access-a-collection-of-ribbons-that-appear-in-a-specific-outlook-inspector-window"></a>存取出現在特定 [Outlook 檢查] 視窗中的功能區集合  
 您可以存取出現在 Outlook 功能區集合*偵測器*。 [檢查] 是一個視窗，會在使用者執行特定工作 (例如建立電子郵件訊息) 時，在 Outlook 中開啟。 若要存取 [檢查] 視窗的功能區，請呼叫 `Globals` 類別的 `Ribbons` 屬性，並傳入代表 [檢查] 的 <xref:Microsoft.Office.Interop.Outlook.Inspector> 物件。  

 以下範例將取得目前擁有焦點之 [檢查] 中的功能區集合。 然後這個範例會存取名為 `Ribbon1` 的功能區，並且將出現在功能區下拉式方塊中的文字設定為 `Hello World`。  

 [!code-vb[Trin_Outlook_FR_Access#5](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb#5)]
 [!code-csharp[Trin_Outlook_FR_Access#5](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs#5)]  

## <a name="access-a-collection-of-ribbons-that-appear-for-a-specific-outlook-explorer"></a>存取出現在特定 Outlook 總管的功能區集合  
 您可以存取出現在 Outlook 功能區集合*總管*。 [總管] 是 Outlook 執行個體的主要應用程式使用者介面 (UI)。 若要存取 [總管] 視窗的功能區，請呼叫 `Globals` 類別的 `Ribbons` 屬性，並傳入代表 [總管] 的 <xref:Microsoft.Office.Interop.Outlook.Explorer> 物件。  

 下列範例會取得目前擁有焦點的 [總管] 中的功能區集合。 然後這個範例會存取名為 `Ribbon1` 的功能區，並且將出現在功能區下拉式方塊中的文字設定為 `Hello World`。  

 [!code-vb[Trin_Outlook_FR_Access#6](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb#6)]
 [!code-csharp[Trin_Outlook_FR_Access#6](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs#6)]  

## <a name="see-also"></a>另請參閱  
 [功能區概觀](../vsto/ribbon-overview.md)   
 [功能區設計工具](../vsto/ribbon-designer.md)   
 [功能區 XML](../vsto/ribbon-xml.md)   
 [功能區物件模型概觀](../vsto/ribbon-object-model-overview.md)   
 [逐步解說： 使用功能區設計工具建立自訂索引標籤](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [逐步解說： 更新在執行階段的功能區上的控制項](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)   
 [適用於 Outlook 自訂功能區](../vsto/customizing-a-ribbon-for-outlook.md)   
 [存取表單區域在執行階段](../vsto/accessing-a-form-region-at-run-time.md)  
