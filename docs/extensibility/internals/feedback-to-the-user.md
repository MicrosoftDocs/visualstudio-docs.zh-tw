---
title: 向使用者的反饋 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- user model feedback
- environment, context
- IDE, context
- IDE, user feedback
ms.assetid: 2d472a24-3813-4f5f-9783-b491ad8a71ad
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 46b9190b16b9aa444384847bf209ccca50c7f768
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708406"
---
# <a name="feedback-to-the-user"></a>向使用者的回饋
在[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]整合式開發環境 (IDE) 中,有關可用功能的可視回饋基於使用者當前選擇和全域選擇上下文。 下表列出了在不同的選擇上下文中可用的功能。

|選擇內容|可用功能|
|-----------------------|-----------------------------|
|IDE|全域|
|目前產品集|特定於產品|
|活動層次結構|特定於層次結構類型的層次結構類型|
|活動層次結構項目|層次結構項目類型的特定|
|活動文件|特定於文件類型的文件型態|
|最頂層多文件介面 (MDI) 視窗|特定於視窗型態|
|目前選擇內容|選擇內容的文字|

 如果只顯示使用者所需的功能,並不斷提供一致的選擇和環境上下文反饋,則可以降低 IDE 中的複雜性。 每當 IDE 中開啟視窗時,以下規則將適用:

- 如果視窗更改其選擇上下文,則選擇反饋在視窗中明確指示,**如果顯示動態幫助**視窗,則更新以反映當前上下文。

- 如果視窗更改全域選擇上下文,則所有特定於上下文的功能表、活動層次結構視窗和應用程式標題列將更新以反映當前上下文。

- 視窗應在 **「屬性」** 視窗中顯示目前選擇的屬性,如果顯示,則選擇「**屬性頁」** 對話框。

- 如果視窗不顯示屬性或更改全域選擇上下文,則當視窗不再是 IDE 中的活動視窗時,選擇反饋不應保留在視窗中。

- 所有特定於文檔的工具視窗都應持續反映活動文檔。

- 功能表、工具列和應用程式標題列應反映最頂層的多文檔介面 (MDI) 用戶端視窗。

  例如,當開啟視覺化基本 Web 應用程式項目中**Web 窗體**的 HTML 檢視`<td>`並使用者選擇標記 時,會以下列方式提供回饋:

- 所選內容在活動視窗中指示,並反映在 **「屬性」** 視窗中。

- 特定於文件**的工具箱**將更新以反映活動文檔。

- 將顯示**編輯器**工具列和 **「表」** 選單,標題列將更新以反映 Web 窗體視窗。

- 活動層次結構視窗(通常是**解決方案資源管理員**)及其標題列更新以反映當前上下文和上下文相關的**專案**功能表命令,現在應用於活動 Web 應用程式專案。

## <a name="see-also"></a>另請參閱
- [IDE 選擇與貨幣](../../extensibility/internals/selection-and-currency-in-the-ide.md)
- [選擇內容物件](../../extensibility/internals/selection-context-objects.md)
- [層次結構與選擇](../../extensibility/internals/hierarchies-and-selection.md)
