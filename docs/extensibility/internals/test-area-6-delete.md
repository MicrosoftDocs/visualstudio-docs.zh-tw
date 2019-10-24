---
title: 測試區域6：刪除 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], deleting items
- source control plug-ins, deleting items
ms.assetid: 6f2e872c-5ba2-4303-9f50-a90cef9a6225
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1d75721a09615026cd10a42e4b6d8d8520b41239
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72722449"
---
# <a name="test-area-6-delete"></a>測試區域 6︰刪除
這個原始檔控制外掛程式測試區域涵蓋了刪除動作。

 原始檔控制會回應**方案總管**中的刪除動作。

 以下是可以刪除的專案清單：

- 檔案

- 資料夾

- 專案

  視專案類型而定，您可能可以選擇**移除**專案（將檔案留在磁片上）或**刪除**專案（移除磁片上的檔案）。 任一動作都會將專案或專案從**方案總管**中移除。

## <a name="expected-behavior"></a>預期的行為
 刪除測試區域中測試案例的預期行為如下：

- 已刪除的專案不會再顯示在**方案總管**中。

- 已刪除專案或專案的父系會視需要簽出（可能會出現提示）。

- 當您刪除已簽出或加入的專案之後，它不會出現在 [**暫止簽入**] 視窗中。

- 即使在刪除之後，此專案仍存在於原始檔控制存放區中，而且必須手動清除。

|動作|測試步驟|要驗證的預期結果|
|------------|----------------|--------------------------------|
|刪除用戶端專案|1. 建立用戶端專案。<br />2. 將方案加入至原始檔控制。<br />3. 從方案中移除整個專案|一般的預期行為。|
|刪除空白檔案|1. 建立用戶端專案。<br />2. 將零位元組的檔案新增至專案。<br />3. 將方案加入至原始檔控制。<br />4. 選取檔案，將它刪除。|一般的預期行為。|
|刪除具有一個檔案的資料夾|1. 建立單一專案方案。<br />2. 新增資料夾。<br />3. 將一個檔案加入資料夾。<br />4. 將方案加入至原始檔控制。<br />5. 簽出項目以避免出現提示。<br />6. 刪除資料夾。|一般的預期行為。|
|刪除檔案系統 Web 專案|1. 建立檔案系統 Web 專案（使用 [流覽] 按鈕來指定 UNC 路徑）。<br />2. 將方案加入至原始檔控制。<br />3. 從方案中移除整個專案。<br />4. 針對本機 Web 專案重複步驟1到3（透過程式碼執行不同的路徑，但具有相同的外部介面和行為）。|一般的預期行為。|
|從檔案系統 Web 專案中刪除檔案|1. 建立檔案系統 Web 專案。<br />2. 將方案加入至原始檔控制。<br />3. 從專案中刪除檔案。<br />4. 針對本機 Web 專案重複步驟1到3（透過程式碼執行不同的路徑，但具有相同的外部介面和行為）。|一般的預期行為。|

## <a name="see-also"></a>請參閱
- [原始檔控制外掛程式測試指南](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)