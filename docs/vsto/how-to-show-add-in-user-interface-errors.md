---
title: 如何：顯示增益集使用者介面錯誤
description: 瞭解如何使用 Visual Studio 以程式設計方式顯示 Microsoft Office 應用程式中的 VTSO 增益集使用者介面錯誤。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- add-ins [Office development in Visual Studio], user interface errors
- errors [Office development in Visual Studio], user interface errors
- user interfaces [Office development in Visual Studio], errors
- application-level add-ins [Office development in Visual Studio], user interface errors
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 29e07e49d901b44b534d9d274e5535be663e97ef
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99927674"
---
# <a name="how-to-show-add-in-user-interface-errors"></a>如何：顯示增益集使用者介面錯誤
  根據預設，如果 VSTO 增益集嘗試操作 Microsoft Office 使用者介面 (UI) 且失敗，則不會顯示任何錯誤訊息。 不過，您可以設定 Microsoft Office 應用程式，顯示與 UI 相關的錯誤訊息。 您可以使用這些訊息來協助判斷自訂功能區未出現的原因，或為什麼會出現功能區但不會顯示任何控制項。

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

## <a name="to-show-vsto-add-in-user-interface-errors"></a>顯示 VSTO 增益集使用者介面錯誤

1. 啟動應用程式。

2. 按一下 [檔案]  索引標籤。

3. 按一下 [選項]。

4. 在分類窗格中，按一下 [進階] 。

5. 在詳細資料窗格中，選取 [顯示 VSTO 增益集使用者介面錯誤] ，然後按一下 [確定] 。

    > [!NOTE]
    > 對於 Outlook，[顯示 VSTO 增益集使用者介面錯誤]  核取方塊位於詳細資料窗格的 [開發人員]  區段。 對於其他應用程式，此核取方塊位於詳細資料窗格的 [一般]  區段。

## <a name="see-also"></a>另請參閱
- [Office UI 自訂](../vsto/office-ui-customization.md)
- [建立 Outlook 表單區域](../vsto/creating-outlook-form-regions.md)
- [功能區總覽](../vsto/ribbon-overview.md)
- [動作窗格總覽](../vsto/actions-pane-overview.md)
