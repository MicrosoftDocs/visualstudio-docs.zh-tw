---
title: 測試區域6：刪除 |Microsoft Docs
description: 此原始檔控制測試區域涵蓋方案總管中 Visual Studio 原始檔控制外掛程式的刪除動作。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], deleting items
- source control plug-ins, deleting items
ms.assetid: 6f2e872c-5ba2-4303-9f50-a90cef9a6225
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e405df704dfbba14413bd3787a9fb9f959c62a46
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105078587"
---
# <a name="test-area-6-delete"></a>測試區域 6：刪除
此原始檔控制外掛程式測試區域涵蓋刪除動作。

 原始檔控制會回應 **方案總管** 中的刪除動作。

 以下是可刪除的專案清單：

- 檔案

- 資料夾

- Project

  視專案類型而定，您可以選擇 **移除** 專案， (將檔案保留在磁片上) 或 **刪除** 專案 (移除磁片) 上的檔案。 任一個動作會從 **方案總管** 移除專案或專案。

## <a name="expected-behavior"></a>預期行為
 刪除測試區域中測試案例的預期行為如下：

- **方案總管** 中不再顯示已刪除的專案。

- 視需要簽出已刪除專案或專案的父系 (可能出現提示。 ) 

- 當您刪除已簽出或加入的專案之後，該專案就不會出現在 [ **暫止簽入** ] 視窗中。

- 即使在刪除後，專案仍然存在於原始檔控制存放區中，而且必須手動清除。

|動作|測試步驟|要驗證的預期結果|
|------------|----------------|--------------------------------|
|刪除用戶端專案|1. 建立用戶端專案。<br />2. 將方案加入至原始檔控制。<br />3. 從方案中移除整個專案|常見的預期行為。|
|刪除空白檔案|1. 建立用戶端專案。<br />2. 將零位元組檔案新增至專案。<br />3. 將方案加入至原始檔控制。<br />4. 選取檔案，將它刪除。|常見的預期行為。|
|刪除具有一個檔案的資料夾|1. 建立單一專案方案。<br />2. 新增資料夾。<br />3. 將一個檔案新增至資料夾。<br />4. 將方案加入至原始檔控制。<br />5. 查看專案以避免出現提示。<br />6. 刪除資料夾。|常見的預期行為。|
|刪除檔案系統 Web 專案|1. 建立檔案系統 Web 專案 (使用 [流覽] 按鈕來指定 UNC 路徑) 。<br />2. 將方案加入至原始檔控制。<br />3. 從方案中移除整個專案。<br />4. 針對本機 Web 專案重複步驟1到3， (透過程式碼執行不同的路徑，但) 的外部介面和行為相同。|常見的預期行為。|
|刪除檔案系統 Web 專案中的檔案|1. 建立檔案系統 Web 專案。<br />2. 將方案加入至原始檔控制。<br />3. 從專案中刪除檔案。<br />4. 針對本機 Web 專案重複步驟1到3， (透過程式碼執行不同的路徑，但) 的外部介面和行為相同。|常見的預期行為。|

## <a name="see-also"></a>另請參閱
- [原始檔控制外掛程式測試指南](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
