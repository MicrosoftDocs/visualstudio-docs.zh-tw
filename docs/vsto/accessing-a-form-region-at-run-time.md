---
title: 在執行時間存取表單區域
description: 瞭解如何在執行時間存取各種專案類型和版本 Microsoft Office 中的表單區域。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Inspectors [Office development in Visual Studio]
- Explorers [Office development in Visual Studio]
- form regions [Office development in Visual Studio], accessing at run time
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 62d8236b987afbb7dc9d5e4462b79ffb4fe00bc5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99928870"
---
# <a name="access-a-form-region-at-run-time"></a>在執行時間存取表單區域

|適用於|
|----------------|
|本主題資訊僅適用於下列 Microsoft Office 專案類型及版本。 如需詳細資訊，請參閱 [依 Office 應用程式和專案類型提供的功能](../vsto/features-available-by-office-application-and-project-type.md)。<br /><br /> **專案類型**<br /><br /> -VSTO 增益集專案<br /><br /> **Microsoft Office 版本**<br /><br /> -   [!INCLUDE[Outlook_14_short](../vsto/includes/outlook-14-short-md.md)]|

 使用 `Globals` 類別，從任何地方在 Outlook 專案中存取表單區域。 如需類別的詳細資訊 `Globals` ，請參閱 [全域存取 Office 專案中的物件](../vsto/global-access-to-objects-in-office-projects.md)。

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="access-form-regions-that-appear-in-a-specific-outlook-inspector-window"></a>出現在特定 [Outlook 檢查] 視窗中的存取表單區域
 若要存取出現在特定 Outlook 檢查中的所有表單區域，請呼叫 `FormRegions` 類別的 `Globals` 屬性，並傳入代表該檢查的 <xref:Microsoft.Office.Interop.Outlook.Inspector> 物件。

 以下範例將取得目前擁有焦點之檢查中出現的表單區域集合。 然後這個範例會存取名為 `formRegion1` 之集合中的表單區域，並且將出現在文字方塊中的文字設定為 `Hello World`。

 [!code-vb[Trin_Outlook_FR_Access#2](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb#2)]
 [!code-csharp[Trin_Outlook_FR_Access#2](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs#2)]

## <a name="access-form-regions-that-appear-in-a-specific-outlook-explorer-window"></a>在特定的 Outlook Explorer 視窗中顯示的存取表單區域
 若要存取出現在特定 Outlook 總管中的所有表單區域，請呼叫 `FormRegions` 類別的 `Globals` 屬性，並傳入代表該總管的 <xref:Microsoft.Office.Interop.Outlook.Explorer> 物件。

 以下範例將取得目前擁有焦點之總管中出現的表單區域集合。 然後這個範例會存取名為 `formRegion1` 之集合中的表單區域，並且將出現在文字方塊中的文字設定為 `Hello World`。

 [!code-vb[Trin_Outlook_FR_Access#3](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb#3)]
 [!code-csharp[Trin_Outlook_FR_Access#3](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs#3)]

## <a name="access-all-form-regions"></a>存取所有表單區域
 若要存取出現在所有總管及檢查中的全部表單區域，請呼叫 `FormRegions` 類別的 `Globals` 屬性。

 以下範例將取得在所有總管及所有檢查中出現的表單區域集合。 然後這個範例會存取名為 `formRegion1` 的表單區域，並且將出現在文字方塊中的文字設定為 `Hello World`。

 [!code-vb[Trin_Outlook_FR_Access#1](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb#1)]
 [!code-csharp[Trin_Outlook_FR_Access#1](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs#1)]

## <a name="access-controls-on-a-form-region"></a>存取表單區域上的控制項
 若要使用 `Globals` 類別存取表單區域上的控制項，您必須使控制項能存取表單區域程式碼檔案外部的程式碼。

### <a name="form-regions-designed-in-the-form-region-designer"></a>表單區域設計工具中設計的表單區域
 若為 C#，請變更您想要存取之每個控制項的修飾詞。 若要這樣做，請在 [表單區域設計工具] 中選取每個控制項，並且將 [屬性]  視窗中的 **修飾詞** 屬性變更為 **內部** 或 **公用** 。 例如，如果您將 **的** 修飾詞 `textBox1` 屬性變更為 **內部**，您可以輸入 `textBox1` 來存取 `Globals.FormRegions.FormRegion1.textBox1`。

 若為 Visual Basic，您不需要變更修飾詞。

### <a name="imported-form-regions"></a>匯入的表單區域
 當您匯入在 Outlook 中設計的表單區域時，在表單區域之每個控制項的存取修飾詞會變成私用。 因為您無法使用表單區域設計工具來修改匯入的表單區域，所以沒有任何方法可以變更 [屬性]  視窗中控制項的修飾詞。

 若要啟用區域程式碼檔案之外控制項表單的存取，請在表單區域程式碼檔案中建立屬性以傳回該控制項。

 如需有關如何在 c # 中建立屬性的詳細資訊，請參閱 [如何：宣告和使用讀寫屬性 &#40;C&#35; 程式設計指南&#41;](/dotnet/csharp/programming-guide/classes-and-structs/how-to-declare-and-use-read-write-properties)。

 如需有關如何在 Visual Basic 中建立屬性的詳細資訊，請參閱 [如何：建立屬性 (Visual Basic) ](/dotnet/visual-basic/programming-guide/language-features/procedures/how-to-create-a-property)。

## <a name="see-also"></a>另請參閱
- [建立 Outlook 表單區域的指導方針](../vsto/guidelines-for-creating-outlook-form-regions.md)
- [逐步解說：設計 Outlook 表單區域](../vsto/walkthrough-designing-an-outlook-form-region.md)
- [如何：在 Outlook 增益集專案中加入表單區域](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)
- [Outlook 表單區域中的自訂動作](../vsto/custom-actions-in-outlook-form-regions.md)
- [將表單區域與 Outlook 訊息類別產生關聯](../vsto/associating-a-form-region-with-an-outlook-message-class.md)
- [逐步解說：匯入在 Outlook 中設計的表單區域](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)
- [如何：防止 Outlook 顯示表單區域](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md)
- [建立 Outlook 表單區域](../vsto/creating-outlook-form-regions.md)
- [在執行時間存取功能區](../vsto/accessing-the-ribbon-at-run-time.md)
