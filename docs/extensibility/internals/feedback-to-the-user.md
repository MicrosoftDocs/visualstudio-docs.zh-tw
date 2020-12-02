---
title: 對使用者的意見反應 |Microsoft Docs
description: 瞭解如何在 Visual Studio 整合式開發環境 (IDE) 中提供視覺回饋給使用者。
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: d8f3f79a61729a641ee7c046ddd196a648469fb3
ms.sourcegitcommit: df6ba39a62eae387e29f89388be9e3ee5ceff69c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2020
ms.locfileid: "96480521"
---
# <a name="feedback-to-the-user"></a>對使用者的意見反應
在 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 整合式開發環境 (IDE) 中，有關可用功能的視覺化意見反應是以使用者目前的選取範圍和全域選取內容為基礎。 下表列出不同的選取內容中可用的功能。

|選取內容|可用的功能|
|-----------------------|-----------------------------|
|IDE|全球|
|目前的產品集|特定產品|
|主動階層|階層類型特定|
|現用階層專案|階層專案類型特定|
|活動文檔|特定檔案類型|
| (MDI) 視窗的最上層多重文件介面|特定視窗類型|
|目前的選取範圍內容|選取內容特定|

 如果您只是要呈現使用者所需的功能，並持續提供一致的選取範圍和環境內容回饋，您就可以降低 IDE 中的複雜度。 當視窗在 IDE 中開啟時，適用下列規則：

- 如果視窗變更其選取內容，則會在視窗中清楚指出選取的意見反應，而且 **動態** 說明視窗（如所示）會更新以反映目前的內容。

- 如果視窗變更全域選取內容，則會更新所有內容特定的功能表、作用中的階層視窗和應用程式標題列，以反映目前的內容。

- 視窗應該會在 [ **屬性** ] 視窗中顯示目前選取範圍的屬性，並選擇性地呈現 [ **屬性頁** ] 對話方塊。

- 如果視窗未顯示 [屬性] 或 [變更全域選取內容]，當它不再是 IDE 中的使用中視窗時，就不應該將選取的意見反應保留在視窗中。

- 所有檔特定工具視窗都應該持續反映使用中的檔。

- 功能表、工具列和應用程式標題列應該會反映 (MDI) 用戶端視窗的最上層多重文件介面。

  例如，當開啟 Visual Basic Web 應用程式專案內的 **Web 表單** HTML 視圖，而且使用者選取 `<td>` 標記時，會以下列方式提供意見反應：

- 選取範圍會顯示在使用中視窗中，並反映在 [ **屬性** ] 視窗中。

- 檔特定的 **工具箱** 會更新，以反映使用中的檔。

- **編輯器** 工具列和 **資料表** 功能表隨即顯示，且標題列會更新以反映 Web 表單視窗。

- 使用中的階層視窗（通常是 **方案總管**）及其標題列更新，以反映目前的內容，而且即時線上的 [ **專案** ] 功能表命令會套用至使用中的 Web 應用程式專案。

## <a name="see-also"></a>另請參閱
- [IDE 中的選取專案和貨幣](../../extensibility/internals/selection-and-currency-in-the-ide.md)
- [選取專案內容物件](../../extensibility/internals/selection-context-objects.md)
- [階層和選取範圍](../../extensibility/internals/hierarchies-and-selection.md)
