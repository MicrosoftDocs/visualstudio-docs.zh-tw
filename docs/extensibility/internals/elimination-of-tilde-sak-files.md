---
title: 移除 【SAK 檔案】微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- temporary files
- ~sak files
- source control plug-ins, ~SAK files
ms.assetid: 5277b5fa-073b-4bd1-8ba1-9dc913aa3c50
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0294198bb1560f8df6f17170013f88d4fe11e5cf
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708506"
---
# <a name="elimination-of-sak-files"></a>移除 _SAK檔案
在原始程式碼管理外掛程式 API 1.2 中 *,\SAK*檔案已被功能標誌和新功能所取代,這些功能檢測原始程式碼管理外掛程式是否支援*MSSCCPRJ*檔和共享簽出。

## <a name="sak-files"></a>*SAK 檔案
Visual Studio .NET 2003 建立了暫存檔,預置了 *@SAK*。 這些檔案用於確定原始程式碼管理外掛程式是否支援:

- *MSSCCPRJ.SCC*檔。

- 多個(共用)簽出。

對於支援原始程式碼管理外掛程式 API 1.2 中提供的進階功能的外掛程式,IDE 無需使用以下各節中詳述的新功能、標誌和函數來檢測這些功能,而無需創建臨時檔。

## <a name="new-capability-flags"></a>新功能旗標
 `SCC_CAP_SCCFILE`

 `SCC_CAP_MULTICHECKOUT`

## <a name="new-functions"></a>新的函式
- [SccWillCreateSccFile](../../extensibility/sccwillcreatesccfile-function.md)

- [SccIsMultiCheckoutEnabled](../../extensibility/sccismulticheckoutenabled-function.md)

 如果原始程式碼管理外掛程式支援多個(共用)簽出,則它`SCC_CAP_MULTICHECKOUT`聲明該功能並`SccIsMultiCheckOutEnabled`實現該功能。 每當對任何源控制的專案執行簽出操作時,都會調用此功能。

 如果原始程式管理外掛程式支援建立與*MSSCCPRJ.SCC*檔,則`SCC_CAP_SCCFILE`它聲明 這個功能並實現[SccWillCreateSccFile](../../extensibility/sccwillcreatesccfile-function.md)。 使用檔案清單呼叫此功能。 該函數將`TRUE' or 'FALSE`為每個檔返回,以指示 Visual Studio 是否應為其使用*MSSCCPRJ.SCC*檔。 如果原始碼管理外掛程式選擇不支援這些新功能和功能,它可以使用以下註冊表項來關閉這些檔案的建立:

 **[HKEY_CURRENT_USER_軟體\微軟[VisualStudio]8.0\源控制]不建立暫存檔在原始碼管理** = *dword:0000001*

> [!NOTE]
> 如果此註冊表項設置為*dword:00000000,* 則等效於不存在的密鑰,Visual Studio 仍嘗試創建臨時檔。 但是,如果註冊表項設置為*dword:00000001,Visual*Studio 不會嘗試創建臨時檔。 相反,它假定原始程式碼管理外掛程式不支援*MSSCCPRJ.SCC*檔,並且不支援共用簽出。

## <a name="see-also"></a>另請參閱
- [原始程式碼管理外掛程式 API 版本 1.2 中的新增功能](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
