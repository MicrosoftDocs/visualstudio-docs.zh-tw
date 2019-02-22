---
title: 適用於 Outlook 自訂功能區
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Inspectors [Office development in Visual Studio]
- Outlook [Office development in Visual Studio], Ribbon
- customizing the Ribbon, about customizing the Ribbon
- custom Ribbon, about customizing the Ribbon
- Ribbon [Office development in Visual Studio], Outlook
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 58735a36afd48132f919e370da5e27fd0c42a0f0
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "56614957"
---
# <a name="customize-a-ribbon-for-outlook"></a>適用於 Outlook 自訂功能區
  當您在 Microsoft Office Outlook 自訂功能區時，您必須考慮自訂功能區在應用程式中出現的位置。 Outlook 會將功能區顯示在主應用程式使用者介面 (UI) 中，以及在使用者執行建立電子郵件訊息等特定工作時開啟的視窗中。 這些應用程式視窗名為偵測器。

 ![影片連結](../vsto/media/playvideo.gif "影片連結")如需相關的影片示範，請參閱[How do i:您可以使用功能區設計工具自訂 Outlook 功能區？](http://go.microsoft.com/fwlink/?LinkID=130312).

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="add-a-custom-ribbon-to-the-main-application-ui"></a>將自訂功能區新增至主應用程式 UI
 Outlook 中的主應用程式 UI 稱為「總管」。 如果您使用**功能區 （視覺化設計工具）** 項目時，您可以加入功能區 總管 中依序按一下**RibbonType**屬性中的功能區**屬性** 視窗中，然後選取**Microsoft.Outlook.Explorer**。

## <a name="assign-a-ribbon-to-an-inspector"></a>將功能區指派給偵測器
 您可藉由指定與偵測器訊息類別相對應的功能區類型，識別您想要自訂的偵測器。

 如果您使用**功能區 （視覺化設計工具）** 項目，按一下**RibbonType**屬性中的功能區**屬性** 視窗中，並接著選取一或多個功能區 Id 的來源值清單。

 您可以在專案中加入多個功能區。 如果有多個功能區共用功能區 ID，請覆寫在專案 `ThisAddin` 類別中的 `CreateRibbonExtensibilityObject` 方法，以指定要在執行階段顯示哪個功能區。 如需詳細資訊，請參閱 <<c0> [ 功能區概觀](../vsto/ribbon-overview.md)。 如需有關每個功能區類型的詳細資訊，請參閱技術文件[來自訂功能區的 Outlook 2007](/previous-versions/office/developer/office-2007/bb226712(v=office.12))。

## <a name="specify-the-ribbon-type-by-using-ribbon-xml"></a>使用功能區 XML 來指定功能區類型
 如果您使用**功能區 (XML)** 項目，請檢查值*ribbonID*中的參數<xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A>方法，並傳回適當的功能區。

 <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A> 方法會在功能區程式碼檔中由 Visual Studio 自動產生。 *RibbonID*參數是識別總管或偵測器的特定類型的字串。 如需可能值的完整清單*ribbonID*參數，請參閱技術文件[自訂 Outlook 2007 功能區](/previous-versions/office/developer/office-2007/bb226712(v=office.12))。

 下列程式碼範例示範如何只在 `Microsoft.Outlook.Mail.Compose` 偵測器中顯示自訂功能區。 這是在使用者建立新的電子郵件訊息時開啟的偵測器。 若要顯示在功能區中指定`GetResourceText()`方法，就會發出**功能區**類別。 如需詳細資訊**功能區**類別，請參閱[功能區 XML](../vsto/ribbon-xml.md)。

 [!code-csharp[Trin_RibbonOutlookBasic#1](../vsto/codesnippet/CSharp/Trin_RibbonOutlookBasic/Ribbon1.cs#1)]
 [!code-vb[Trin_RibbonOutlookBasic#1](../vsto/codesnippet/VisualBasic/Trin_RibbonOutlookBasic/Ribbon1.vb#1)]

## <a name="see-also"></a>另請參閱
- [在執行階段功能區的存取](../vsto/accessing-the-ribbon-at-run-time.md)
- [功能區概觀](../vsto/ribbon-overview.md)
- [功能區設計工具](../vsto/ribbon-designer.md)
- [Ribbon XML](../vsto/ribbon-xml.md)
