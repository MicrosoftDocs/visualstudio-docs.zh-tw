---
title: '[進階安全性設定] 對話方塊'
description: '[Advanced Security Settings] 對話方塊可讓您指定與 [區域] 中的調試相關的安全性設定。'
ms.custom: SEO-VS-2020
ms.date: 06/27/2018
ms.technology: vs-ide-deployment
ms.topic: reference
f1_keywords:
- vs.err.debug_in_zone_no_hostproc
helpviewer_keywords:
- Advanced Security Settings dialog box
ms.assetid: 2e7aefe9-6d20-4f3e-b257-aee1ebcc6f5d
author: Mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ffbf2bb5a8a73ba577489af825969c3bdc23f15e
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2020
ms.locfileid: "94351501"
---
# <a name="advanced-security-settings-dialog-box"></a>[進階安全性設定] 對話方塊

此對話方塊可讓您指定在區域中偵錯的相關安全性設定。

![Visual Studio 中的進階安全性設定對話方塊](../media/advanced-security-settings.png)

若要存取這個對話方塊，請選取方案總管中的專案節點，然後按一下 [專案] 功能表上的 [屬性]。 當 [ **專案設計** 工具] 出現時，按一下 [ **安全性** ] 索引標籤。在 [ **安全性** ] 頁面上，選取 [ **啟用 ClickOnce 安全性設定** ]，再按一下 [ **這是部分信任的應用程式** ]，然後按一下 [ **Advanced** ]。

## <a name="uielement-list"></a>UIElement 清單

**允許應用程式存取它的來源網站**

如果您選取此核取方塊，則應用程式可以存取在其上發行它的網站或伺服器共用。 預設會選取這個選項。

**將下列 URL 視為此應用程式的下載位置來進行偵錯**

如果您必須讓應用程式存取對應至 [發行] 頁面上所指定之 **安裝 URL** 的網站或伺服器共用，請在這裡輸入該 URL。 只有在選取 [允許應用程式存取它的來源網站] 時，才能使用此選項。

## <a name="see-also"></a>請參閱

- [專案設計工具、安全性頁](../../ide/reference/security-page-project-designer.md)
