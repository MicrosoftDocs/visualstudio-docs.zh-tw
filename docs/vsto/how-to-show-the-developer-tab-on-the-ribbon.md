---
title: 如何：在功能區顯示開發人員索引標籤
description: 瞭解如何使用 Visual Studio，以程式設計方式在 Microsoft Word 檔的功能區上顯示 [開發人員] 索引標籤。
ms.custom: SEO-VS-2020
ms.date: 08/14/2019
ms.topic: how-to
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
ms.openlocfilehash: 4dc38b941d27cab0653b923ddd03ba8b78eeab58
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2020
ms.locfileid: "97528150"
---
# <a name="how-to-show-the-developer-tab-on-the-ribbon"></a>如何：在功能區顯示開發人員索引標籤
  若要存取 Office 應用程式功能區上的 [ **開發人員** ] 索引標籤，您必須將它設定為顯示該索引標籤，因為預設不會顯示此索引標籤。 例如，如果您要將 <xref:Microsoft.Office.Tools.Word.GroupContentControl> 加入至 Word 文件層級自訂中，您必須顯示此索引標籤。

> [!NOTE]
> 本指導僅適用於 Office 2010 或更新版應用程式。 如果您想要在 2007 Microsoft Office 系統中顯示此索引標籤，請參閱本主題的下列版本 [如何：在功能區上顯示開發人員](https://web.archive.org/web/20140303033431/msdn.microsoft.com/library/bb608625(v=vs.90).aspx
)索引標籤。

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

> [!NOTE]
> 存取權沒有 [ **開發人員** ] 索引標籤。

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="to-show-the-developer-tab"></a>顯示開發人員索引標籤

1. 啟動本主題支援的任何 Office 應用程式。 請參閱本主題稍早的 **適用物件：** 附注。

2. **在 [檔案] 索引** 標籤上，選擇 [**選項**] 按鈕。

     下圖顯示 Office 2010 **中的 [** 檔案] 索引標籤和 [ **選項** ] 按鈕。

     ![在 Outlook 2010 中依序選擇 [檔案] 和 [選項]](../vsto/media/vsto-office-file-tab.png "在 Outlook 2010 中依序選擇 [檔案] 和 [選項]")

     下圖顯示 Office 2013 中 **的 [檔案** ] 索引標籤。

     ![Outlook 2013 中的 [檔案] 索引標籤](../vsto/media/vsto-office2013-filetab.png "Outlook 2013 中的 [檔案] 索引標籤")

     下圖顯示 Office 2013 中的 [ **選項** ] 按鈕。

     ![Outlook 2013 Preview 中的 [選項] 按鈕](../vsto/media/vsto-office2013-optionsbutton.png "Outlook 2013 Preview 中的 [選項] 按鈕")

3. 在 [ _ApplicationName_**選項** ] 對話方塊中，選擇 [ **自訂功能區** ] 按鈕。

     下圖顯示 Excel 2010 中的 [ **選項** ] 對話方塊和 [ **自訂] 功能區** 按鈕。 在本主題頂端附近的「適用於」一節中所列的所有其他應用程式中，此按鈕的位置類似。

     ![自訂功能區按鈕](../vsto/media/vsto-office2010-customizeribbonbutton.png "自訂功能區按鈕")

4. 在主要索引標籤的清單中，選取 [ **開發人員** ] 核取方塊。

     下圖顯示 Word 2010 和中的 [ **開發人員** ] 核取方塊 [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] 。 在本主題頂端附近的「適用於」一節中所列的所有其他應用程式中，此核取方塊的位置類似。

     ![[Word 選項] 對話方塊中的 [開發人員] 核取方塊](../vsto/media/vsto-office2010-developercheckbox.png "[Word 選項] 對話方塊中的 [開發人員] 核取方塊")

5. 選擇 [ **確定** ] 按鈕以關閉 [ **選項** ] 對話方塊。

## <a name="see-also"></a>另請參閱
- [Office UI 自訂](../vsto/office-ui-customization.md)
