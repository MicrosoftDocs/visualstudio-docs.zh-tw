---
title: 進階安全性設定對話方塊 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.err.debug_in_zone_no_hostproc
- vs.err.debug_in_zone_no_hostproc:11310
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Advanced Security Settings dialog box
ms.assetid: 2e7aefe9-6d20-4f3e-b257-aee1ebcc6f5d
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 000c3c4e2996869e96fd0d6097b5bab8576936a7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72651744"
---
# <a name="advanced-security-settings-dialog-box"></a>[進階安全性設定] 對話方塊
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

此對話方塊可讓您指定在區域中偵錯的相關安全性設定。

 若要存取這個對話方塊，請選取方案總管**** 中的專案節點，然後按一下 [專案]**** 功能表上的 [屬性]****。 當 [ **專案設計** 工具] 出現時，按一下 [ **安全性** ] 索引標籤。在 [ **安全性** ] 頁面上，選取 [ **啟用 ClickOnce 安全性設定**]，再按一下 [ **這是部分信任的應用程式**]，然後按一下 [ **Advanced**]。

## <a name="uielement-list"></a>UIElement 清單
 **以選取的權限集合對此應用程式進行偵錯** 如果您選取此核取方塊，則會在偵錯期間使用 [安全性]**** 頁面上所選取的權限集合。 預設會選取這個選項。

 若要讓安全性區域中的偵錯運作，必須啟用此選項；也必須啟用 [啟用 Visual Studio 裝載處理序]**** 選項 (位於 [專案設計工具]**** 的 [偵錯]**** 頁面上)。

 針對 WPF 網站瀏覽器應用程式專案，核取並停用 [以選取的使用權限集合對此應用程式進行偵錯]**** 選項。

 **允許應用程式存取它的來源網站** 如果您選取此核取方塊，則應用程式可以存取在其上發行它的網站或伺服器共用。 預設會選取這個選項。

 **將下列 URL 視為此應用程式的下載位置來進行偵錯** 如果您必須讓應用程式存取對應至 [發行]**** 頁面上所指定之 [安裝 URL]**** 的網站或伺服器共用，請在這裡鍵入該 URL。 只有在選取 [允許應用程式存取它的來源網站]**** 時，才能使用此選項。

## <a name="see-also"></a>另請參閱
 [專案設計工具、安全性頁](../../ide/reference/security-page-project-designer.md)
