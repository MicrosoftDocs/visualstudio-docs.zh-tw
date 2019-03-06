---
title: 測試區域 6︰刪除 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], deleting items
- source control plug-ins, deleting items
ms.assetid: 6f2e872c-5ba2-4303-9f50-a90cef9a6225
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7f62b580b72f7910f8d5a688acc8df61361286c0
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "56627918"
---
# <a name="test-area-6-delete"></a>測試區域 6︰刪除
此原始檔控制外掛程式的測試區域涵蓋刪除動作。

 回應刪除動作，在原始檔控制**方案總管 中**。

 以下是一份可刪除的項目：

- 檔案

- 資料夾

- 專案

  根據專案類型中，您可能必須選擇**移除**專案 （分葉磁碟上的檔案） 或**刪除**（移除磁碟上的檔案） 的專案。 任何一項動作會移除專案或項目從**方案總管 中**。

## <a name="expected-behavior"></a>預期的行為
 刪除測試區域中的測試案例的預期的行為是：

-   已刪除的項目已不再顯示內**方案總管 中**。

-   已刪除的專案或項目的父代已簽出，視需要 （可能是使用提示。）

-   在出刪除已選取，或新增項目之後，它不會顯示在**暫止簽入**視窗。

-   項目仍存在於原始檔控制存放區中，內，即使已經刪除，並必須以手動方式清除。

|動作|測試步驟|若要確認預期的結果|
|------------|----------------|--------------------------------|
|刪除用戶端專案|1.建立用戶端專案。<br />2.您可以將方案加入原始檔控制。<br />3.從方案移除整個專案|常見的預期的行為。|
|刪除空白檔案|1.建立用戶端專案。<br />2.您可以將零位元組檔案加入專案。<br />3.您可以將方案加入原始檔控制。<br />4.選取的檔案，請刪除它。|常見的預期的行為。|
|刪除資料夾，其中包含一個檔案|1.建立單一專案的方案。<br />2.新增的資料夾。<br />3.新增一個檔案的資料夾。<br />4.您可以將方案加入原始檔控制。<br />5.簽出專案，以避免出現提示。<br />6.刪除資料夾。|常見的預期的行為。|
|刪除檔案系統的 Web 專案|1.建立檔案系統的 Web 專案 （使用瀏覽按鈕，以指定的 UNC 路徑）。<br />2.您可以將方案加入原始檔控制。<br />3.從方案中移除整個專案。<br />4.針對本機 Web 專案重複步驟 1 到 3 （運用不同的路徑執行程式碼，但具有相同的外部介面和行為）。|常見的預期的行為。|
|從檔案系統的 Web 專案刪除檔案|1.建立檔案系統 Web 專案。<br />2.您可以將方案加入原始檔控制。<br />3.從專案刪除檔案。<br />4.針對本機 Web 專案重複步驟 1 到 3 （運用不同的路徑執行程式碼，但具有相同的外部介面和行為）。|常見的預期的行為。|

## <a name="see-also"></a>另請參閱
- [原始檔控制外掛程式測試指南](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)