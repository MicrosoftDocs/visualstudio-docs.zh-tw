---
title: '測試區域 6: 刪除 |微軟文件'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], deleting items
- source control plug-ins, deleting items
ms.assetid: 6f2e872c-5ba2-4303-9f50-a90cef9a6225
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9902ab9d1cb9c28ddf67b83590a4cccd5f6562f2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704515"
---
# <a name="test-area-6-delete"></a>測試區域 6︰刪除
此原始程式管理外掛程式測試區域涵蓋刪除操作。

 原始程式碼管理回應**解決方案資源管理員**中的刪除操作。

 以下是可移除的項目清單:

- 檔案

- 資料夾

- 隨附此逐步解說的專案

  根據項目類型,您可以選擇**刪除**專案(將檔案留在磁碟上 **)或刪除專案**(刪除磁碟上的檔案)。 操作從**解決方案資源管理員**中刪除專案或項。

## <a name="expected-behavior"></a>預期行為
 刪除測試區域中測試用例的預期行為是:

- 已刪除的專案在**解決方案資源管理員**中不再可見。

- 根據需要簽出已刪除專案或專案的父項(可能帶有提示)。

- 刪除簽出或添加的專案後,它不會顯示在 **「掛起簽入」** 視窗中。

- 即使在刪除之後,該項仍存在於原始程式碼管理儲存中,必須手動清除。

|動作|測試步驟|要驗證的預期結果|
|------------|----------------|--------------------------------|
|移除客戶端項目|1. 創建用戶端專案。<br />2. 將解決方案添加到原始碼管理。<br />3. 從解決方案中移除整個項目|常見預期行為。|
|刪除空檔案|1. 創建用戶端專案。<br />2. 向專案添加零位元組檔。<br />3. 將解決方案添加到原始程式碼管理。<br />4. 選擇檔案,將其刪除。|常見預期行為。|
|移除包含檔案的資料夾|1. 創建單個專案解決方案。<br />2. 添加資料夾。<br />3. 將一個檔案添加到資料夾中。<br />4. 將解決方案添加到原始程式碼管理。<br />5. 查看專案以避免提示。<br />6. 刪除資料夾。|常見預期行為。|
|移除檔案系統 Web 專案|1. 創建檔案系統 Web 專案(使用"瀏覽"按鈕指定 UNC 路徑)。<br />2. 將解決方案添加到原始碼管理。<br />3. 從解決方案中刪除整個專案。<br />4. 對本地 Web 專案重複步驟 1 到 3(通過代碼執行不同的路徑,但具有相同的外部介面和行為)。|常見預期行為。|
|從檔案系統 Web 項目中移除檔案|1. 創建檔案系統 Web 專案。<br />2. 將解決方案添加到原始碼管理。<br />3. 從項目中刪除檔。<br />4. 對本地 Web 專案重複步驟 1 到 3(通過代碼執行不同的路徑,但具有相同的外部介面和行為)。|常見預期行為。|

## <a name="see-also"></a>另請參閱
- [原始檔控制外掛程式測試指南](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
