---
title: HOW TO：顯示增益集使用者介面錯誤
ms.date: 02/02/2017
ms.topic: conceptual
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 34727c0949ab4ad6baf8e91b27b20115cf074b92
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60096357"
---
# <a name="how-to-show-add-in-user-interface-errors"></a>HOW TO：顯示增益集使用者介面錯誤
  根據預設，如果 VSTO 增益集嘗試處理的 Microsoft Office 使用者介面 (UI) 和失敗，就會不顯示任何錯誤訊息。 不過，您可以設定 Microsoft Office 應用程式，顯示與 UI 相關的錯誤訊息。 您可以使用這些訊息，以協助判斷為何自訂功能區未出現，或為何出現了功能區，但沒有出現任何控制項。

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

## <a name="to-show-vsto-add-in-user-interface-errors"></a>顯示 VSTO 增益集使用者介面錯誤

1. 啟動應用程式。

2. 按一下 [檔案]  索引標籤。

3. 按一下 [選項] 。

4. 在分類窗格中，按一下 [進階] 。

5. 在詳細資料窗格中，選取 [顯示 VSTO 增益集使用者介面錯誤] ，然後按一下 [確定] 。

    > [!NOTE]
    >  對於 Outlook，[顯示 VSTO 增益集使用者介面錯誤]  核取方塊位於詳細資料窗格的 [開發人員]  區段。 對於其他應用程式，此核取方塊位於詳細資料窗格的 [一般]  區段。

## <a name="see-also"></a>另請參閱
- [Office UI 自訂](../vsto/office-ui-customization.md)
- [建立 Outlook 表單區域](../vsto/creating-outlook-form-regions.md)
- [功能區概觀](../vsto/ribbon-overview.md)
- [執行窗格概觀](../vsto/actions-pane-overview.md)
