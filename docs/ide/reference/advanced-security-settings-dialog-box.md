---
title: '[進階安全性設定] 對話方塊'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.err.debug_in_zone_no_hostproc
helpviewer_keywords:
- Advanced Security Settings dialog box
ms.assetid: 2e7aefe9-6d20-4f3e-b257-aee1ebcc6f5d
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6fec353f6ede2a9d2f99a8dfc19611577bbc6160
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="advanced-security-settings-dialog-box"></a>[進階安全性設定] 對話方塊
此對話方塊可讓您指定在區域中偵錯的相關安全性設定。

 若要存取這個對話方塊，請選取方案總管中的專案節點，然後按一下 [專案] 功能表上的 [屬性]。 [專案設計工具] 出現時，請按一下 [安全性] 索引標籤。在 [安全性] 頁面上，選取 [啟用 ClickOnce 安全性設定]，並按一下 [這是部分信任的應用程式]，然後按一下 [進階]。

## <a name="uielement-list"></a>UIElement 清單
 **以選取的權限集合對此應用程式進行偵錯** 如果您選取此核取方塊，則會在偵錯期間使用 [安全性] 頁面上所選取的權限集合。 根據預設，這個選項是選取的。

 若要讓安全性區域中的偵錯運作，必須啟用此選項；也必須啟用 [啟用 Visual Studio 裝載處理序] 選項 (位於 [專案設計工具] 的 [偵錯] 頁面上)。

 針對 WPF 網站瀏覽器應用程式專案，核取並停用 [以選取的使用權限集合對此應用程式進行偵錯] 選項。

 **允許應用程式存取它的來源網站** 如果您選取此核取方塊，則應用程式可以存取在其上發行它的網站或伺服器共用。 根據預設，這個選項是選取的。

 **將下列 URL 視為此應用程式的下載位置來進行偵錯** 如果您必須讓應用程式存取對應至 [發行] 頁面上所指定之 [安裝 URL] 的網站或伺服器共用，請在這裡鍵入該 URL。 只有在選取 [允許應用程式存取它的來源網站] 時，才能使用此選項。

## <a name="see-also"></a>請參閱

- [專案設計工具、安全性頁面](../../ide/reference/security-page-project-designer.md)