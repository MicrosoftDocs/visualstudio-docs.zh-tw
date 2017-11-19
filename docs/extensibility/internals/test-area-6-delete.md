---
title: "測試區域 6： 刪除 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control [Visual Studio SDK], deleting items
- source control plug-ins, deleting items
ms.assetid: 6f2e872c-5ba2-4303-9f50-a90cef9a6225
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2a8949135bb7354ba0279ac1b6c2f0ba99fb1b2a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="test-area-6-delete"></a>測試區域 6： 刪除
這個原始檔控制外掛程式的測試區域涵蓋刪除動作。  
  
 原始檔控制刪除中的動作會回應**方案總管 中**。  
  
 以下是您可以刪除的項目清單：  
  
-   檔案  
  
-   資料夾  
  
-   專案  
  
 根據專案類型中，您可能必須選擇**移除**（分葉磁碟上的檔案） 的專案或**刪除**（移除磁碟上的檔案） 的專案。 任何一項動作會移除專案或項目從**方案總管 中**。  
  
## <a name="expected-behavior"></a>預期的行為  
 刪除測試區域中的測試案例的預期的行為是：  
  
-   已刪除的項目不再顯示內**方案總管 中**。  
  
-   已刪除的專案或項目的父代已簽出，視需要 （可能含提示。）  
  
-   刪除簽出，或新增項目之後，它不會顯示在**暫止簽入**視窗。  
  
-   項目仍會存在於原始檔控制存放區中，內，即使在刪除後，且必須手動清除。  
  
|動作|測試步驟|若要確認預期的結果|  
|------------|----------------|--------------------------------|  
|刪除用戶端專案|1.建立用戶端專案。<br />2.將方案加入原始檔控制。<br />3.從方案移除整個專案|常見的預期的行為。|  
|刪除空白檔案|1.建立用戶端專案。<br />2.將零位元組檔案加入專案。<br />3.將方案加入原始檔控制。<br />4.選取檔案，將它刪除。|常見的預期的行為。|  
|刪除資料夾，其中包含一個檔案|1.建立單一專案的方案。<br />2.新增的資料夾。<br />3.新增一個檔案的資料夾。<br />4.將方案加入原始檔控制。<br />5.簽出以避免提示專案。<br />6.刪除資料夾。|常見的預期的行為。|  
|刪除檔案系統的 Web 專案|1.建立檔案系統的 Web 專案 （使用瀏覽按鈕，以指定的 UNC 路徑）。<br />2.將方案加入原始檔控制。<br />3.從方案中移除整個專案。<br />4.本機 Web 專案重複步驟 1 到 3 （執行整個程式碼的不同路徑但具有相同的外部介面和行為）。|常見的預期的行為。|  
|從檔案系統網站專案刪除檔案|1.建立檔案系統的 Web 專案。<br />2.將方案加入原始檔控制。<br />3.從專案刪除檔案。<br />4.本機 Web 專案重複步驟 1 到 3 （執行整個程式碼的不同路徑但具有相同的外部介面和行為）。|常見的預期的行為。|  
  
## <a name="see-also"></a>另請參閱  
 [原始檔控制外掛程式測試指南](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)