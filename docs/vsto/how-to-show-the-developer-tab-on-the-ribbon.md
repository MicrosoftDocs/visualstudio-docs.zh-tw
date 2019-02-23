---
title: HOW TO：在功能區顯示開發人員索引標籤
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Ribbon [Office development in Visual Studio], tabs
- Developer tab [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 64a0fb4dbc91ff09bddf037a8ce140f134e41e43
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "56614658"
---
# <a name="how-to-show-the-developer-tab-on-the-ribbon"></a>HOW TO：在功能區顯示開發人員索引標籤
  若要存取**開發人員** 索引標籤上的 Office 應用程式功能區中，您必須將它設定為顯示該索引標籤上，因為它不會出現預設。 例如，如果您要將 <xref:Microsoft.Office.Tools.Word.GroupContentControl> 加入至 Word 文件層級自訂中，您必須顯示此索引標籤。

> [!NOTE]
>  本指導僅適用於 Office 2010 或更新版應用程式。 如果您想要在 2007 Microsoft Office System 顯示這個索引標籤，請參閱本主題的下列版本[How to:在功能區顯示開發人員索引標籤](https://web.archive.org/web/20140303033431/msdn.microsoft.com/library/bb608625(v=vs.90).aspx
)。

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

> [!NOTE]
>  沒有存取權**開發人員** 索引標籤。

## <a name="to-show-the-developer-tab"></a>顯示開發人員索引標籤

1.  啟動本主題支援的任何 Office 應用程式。 請參閱**適用於：** 稍早在本主題中的附註。

2.  在 [**檔案**索引標籤上，選擇**選項**] 按鈕。

     下圖顯示**檔案**索引標籤並**選項**Office 2010 中的按鈕。

     ![選擇 [檔案]，Outlook 2010 中的選項](../vsto/media/vsto-office-file-tab.png "Outlook 2010 中選擇 [檔案]，選項")

     下圖顯示**檔案**Office 2013 中的索引標籤。

     ![Outlook 2013 中的 [檔案] 索引標籤](../vsto/media/vsto-office2013-filetab.png "Outlook 2013 中的 [檔案] 索引標籤")

     下圖顯示**選項**Office 2013 中的按鈕。

     ![Outlook 2013 Preview 中的 [選項] 按鈕](../vsto/media/vsto-office2013-optionsbutton.png "Outlook 2013 Preview 中的 [選項] 按鈕")

3.  在  _ApplicationName_**選項**對話方塊方塊中，選擇 **自訂功能區** 按鈕。

     下圖顯示**選項** 對話方塊中，**自訂功能區**Excel 2010 中的按鈕。 在本主題頂端附近的「適用於」一節中所列的所有其他應用程式中，此按鈕的位置類似。

     ![自訂功能區按鈕](../vsto/media/vsto-office2010-customizeribbonbutton.png "自訂功能區按鈕")

4.  在主要索引標籤的清單中，選取**開發人員**核取方塊。

     下圖顯示**開發人員**Word 2010 中的核取方塊和[!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)]。 在本主題頂端附近的「適用於」一節中所列的所有其他應用程式中，此核取方塊的位置類似。

     ![在 [Word 選項] 對話方塊的 [開發人員] 核取方塊](../vsto/media/vsto-office2010-developercheckbox.png "The Developer 核取方塊，在 [Word 選項] 對話方塊")

5.  選擇**確定**按鈕以關閉**選項** 對話方塊。

## <a name="see-also"></a>另請參閱
- [Office UI 自訂](../vsto/office-ui-customization.md)
